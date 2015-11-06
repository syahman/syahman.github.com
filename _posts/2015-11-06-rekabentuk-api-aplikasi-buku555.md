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

**2.0   Kaedah HTTP**

Untuk merekabentuk API yang berguna, API hendaklah menyokong kaedah HTTP seperti
GET,POST,PUT dan DELETE. Ada lagi kaedah HTTP lain seperti OPTIONS,PATCH,HEAD tetapi jarang
digunakan. Setiap kaedah bergantung kepada keperluan aplikasi, sudah tentu setiap aplikasi
perlu ada CRUD (Create,Read,Update dan Delete). 

Cuba anda hubung kait kaedah di bawah ini dengan CRUD. 

| Kaedah | Keterangan                  |
|--------|-----------------------------|
| GET    | To fetch a resource         |
| POST   | To create a new resource    |
| PUT    | To update existing resource |
| DELETE | To delete a resource        |



