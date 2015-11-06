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
    
    
**Konfigurasi Pangkala Data**    

Selepas selesai rpm install, jawab soalan2 berikut : 

    1.the APEX http port (8080 by default)
    2.the database (TNS) listener port (1521 by default)
    3.A single password to be assigned to the database SYS and SYSTEM users
    4.whether you want the database to start automatically when the system starts (Yes by default)
    Unless you have other software, or Oracle Instances, running elsewhere, the defaults should be fine.

**Arahan initial setup oracle XE**


    /etc/init.d/oracle-xe configure

Output seperti di bawah : 
  
    Oracle Database 11g Express Edition Configuration
    -------------------------------------------------
    This will configure on-boot properties of Oracle Database 11g Express 
    Edition.  The following questions will determine whether the database should 
    be starting upon system boot, the ports it will use, and the passwords that 
    will be used for database accounts.  Press <Enter> to accept the defaults. 
    Ctrl-C will abort.
    
    Specify the HTTP port that will be used for Oracle Application Express [8080]:8080
    
    Specify a port that will be used for the database listener [1521]:1521
 
    Specify a password to be used for database accounts.  Note that the same
    password will be used for SYS and SYSTEM.  Oracle recommends the use of 
    different passwords for each database account.  This can be done after 
    initial configuration:
    Confirm the password:
 
    Do you want Oracle Database 11g Express Edition to be started on boot (y/n) [y]:y
 
    Starting Oracle Net Listener...Done
    Configuring database...Done
    Starting Oracle Database 11g Express Edition instance...Done
    Installation completed successfully.



**Konfigurasi Environment Oracle (User Oracle)**



<img src="{{ASSET_PATH}}/images/ora1vibashprofile.png" align="left"/> 
Log masuk sebagai user oracle. Boleh guna **su- oracle**

<img src="{{ASSET_PATH}}/images/ora1oraenv.png" align="left"/> 
Buka sebarang editor (nano,vi ..) untuk cipta fail .bash_profile sekiranya belum wujud.
Aturan .bash_profile

<img src="{{ASSET_PATH}}/images/ora1nlslangterm.png" align="left"/>

<img src="{{ASSET_PATH}}/images/ora1nlslang.png" align="left"/>
Kemaskini fail nls_lang.sh pada baris terakhir. masukkan "" untuk 

    NLS_LANG="${nlslang}.${charset}"
    echo $NLS_LANG
  
Uji capaian dengan menggunakan **sqlplus**

<img src="{{ASSET_PATH}}/images/ora1sqlplus.png" align="left"/>



**Tahniah ! Pemasangan telah selesai. Reboot server anda ..**

YOUTUBE : Screencast Pemasangan OracleXE 11g Pada Centos 7

<iframe width="600" height="400" src="//www.youtube.com/embed/6M2mHXmuRGs" frameborder="0" allowfullscreen></iframe>
