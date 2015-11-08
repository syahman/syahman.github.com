---
layout: post
title: "JWT (JSON Web Token)   Satu Pengenalan"
description: ""
category: 
tags: []
---
{% include JB/setup %}


**Sumber Rujukan :**

<iframe width="600" height="400" src="//www.youtube.com/embed/oXxbB5kv9OA" frameborder="0" allowfullscreen></iframe>



**1.0   Pendahuluan**

Mengapa setiap kali menggunakan aplikasi internet, kita perlu log masuk ? Sudah tentu! sebagai langkah
keselamatan yang disediakan oleh penyedia perkhidmatan. Sebagai contoh, semasa menggunakan
aplikasi web Maybank2u kita akan memasukkan ID pengguna dan kata laluan beserta pengecaman imej. 
Dari segi pembangunan aplikasi berasaskan web ini, para pengaturcara menggunakan kaedah **cookies** untuk
menyimpan maklumat pengguna semasa mereka menggunakan aplikasi. Pengguna disaran tidak mematikan fungsi
**cookies** supaya aplikasi dapat menyimpan maklumat yang diperlukan dalam pelayar internet semasa menggunakan
aplikasi web. 

Bagaimana pula sekiranya anda menggunakan aplikasi mudah alih ? Memang, kerja-kerja nak menaip kata laluan
dan id pengguna setiap kali menggunakan aplikasi adalah menyusahkan. Ini peranti saya, mengapa perlu keyin
setiap kali. Sedikit permasalahan ini telah diselesaikan dengan adanya kaedah kaedah baru untuk melindungi
data pengguna walaupun mereka tidak log masuk setiap kali menggunakan aplikasi. Ya, ini disebabkan peranti
anda telah menyimpan **token** yang berupaya mengecam anda setiap kali menggunakan aplikasi. 


**2.0   Cookies vs Token**

Setiap teknologi mesti ada kelebihan masing masing. Tetapi inovasi akan memudahkan dan menyebabkan teknologi
yang digunakan sekarang **deprecated** atau **obsoleted**. 

Ada dua cara kaedah **authentication** . Samada menggunakan Cookies atau Token

<img src="{{ASSET_PATH}}/images/cookies.png"/>
<span style="display:block;">**authentication** berasaskan **cookies**</span>

-----------------------------------------------------------------

Masalah Cookies

1. Hard to scale
2. Performance bottlenecks
3. Requires state (session) persistence
4. Troublesome Cross-origin request sharing (CORS), Vulnerable to CSRF attacks
5. Hacky” implementations in MV*


<img src="{{ASSET_PATH}}/images/token.png"/>
<span style="display:block;">**authentication** berasaskan **token**</span>

-----------------------------------------------------------------

Kelebihan Token

1. Easier to scale
2. Stateless
3. Secure
4. Performant
5. Cross-origin request sharing (CORS)


**3.0   Apakah JSON Web Tokens (JWT) ?**
 

**JSON Web Token** adalah standard baru industri (RFC 7519 - rujuk Internet Engineering Task Force [https://tools.ietf.org/html/rfc7519](https://tools.ietf.org/html/rfc7519).
Disebut dalam English sebagai "jot", membolehkan maklumat dibawa dalam bentuk JSON dengan selamat. 

**JSON Web Tokens** adalah terbuka, kaedah yang mengesahkan identiti (tuntutan?)  antara dua pihak. 

**JSON Web Tokens** boleh didapati dalam pustaka .NET, Python, Node.js, Java, PHP, Ruby, Go, JavaScript, dan Haskell.
Implementasi boleh digunakan dalam pelbagai senario.

JWTs membawa pakej maklumat sendiri : JWT membolehkan maklumat asas pengguna diletakkan dalam token dalam bentuk **payload** Biasanya token JWT terdiri daripada 3 komponen asas,
Header,Payload,Signature. Contoh JWT  seperti di bawah : 

<img src="{{ASSET_PATH}}/images/jwttoken.png"/>

JWT boleh dihantar dengan mudah. Boleh dimasukkan dalam HTTP header, kaedah POST atau diletakkan
dalam URL (kaedah GET). 

**Tips** : Jika saiz JWT besar (sebab banyak sangat payload dimasukkan), lebih sesuai letak dalam HTTP header atau kaedah POST.

**4.0   Bagaimana JWT Berfungsi**
 
TODO : 

**5.0   Senario 1 - Aplikasi Mudah Alih <-> Pelayan RESTfull API**
 
TODO: 

**6.0   Senario 2 - Sebagai Single Sign On Server Dalaman (Local SSO)** 

TODO : 

**7.0   Rujukan dan Kajian Akademik**

TODO : 
 
1. [https://scotch.io/tutorials/the-anatomy-of-a-json-web-token](https://scotch.io/tutorials/the-anatomy-of-a-json-web-token) 