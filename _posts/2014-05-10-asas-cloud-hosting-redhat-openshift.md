---
layout: post
title: "Asas Cloud Hosting Redhat Openshift"
description: ""
category: development
tags: [cloud,openshift]
---
{% include JB/setup %}

**Memasang dan Membina Aplikasi di Redhat OpenShift**

Apa itu OpenShift ? --> [https://www.openshift.com](https://www.openshift.com)

Semua aplikasi yang dipasang pada cloud OpenShift menggunakan pengawal kod sumber dan versioning **Git**.  
Anda buat kod dalam komputer anda dan 'push' sebarang perubahan ke server OpenShift.  

Ianya percuma dan berbaloi untuk pengujian dan pembangunan.

<!-- more --> 

Satu kelebihan **Git** adalah tidak memerlukan anda sepanjang masa talian internet untuk anda bekerja.  
Cuma nasihat saya, cuba lupakan pengalaman anda menggunakan ftp,sftp sekiranya ingin menggunakan  
perkhidmatan OpenShift. Berlatihlah menggunakan **Git**. Google untuk membantu proses pemahaman anda.  
Install utiliti **rhc** (memerlukan ruby dipasang pada komputer anda).  

**Menggunakan Repositori Git**

Sekiranya anda telah mempunyai akaun OpenShift, untuk versi percuma anda boleh mencipta maksimun 3 aplikasi.  
Banyak bahasa yang disediakan seperti Java,PHP,Phyton,Ruby. Panel pada laman kawalan OpenShift adalah  
seperti berikut :    

<img src="{{ASSET_PATH}}/images/oshift1.png" align="left"/>   

<img src="{{ASSET_PATH}}/images/oshift2.png" align="left"/>   

<img src="{{ASSET_PATH}}/images/oshift3.png" align="left"/>   

Pada terminal boleh taip :  

$ git clone <git url/link> <nama direktori nak cipta> 

**Kemaskini Perubahan Kod Ke Server Openshift**

$ git add .   
$ git commit -m "Versi 1. Testing PHP SLIM Restfull Api"  

$ git push

bila 'push' siap, anda boleh paparkan aplikasi pada URL yang diberikan oleh OpenShift. 


**Aturan Sambungan Ke MySql Dengan PHP**

	$mysqlCon = mysqli_connect(getenv('OPENSHIFT_MYSQL_DB_HOST'), getenv('OPENSHIFT_MYSQL_DB_USERNAME'), getenv('OPENSHIFT_MYSQL_DB_PASSWORD'), "", getenv('OPENSHIFT_MYSQL_DB_PORT')) or die("Error: " . mysqli_error($mysqlCon));

	mysqli_select_db($mysqlCon, getenv('OPENSHIFT_APP_NAME')) or die("Error: " . mysqli_error($mysqlCon));  


**@**

	define('DB_HOST', getenv('OPENSHIFT_MYSQL_DB_HOST'));
	define('DB_PORT', getenv('OPENSHIFT_MYSQL_DB_PORT'));
	define('DB_USER', getenv('OPENSHIFT_MYSQL_DB_USERNAME'));
	define('DB_PASS', getenv('OPENSHIFT_MYSQL_DB_PASSWORD'));
	define('DB_NAME', getenv('OPENSHIFT_GEAR_NAME'));

	$dbhost = constant("DB_HOST"); // Host name 
	$dbport = constant("DB_PORT"); // Host port
	$dbusername = constant("DB_USER"); // Mysql username 
	$dbpassword = constant("DB_PASS"); // Mysql password 
	$db_name = constant("DB_NAME"); // Database name 






