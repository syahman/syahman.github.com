---
layout: post
title: "Rekabentuk,memasang,menguji REST API menggunakan NodeJS+ExpressJS+Oracle DB"
description: ""
category: 
tags: [rest,hybrid,oracle,nodejs,expressjs]
---
{% include JB/setup %}

**Pengenalan**

Tutorial pada kali ini membangunkan POC RESTfull API untuk digunakan pada aplikasi mudah alih atau sebarang aplikasi yang menggunapakai
kaedah API (**A**pplication **P**rogramming **I**nterface)

API ini penting untuk integrasi data pada aplikasi mudah alih. Selain memudahkan capaian data, perkongsian data menggunakan JSON dilihat
tidaklah rumit berbanding XML. Kaedah **web services** ini telah lama diimplementasi dalam integrasi antara aplikasi/sistem,platform seperti SOAP protokol.

Keperluan bisnes dan integrasi data pada platform mudah alih merancakkan lagi penggunaan API. Selain data mudah dikongsi, ia juga mampu melindungi
data sulit sekiranya menggunakan kaedah dan rekabentuk yang mengambilkira aspek keselamatan data. 

Anda boleh merujuk kepada tutorial pemasangan pangkalan data oracle 11g XE centos 7 di sini :
[http://www.shmn.my/2015/10/30/panduan-pemasangan-oraclexe-pada-server-centos/](http://www.shmn.my/2015/10/30/panduan-pemasangan-oraclexe-pada-server-centos/)

**Skema Data Contoh (Buku555)**

<img src="{{ASSET_PATH}}/images/b555.png" /> 
<span style="display:block;">Ini merupakan lakaran awal aplikasi Buku555 (saya jadikan contoh untuk kelas/latihan). </span>

<img src="{{ASSET_PATH}}/images/skema555.png" /> 
<span style="display:block;">ERD ringkas pangkalan data. Boleh rujuk lampiran skema_design.sql dalam github projek Buku555.</span>

    CREATE TABLE b_users
    ( userid number(10) NOT NULL,
      token varchar2(256) NOT NULL,
      name varchar2(256) NOT NULL,
      emel varchar2(256) NOT NULL,
      active number(1) NOT NULL,
      CONSTRAINT  b_users_pk PRIMARY KEY (userid),
      CONSTRAINT  b_users_uk UNIQUE (emel)
    );
    
    
    CREATE TABLE b_trx
    ( trxid number(10) NOT NULL,
      userid number(10) NOT NULL,
      amount number(7,2) NOT NULL,
      trxdate timestamp(6) NOT NULL,
      item varchar(256) NOT NULL,
      active number(1) NOT NULL,
      CONSTRAINT b_trx_pk PRIMARY KEY (trxid),
      CONSTRAINT b_trx_fk
      FOREIGN KEY (userid)
      REFERENCES b_users(userid)
    ); 


    CREATE INDEX b_users_idx
      ON b_users (userid,emel);
    
    CREATE INDEX b_trx_idx
      ON b_trx (trxid,userid);
      

**Pemasangan NodeJS**

Saya menggunakan versi nodejs 0.12.7 kerana versi terkini tidak dapat dikompil bersama modul nodejs oracledb.
Rujuk pada github nodejs oracle driver [https://github.com/oracle/node-oracledb](https://github.com/oracle/node-oracledb)
Run arahan di bawah : 

      wget https://nodejs.org/dist/v0.12.7/node-v0.12.7-linux-x64.tar.gz
      tar xzf node-v0.12.7-linux-x64.tar.gz
      cd node-v0.12.7-linux-x64/
      ls
      for dir in bin include lib share; do cp -par ${dir}/* /usr/local/${dir}/; done
      node -v
      npm -v
    

**Pemasangan ExpressJS**

sdfsdfsdf

**Pemasangan Driver Native NodeJS-ORACLE**

**Rekabentuk API**

**Pengujian API menggunakan klien REST :: POSTMAN (chrome packaged app)**

**Aplikasi pada platform mudah alih - hybrid phonegap/cordova**

**Aplikasi pada platform mudah alih - native android**

will update later..


