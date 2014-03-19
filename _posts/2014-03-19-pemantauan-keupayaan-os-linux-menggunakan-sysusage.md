---
layout: post
title: "Pemantauan Keupayaan OS (Linux) Menggunakan SysUsage"
description: ""
category: performance
tags: [performance,linux]
---
{% include JB/setup %}

SysUsage ( [SysUsage GitHub Repo](https://github.com/darold/sysusage) ) adalah perisian yang memantau keupayaan OS dan menjana laporan dalam bentuk graf secara berkala menggunakan data [SAR](www.linuxjournal.com/content/sysadmins-toolbox-sar)(System Activity Report). Integrasi dengan utiliti [rrdtool](oss.oetiker.ch/rrdtool) dan pustaka javascript yang mampu membuat plot/graf untuk memaparkan keupayaan dan prestasi semasa OS. Laporan ini akan dipaparkan pada antaramuka web. 

<!-- more -->

Saya kerapkali menggabungkan analisis data OS yang dijana oleh SysUsage dengan pgBadger untuk semakan keupayaan dan prestasi serta perbandingan pangkalan data PostgreSQL. 

