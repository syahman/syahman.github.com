---
layout: post
title: "Rekabentuk API Aplikasi Buku555"
description: ""
category: 
tags: []
---
{% include JB/setup %}



**Rekabentuk API (Application Programming Interface) Untuk Aplikasi Buku555**

**1.0	Asas**

Arkitektur REST amat berguna untuk membangunkan aplikasi client/server berasaskan rangkaian.
Maksud REST adalah Representational State Transfer. 

    REST was initially proposed by Roy Thomas Fielding in his 2000 PhD dissertation "Architectural Styles and the Design of Network-based Software Architectures".
    Fielding developed the REST architectural style in parallel with HTTP 1.1 of 1996-1999, based on the existing design of HTTP 1.0 of 1996.

Implementasi REST lebih mudah berbanding kaedah lain seperti SOAP,CORBA,WSDL dll..
Ia hanya menggunakan protokol HTTP.

------------------------------------------------

**2.0   Kaedah HTTP**

Untuk merekabentuk API yang berguna, API hendaklah menyokong kaedah HTTP seperti
GET,POST,PUT dan DELETE. Ada lagi kaedah HTTP lain seperti OPTIONS,PATCH,HEAD tetapi jarang
digunakan. Setiap kaedah bergantung kepada keperluan aplikasi, sudah tentu setiap aplikasi
perlu ada CRUD (Create,Read,Update dan Delete). 

Cuba anda hubung kait kaedah di bawah ini dengan CRUD. 

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

**6.0 Pengujian API menggunakan aplikasi chrome POSTMAN**


