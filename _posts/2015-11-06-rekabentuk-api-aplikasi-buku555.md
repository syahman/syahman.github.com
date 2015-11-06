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

Setiap request akan ada reply. Jadual di bawah adalah contoh kod status HTTP. Anda akan lebih memahami
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

**4.0	Endpoint URL**

Endpoint URL dalam rekabentuk API hendaklah mudah difahami dan berfungsi dengan baik. 
Setiap URL untuk setiap fungsi aplikasi hendaklah dikenalpasti. Penggunaan API key diperlukan
untuk akses data sensitif dan disaran menggunakan secure HTTP (https) untuk mengelakkan pencerobohan data oleh
orang tengah (man-in-the-middle attack). Rujuk lebih lanjut OWASP bab API, web services. API key 
diletakkan dalam header HTTP, bukan diletakkan sekali dalam URL. contoh endpoint URL : 

    GET http://buku555.abc/users/:1
    guna method GET untuk dapatkan rekod users yang mempunyai userid=1 (contoh)
    
    POST http://buku555.abc/users/
    guna method POST untuk masukkan rekod users baru
    
--------------------------------------------------


**5.0  Rekabentuk Struktur Endpoint URL Buku555**

Rekabentuk API untuk aplikasi Buku555 adalah seperti jadual di bawah. Setiap endpoint URL mempunyai
fungsi khusus yang berkaitan dengan CRUD. 

{: .table .table-striped}
|# | Endpoint URL                | Kaedah    |Parameter                | Keterangan                      |
|--|-----------------------------|-----------|-----------------------------------------------------------|
|1 | /users  	                 | POST	     | tba| rekod baru users |
|2 | /users/:userid              | GET	     | tba| baca rekod users |
|3 | /users/:userid	             | PUT	     | tba| update rekod users |
|4 | /users/:userid              | DELETE	 | tba| padam rekod users |
|5 | /trxs       	             | POST	     | tba| transaksi baru |
|6 | /trxs/:userid	             | GET	     | tba| baca transaksi/userid |
|7 | /trxs/:userid	             | PUT	     | tba| update transaksi/userid |
|8 | /trxs/:trxid/:userid        | DELETE	 | tba| pada rekod transaksi |
|9 | /about	                     | GET	     | tba| kredit aplikasi |
|10| /version                    | GET       | tba| versi api |

----------------------------------------------------------------
