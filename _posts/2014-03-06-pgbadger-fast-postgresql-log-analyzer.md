---
layout: post
title: "PgBadger Untuk Menyemak Log Pangkalan Data PostgreSQL - Bahagian I"
description: ""
category: postgreSQL
tags: [postgres, performance]
---
{% include JB/setup %}

For those of you who haven't known about pgBadger yet, here is a brief description about it:

pgBadger is a PostgreSQL log analyzer build for speed with fully detailed reports from your PostgreSQL log file. It's a single and small Perl script that outperform any other PostgreSQL log analyzer.

It is written in pure Perl language and uses a javascript library (flotr2) to draw graphs so that you don't need to install any additional Perl modules or other packages. Furthermore, this library gives us more features such as zooming. pgBadger also uses the Bootstrap javascript library and the FontAwesome webfont for better design. Everything is embedded.

<!-- more -->

Article's Outline

1. Installation
2. Sample Report
3. Sanity Checking With SAR Report
4. Troubleshoot PostgreSQL Performance