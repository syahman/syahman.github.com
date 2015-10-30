---
layout: post
title: "Panduan Pemasangan Oracle XE 11g Pada Server CentOS 7"
description: ""
category: 
tags: [oracle,centos]
---
{% include JB/setup %}


**Panduan Pemasangan Oracle XE 11g Pada Server Centos 7**

Pemasangan Oracle XE 11g (setakat ini Oracle masih belum release XE 12c,jadi guna 11g dulu) telah dipermudahkan. Pakej installer menggunakan rpm. Anda boleh
merujuk Google untuk pemasangan Oracle XE 11g pada distribution LINUX yang lain seperti Debian,Ubuntu,Mint dll. 
Tutorial ini hanya menggunakan contoh pemasangan pada Centos 7.

**Muat Turun Oracle XE 11g 64bit**

URL untuk muat turun (perlu daftar akaun dulu dengan ORACLE). 
[http://www.oracle.com/technetwork/database/database-technologies/express-edition/downloads/index.html](http://www.oracle.com/technetwork/database/database-technologies/express-edition/downloads/index.html)

**Peringantan** XE 11g hanya ada versi 64bit untuk LINUX. 


**Pemasangan Oracle XE 11g**

Proses pemasangan adalah mudah. Fail yang dimuatturun hendaklah extract terlebih dahulu.

```
cd $HOME/Downloads
ls -l
-rwxrwx---. 1 mike mike 315891481 Dec 16 20:21 oracle-xe-11.2.0-1.0.x86_64.rpm.zip
```

