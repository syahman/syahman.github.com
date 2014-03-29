---
layout: post
title: "Pemantauan Keupayaan OS (Linux) Menggunakan SysUsage"
description: ""
category: performance
tags: [performance,linux]
---
{% include JB/setup %}

SysUsage ( [SysUsage GitHub Repo](https://github.com/darold/sysusage) ) adalah perisian yang memantau keupayaan OS dan menjana laporan dalam bentuk graf secara berkala menggunakan data [SAR](http://www.linuxjournal.com/content/sysadmins-toolbox-sar)(System Activity Report). Integrasi dengan utiliti [rrdtool](http://oss.oetiker.ch/rrdtool) dan pustaka javascript yang mampu membuat plot/graf untuk memaparkan keupayaan dan prestasi semasa OS.Laporan ini akan dipaparkan pada antaramuka web. 

<!-- more -->

Manual pemasangan dan dokumentasi boleh diperolehi di [sini] (http://sysusage.darold.net). Bagi pengguna Centos atau RedHat,Fedora boleh menggunakan repo rpm (EPEL) di [sini] (http://pkgs.org/centos-6/epel-i386/sysusage-5.3-5.el6.noarch.rpm.html). 

Windows OS ? SysUsage untuk unix/linux sahaja. Tetapi saya ada terjumpa blog untuk menjana laporan daripada Windows Perfmon, juga menggunakan rrdtool di [sini] (http://www.ludovicocaldara.net/dba/generating-graphs-massively-from-windows-performance-counters-logs/). Rujuk artikel saya [Gabungan PHP/rrdtools Untuk Menjana Graf Keupayaan Windows OS] (windows-php-rrdtools.html).

Saya kerapkali menggabungkan analisis data OS yang dijana oleh SysUsage dengan pgBadger untuk semakan keupayaan dan prestasi serta perbandingan pangkalan data PostgreSQL. 



