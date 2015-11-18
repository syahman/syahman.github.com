---
layout: post
title: "Penyelesaian : Persistence Data Sync Problem Semasa Operasi Insert"
description: ""
category: 
tags: []
---
{% include JB/setup %}


**Penyelesaian : Persistence Data Sync Problem Semasa Operasi Insert**

Ketika mengendalikan kursus mobile hybrid, saya perasan masalah ini. Oleh kerana 
primary key dijana secara auto (incremental number), saya tidak dapat sync data dengan sempurna, sebab
data di server dikongsi oleh ramai pengguna. Operasi **Read Update Delete** tiada masalah kerana Apps
hanya perlu resync balik data,reference semula UUIDs untuk dapatkan data terkini dari server. 

lakaran dibawah menggambarkan solution yang mungkin boleh digunakan : 

<img src="{{ASSET_PATH}}/images/uuids.png"/>

-----------------------------------------------------

