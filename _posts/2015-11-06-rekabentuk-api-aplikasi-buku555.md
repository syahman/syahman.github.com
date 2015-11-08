---
layout: post
title: "Rekabentuk RESTfull API Aplikasi Buku555"
description: ""
category: 
tags: []
---
{% include JB/setup %}



**Rekabentuk API (Application Programming Interface) Untuk Aplikasi Buku555**


**1.0	Pendahuluan**


Saya pernah menggunakan PHP SLIM untuk mengaturcara API untuk aplikasi mudah alih. Kali ini,ingin
belajar ilmu baru, teknologi anak muda zaman sekarang (feeling too old!!). Mengapa memilih oracle 
sebagai backend ?  Kerja seharian saya adalah berkaitan oracle. Selain itu, ORACLE telah menyumbang
kepada pembangunan driver nodejs yang membuatkan saya tertarik. Saya juga berkeyakinan JAVASCRIPT adalah
scripting language yang menjadi pilihan kepada pembangunan frontend pada hari ini,terutama SPA apps.
Jadi, mengapa tidak bangunkan juga backend dalam JAVASCRIPT ? tepuk dada tanya otak, boleh ke nak code ni .. 

Oracle juga telah menyediakan platform REST sendiri yang diberi nama **Oracle REST Data Services**. Rujukan
mudah untuk menyediakan REST service menggunakan ORDS -> [https://jsao.io/2015/07/relational-to-json-with-ords/](https://jsao.io/2015/07/relational-to-json-with-ords/). Saya belum sempat menguji fungsi ORDS. 

Arkitektur REST amat berguna untuk membangunkan aplikasi client/server berasaskan rangkaian.
Maksud REST adalah Representational State Transfer. 

    REST was initially proposed by Roy Thomas Fielding in his 2000 PhD dissertation "Architectural Styles and the Design of Network-based Software Architectures".
    Fielding developed the REST architectural style in parallel with HTTP 1.1 of 1996-1999, based on the existing design of HTTP 1.0 of 1996.

Implementasi REST lebih mudah berbanding kaedah lain seperti SOAP,CORBA,WSDL dll..
Ia hanya menggunakan protokol HTTP.

------------------------------------------------

**2.0   Kaedah HTTP**

Untuk merekabentuk API yang berguna, API yang dibina hendaklah menyokong kaedah HTTP seperti
GET,POST,PUT dan DELETE. Ada lagi kaedah HTTP lain seperti OPTIONS,PATCH,HEAD tetapi jarang
digunakan. Setiap kaedah bergantung kepada keperluan aplikasi, sudah tentu setiap aplikasi
perlu ada CRUD (Create,Read,Update dan Delete). 

Cuba anda hubung kait kaedah di bawah ini dengan CRUD :  

{: .table .table-striped}
| Kaedah | Keterangan                  |
|--------|-----------------------------|
| GET    | To fetch a resource         |
| POST   | To create a new resource    |
| PUT    | To update existing resource |
| DELETE | To delete a resource        |

------------------------------------------------

**3.0	HTTP Status Code**

Setiap **request** akan ada **respons**. Jadual di bawah adalah contoh kod status HTTP. Anda akan lebih memahami
kod ini apabila membangunkan sendiri API. 

{: .table .table-striped}
| Kod | Status                |
|-----|-----------------------|
| 200 | OK                    |
| 201 | Created               |
| 304 | Not Modified          |
| 400 | Bad Request           |
| 401 | Unauthorized          |
| 403 | Forbidden             |
| 404 | Not Found             |
| 422 | Unprocessable Entity  |
| 500 | Internal Server Error |

------------------------------------------------

**4.0	Endpoint (Routing) URL**

Endpoint URL dalam rekabentuk API hendaklah mudah difahami dan berfungsi dengan baik, mempunyai mesej respon
yang mempunyai makna dan mudah dibaca **(parse)** oleh klien REST.

Setiap URL bagi setiap fungsi aplikasi hendaklah dikenalpasti. Penggunaan **API key** diperlukan
untuk akses data sensitif dan disaran menggunakan **secure HTTP (https)** untuk mengelakkan pencerobohan data oleh
orang tengah (man-in-the-middle attack). Rujuk lebih lanjut OWASP bab API, web services. API key 
diletakkan dalam header HTTP, bukan diletakkan sekali dalam URL. contoh endpoint URL : 

    Dengan Token : 
    
    GET http://buku555.abc/users/:1
    guna method GET untuk dapatkan rekod users yang mempunyai userid=1 (contoh)
    
    Tanpa Token : 
    
    POST http://buku555.abc/register/
    guna method POST untuk masukkan daftar 
    

Rujukan OWASP :
 
1. [https://www.owasp.org/index.php/Web_Service_Security_Cheat_Sheet](https://www.owasp.org/index.php/Web_Service_Security_Cheat_Sheet)
2. [https://www.owasp.org/index.php/Web_Service_Security_Testing_Cheat_Sheet](https://www.owasp.org/index.php/Web_Service_Security_Testing_Cheat_Sheet)
3. [https://www.owasp.org/index.php/REST_Security_Cheat_Sheet](https://www.owasp.org/index.php/REST_Security_Cheat_Sheet)

**Tips** : Cara menggunakan self-signed certificate untuk webserver (NODEJS) : [https://github.com/coolaj86/nodejs-self-signed-certificate-example](https://github.com/coolaj86/nodejs-self-signed-certificate-example) 
Untuk production hendaklah menggunakan **Authorized SSL Certificate** dari Symantec,Digicert dll.
   
--------------------------------------------------


**5.0  Rekabentuk Struktur Endpoint URL Buku555**


<img src="{{ASSET_PATH}}/images/restdg.png"/>



Rekabentuk API untuk aplikasi Buku555 adalah seperti jadual di bawah. Setiap endpoint URL mempunyai
fungsi khusus yang berkaitan dengan CRUD. 

{: .table .table-striped}
|# | Endpoint URL                | Kaedah    |Parameter                | Keterangan                      | Token ? |
|--|-----------------------------|-----------|-----------------------------------------------------------|--------|
|1 | /users  	                 | POST	     | rujuk skema| rekod baru users | N |
|2 | /users/:userid              | GET	     | userid| baca rekod users | Y
|3 | /users/:userid	             | PUT	     | userid+rujuk skema| update rekod users | Y |
|4 | /users/:userid              | DELETE	 | userid| padam rekod users | Y |
|5 | /trxs       	             | POST	     | rujuk skema| transaksi baru | Y |
|6 | /trxs/:userid	             | GET	     | userid| baca transaksi/userid | Y |
|8 | /trxs/det/:trxid/:userid	 | GET	     | trxid,userid| transaksi detail | Y |
|9 | /trxs/det/:trxid/:userid    | PUT	     | trxid,userid| update transaksi/userid/trxid | Y |
|10 | /trxs/det/:trxid/:userid   | DELETE	 | trxid,userid| padam rekod transaksi/userid/trxid | Y |
|11 | /about	                 | GET	     | -| kredit aplikasi | N |
|12| /version                    | GET       | -| versi api | N |

----------------------------------------------------------------


**6.0 Sampel Aturcara (routes/index.js)**

Anda boleh merujuk kepada kod sumber penuh di Github [](). Penerangan aturcara akan saya kemaskini
atau boleh bertanyakan terus pada kotak diskusi di bawah post ini atau pada Github issues projek Buku555 []().

    var express = require('express');
    var router = express.Router();
    var auth = require('./auth.js');
    var user = require('./users.js');
    var info = require('./info.js');
    var trx  = require('./trxs.js');
    
    
    /*
     * Routes that can be accessed by any one
     */
    
    router.post('/login', auth.login);
    router.get('/about', info.info);
    router.get('/version', info.version);
    router.get('/testoracle',user.testoracle); //disable in production ..
    
    router.post('/register', user.adduser); // rekod baru users , no auth!
    
    /*
     * Routes that can be accessed only by authenticated users
     */
    
    /*
    #	Endpoint URL	Kaedah	Parameter	Keterangan
    1	/users	POST	tba	rekod baru users
    2	/users/:userid	GET	tba	baca rekod users
    3	/users/:userid	PUT	tba	update rekod users
    4	/users/:userid	DELETE	tba	padam rekod users
    5	/trxs	POST	tba	transaksi baru
    6	/trxs/:userid	GET	tba	baca transaksi/userid
    7	/trxs/:userid	PUT	tba	update transaksi/userid
    8	/trxs/:trxid/:userid	DELETE	tba	padam rekod transaksi
    9	/about	GET	tba	kredit aplikasi
    10	/version	GET	tba
    */
    
    // endpoints users
    
    //router.post('/api/v1/users', user.adduser); // rekod baru users , no auth!
    router.get('/api/v1/users/:userid', user.readuser); // baca rekod users
    router.put('/api/v1/users/:userid', user.updateuser); // kemaskini rekod users
    //router.delete('/api/v1/users/:userid', user.delete); // not implemented
    
    // endpoints transactions
    
    router.get('/api/v1/trxs/:userid',trx.readtxn);
    router.post('/api/v1/trxs',trx.addtxn);
    router.put('/api/v1/trxs/:trxid/:userid',trx.updatetxn);
    router.delete('/api/v1/trxs/:trxid/:userid',trx.deletetxn);
    
    module.exports = router;    


**7.0 Middleware JSON Web Token**

Saya menulis lebih lanjut mengenai JWT disini [http://www.shmn.my/2015/11/07/jwt-json-web-token---satu-pengenalan/](http://www.shmn.my/2015/11/07/jwt-json-web-token---satu-pengenalan/). Dalam aplikasi Buku555, middleware JWT digunakan
dalam **routes/users.js** dan **middlewares/validateRequest.js** . Contoh menjana **token** semasa
pendaftaran baru pengguna (routes/users.js). Saya menggunakan pustaka nodejs jwt-simple [https://www.npmjs.com/package/jwt-simple](https://www.npmjs.com/package/jwt-simple).


    function genToken(user) {
        var expires = expiresIn(7); // 7 days
        var token = jwt.encode({
            exp: expires,
            user:user
        }, require('../config/secret')());
        return {
            token: token,
            expires: expires, // client should check token expire date
            user: user
        };
    }
    
    function expiresIn(numDays) {
        var dateObj = new Date();
        return dateObj.setDate(dateObj.getDate() + numDays);
    }
     
        
        
**8.0   Komponen - Rujuk package.json**

    {
      "name": "buku555",
      "version": "1.0.0",
      "description": "aplikasi buku hutang mudah",
      "main": "server.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "",
      "license": "",
      "dependencies": {
        "body-parser": "^1.14.1",
        "express": "^4.13.3",
        "jsonwebtoken": "^5.4.1",
        "jwt-simple": "^0.3.1",
        "md5": "^2.0.0",
        "moment": "^2.10.6",
        "morgan": "^1.6.1",
        "oracledb": "^1.3.0",
        "path": "^0.12.7"
      }
    }
   
    
**9.0 Pengujian API menggunakan aplikasi chrome POSTMAN**


