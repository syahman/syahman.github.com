---
layout: post
title: "Pemasangan,menguji REST API menggunakan NodeJS+ExpressJS+Oracle DB stack"
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
<span style="display:block;">ERD ringkas skema data. Boleh rujuk lampiran **skema_design.sql** dalam github projek Buku555.</span>

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
. Run arahan di bawah : 

      wget https://nodejs.org/dist/v0.12.7/node-v0.12.7-linux-x64.tar.gz
      tar xzf node-v0.12.7-linux-x64.tar.gz
      cd node-v0.12.7-linux-x64/
      ls
      for dir in bin include lib share; do cp -par ${dir}/* /usr/local/${dir}/; done
      node -v
      npm -v
    

**Cipta folder projek**

Katakan, anda berada dalam direktori **/home/shmn** (contoh je ni .. ) sebagaimana contoh berikut : 

    [root@localhost shmn]# mkdir buku555
    [root@localhost shmn]# cd buku555
    [root@localhost buku555]# npm init
    This utility will walk you through creating a package.json file.
    It only covers the most common items, and tries to guess sensible defaults.
    
    See `npm help json` for definitive documentation on these fields
    and exactly what they do.
    
    Use `npm install <pkg> --save` afterwards to install a package and
    save it as a dependency in the package.json file.
    
    Press ^C at any time to quit.
    name: (buku555)
    version: (1.0.0)
    description: aplikasi buku hutang mudah
    entry point: (index.js)
    test command:
    git repository:
    keywords:
    author:
    license: (ISC)
    About to write to /home/shmn/buku555/package.json:
    
    {
      "name": "buku555",
      "version": "1.0.0",
      "description": "aplikasi buku hutang mudah",
      "main": "index.js",
      "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "author": "",
      "license": "ISC"
    }
    
    
    Is this ok? (yes) yes
    [root@localhost buku555]#
    

**Pemasangan ExpressJS**

Masih lagi berada dalam direktori **buku555**, taip arahan berikut : 

    [root@localhost buku555]# npm install express -save
    npm WARN package.json buku555@1.0.0 No repository field.
    npm WARN package.json buku555@1.0.0 No README data
    express@4.13.3 node_modules/express
    ├── escape-html@1.0.2
    ├── merge-descriptors@1.0.0
    ├── array-flatten@1.1.1
    ├── cookie@0.1.3
    ├── utils-merge@1.0.0
    ├── cookie-signature@1.0.6
    ├── methods@1.1.1
    ├── fresh@0.3.0
    ├── range-parser@1.0.3
    ├── vary@1.0.1
    ├── path-to-regexp@0.1.7
    ├── etag@1.7.0
    ├── content-type@1.0.1
    ├── parseurl@1.3.0
    ├── content-disposition@0.5.0
    ├── serve-static@1.10.0
    ├── depd@1.0.1
    ├── qs@4.0.0
    ├── finalhandler@0.4.0 (unpipe@1.0.0)
    ├── debug@2.2.0 (ms@0.7.1)
    ├── on-finished@2.3.0 (ee-first@1.1.1)
    ├── proxy-addr@1.0.8 (forwarded@0.1.0, ipaddr.js@1.0.1)
    ├── accepts@1.2.13 (negotiator@0.5.3, mime-types@2.1.7)
    ├── type-is@1.6.9 (media-typer@0.3.0, mime-types@2.1.7)
    └── send@0.13.0 (destroy@1.0.3, statuses@1.2.1, ms@0.7.1, mime@1.3.4, http-errors@1.3.1)
    [root@localhost buku555]# ls
    node_modules  package.json
    [root@localhost buku555]# cd node_modules/
    [root@localhost node_modules]# ls
    express
    [root@localhost node_modules]#
    
**Pemasangan Modul body-parser**

Masih lagi berada dalam direktori **buku555**, taip arahan berikut : 

    [root@localhost buku555]# npm install body-parser -save
    npm WARN package.json buku555@1.0.0 No repository field.
    npm WARN package.json buku555@1.0.0 No README data
    body-parser@1.14.1 node_modules/body-parser
    ├── bytes@2.1.0
    ├── content-type@1.0.1
    ├── depd@1.1.0
    ├── qs@5.1.0
    ├── iconv-lite@0.4.12
    ├── on-finished@2.3.0 (ee-first@1.1.1)
    ├── raw-body@2.1.4 (unpipe@1.0.0)
    ├── http-errors@1.3.1 (inherits@2.0.1, statuses@1.2.1)
    ├── debug@2.2.0 (ms@0.7.1)
    └── type-is@1.6.9 (media-typer@0.3.0, mime-types@2.1.7)
    [root@localhost buku555]#
    

**Pemasangan Driver Native NodeJS-ORACLE**

Masih lagi berada dalam direktori **buku555**, taip arahan berikut : 

    [root@localhost buku555]# npm install oracledb -save
    npm WARN package.json buku555@1.0.0 No repository field.
    npm WARN package.json buku555@1.0.0 No README data
    -
    > oracledb@1.3.0 install /home/shmn/buku555/node_modules/oracledb
    > node-gyp rebuild
    
    make: Entering directory `/home/shmn/buku555/node_modules/oracledb/build'
      CXX(target) Release/obj.target/oracledb/src/njs/src/njsOracle.o
      CXX(target) Release/obj.target/oracledb/src/njs/src/njsPool.o
      CXX(target) Release/obj.target/oracledb/src/njs/src/njsConnection.o
      CXX(target) Release/obj.target/oracledb/src/njs/src/njsResultSet.o
      CXX(target) Release/obj.target/oracledb/src/njs/src/njsMessages.o
      CXX(target) Release/obj.target/oracledb/src/njs/src/njsIntLob.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiEnv.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiEnvImpl.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiException.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiExceptionImpl.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiConnImpl.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiDateTimeArrayImpl.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiPoolImpl.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiStmtImpl.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiUtils.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiLob.o
      CXX(target) Release/obj.target/oracledb/src/dpi/src/dpiCommon.o
      SOLINK_MODULE(target) Release/obj.target/oracledb.node
      COPY Release/oracledb.node
    make: Leaving directory `/home/shmn/buku555/node_modules/oracledb/build'
    oracledb@1.3.0 node_modules/oracledb
    └── nan@1.9.0
    [root@localhost buku555]#
    

    
**Rekabentuk API**

Bab ini agak panjang, saya pisahkan menjadi satu bab khusus.
[http://www.shmn.my/2015/11/06/rekabentuk-api-aplikasi-buku555/](http://www.shmn.my/2015/11/06/rekabentuk-api-aplikasi-buku555/)
Semoga bermanfaat. 


**Pengujian API menggunakan klien REST :: POSTMAN (chrome packaged app)**

**Aplikasi pada platform mudah alih - hybrid phonegap/cordova**

**Aplikasi pada platform mudah alih - native android**

will update later..


