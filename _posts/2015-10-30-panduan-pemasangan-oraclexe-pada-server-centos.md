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

**Peringatan** XE 11g hanya ada versi 64bit untuk LINUX. 


**Pemasangan Oracle XE 11g**

Proses pemasangan adalah mudah. Fail yang dimuatturun hendaklah extract terlebih dahulu.

    cd $HOME/Downloads
    ls -l
    -rwxrwx---. 1 shmn shmn 3234191481 Oct 30 20:21 oracle-xe-11.2.0-1.0.x86_64.rpm.zip
    
    
**Langkah seterusnya adalah extract guna unzip**


    unzip oracle-xe-11.2.0-1.0.x86_64.rpm.zip

**Output**

    creating: Disk1/
    creating: Disk1/upgrade/
    inflating: Disk1/upgrade/gen_inst.sql  
    creating: Disk1/response/
    inflating: Disk1/response/xe.rsp   
    inflating: Disk1/oracle-xe-11.2.0-1.0.x86_64.rpm 

**Guna akaun root, dan tukar direktori kepada Disk1**

    cd Disk1
    su

**Guna arahan rpm untuk pasang** 


    rpm -ivh oracle-xe-11.2.0-1.0.x86_64.rpm
    Preparing...                          ################################# [100%]
    Updating / installing...
    1:oracle-xe-11.2.0-1.0             ################################# [100%]
    Executing post-install steps...
    You must run '/etc/init.d/oracle-xe configure' as the root user to configure the database.
    
    
    


