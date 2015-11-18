---
layout: post
title: "Penyelesaian : Prevent NodeJS+ExpressJS From Crashing"
description: ""
category: 
tags: []
---
{% include JB/setup %}

**Penyelesaian : Prevent NodeJS+ExpressJS From Crashing**

Setelah membaca posting di StackOverflow, ada yang mencadangkan guna **node-supervisor** (package npm),
ianya membolehkan server node restart automatik sekiranya ada masalah.

Antara kelebihan **node-supervisor**

1. runs your program
2. watches for code changes - hot-code reloading-ish behaviour
3. no memory leaks 

----> kudos to the developer of **node-supervisor**. [https://github.com/petruisfan/node-supervisor](https://github.com/petruisfan/node-supervisor)

