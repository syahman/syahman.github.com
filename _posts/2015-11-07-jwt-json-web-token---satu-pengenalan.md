---
layout: post
title: "JWT (JSON Web Token)   Satu Pengenalan"
description: ""
category: 
tags: []
---
{% include JB/setup %}


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
yang digunakan sekarang **deprecated** atau **obsolete**. 

Ada dua cara kaedah **authentication** . Samada menggunakan Cookie atau Token

<img src="{{ASSET_PATH}}/images/cookies.png" align="left"/>