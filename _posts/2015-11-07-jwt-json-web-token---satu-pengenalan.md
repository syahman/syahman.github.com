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

<img src="{{ASSET_PATH}}/images/cookies.png" align="left"/>
<span style="display:block;">**authentication** berasaskan **cookies**</span>
-----------------------------------------------------------------
Masalah Cookies

1. Hard to scale
2. Performance bottlenecks
3. Requires state (session) persistence
4. Troublesome Cross-origin request sharing (CORS), Vulnerable to CSRF attacks
5. Hacky” implementations in MV*


<img src="{{ASSET_PATH}}/images/token.png"/>
**authentication** berasaskan **token**

Kelebihan Token
-----------------------------------------------------------------
1. Easier to scale
2. Stateless
3. Secure
4. Performant
5. Cross-origin request sharing (CORS)

