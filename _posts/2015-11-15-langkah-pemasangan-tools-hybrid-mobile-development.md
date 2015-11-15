---
layout: post
title: "Langkah Pemasangan Tools Hybrid Mobile Development"
description: ""
category: 
tags: [hybrid,taco,cordova]
---
{% include JB/setup %}

***Langkah Pemasangan Tools Hybrid Mobile Development***

1. nodejs : [https://nodejs.org/en/](https://nodejs.org/en/) (make sure 4 LTS)
2. nodejs version : node -v
3. check java : java -version
4. taco : sudo npm install -g taco-cli
5. taco create project : taco create hello 
6. cd hello
7. taco platform add browser
8. taco install-reqs browser
9. taco platform add android
10. taco install-reqs android
11. osx sahaja : taco platform add ios
12. osx sahaja : taco install-reqs ios
13. register akaun genymotion.com [https://www.genymotion.com](https://www.genymotion.com)
14. download genymotion [https://www.genymotion.com](https://www.genymotion.com)
15. download virtualbox [https://www.virtualbox.org/wiki/DownloadsVirtualBox](https://www.virtualbox.org/wiki/DownloadsVirtualBox) 5.0.10 for OS X hosts  amd64
16. install git client (windows) [https://git-scm.com/download/win](https://git-scm.com/download/win) (osx-built in)

----------------------------------------

***step to build/run***

Android ( install-reqs perlu run sekali sahaja! , bila create projek baru tak perlu run )

1. taco create hello my.edu.umt.hello
2. cd hello
3. taco platform add android
4. taco install-reqs android
5. taco build android
6. taco run android

IOS ( install-reqs perlu run sekali sahaja! , bila create projek baru tak perlu run )

1. taco create hello my.edu.umt.hello
2. cd hello
3. taco platform add ios
4. taco install-reqs ios
5. taco build ios
6. taco run ios



***semak adb device**

run command
    
    adb devices
    
    
    
***Daftar Akaun GitHub**
    
[http://www.github.com](http://www.github.com)
    
1. git clone https://github.com/telerik/whatsername.git 
   
2. cd whatsername

3. sudo npm install 
  
4. sudo npm install -g bower
 
5. bower install  
    
    



