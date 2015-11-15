---
layout: post
title: "Latihan : Pengenalan Komponen KendoUI Mobile"
description: ""
category: 
tags: [kendo]
---
{% include JB/setup %}


**Latihan Pengenalan KendoUI Mobile**

**Pengenalan**

Kendo UI menyediakan  Widget khas untuk sentuhan (touch) yang akan digunakan dalam pembinaan
aplikasi telefon pintar dan tablet berasaskan teknologi HTML5. 

Kendo UI sesuai digunakan untuk aplikasi SPA (Single Page Application), dengan UI yang sesuai
tanpa perlu page refresh untuk paparan.

Kendo UI juga mempunyai ciri MVVM (Model-View-View-Model). Konsep MVVM ini secara ringkasnya,
untuk membolehkan kita integrasi data(Model),fungsi logik(View-Model) ke dalam fungsi paparan(View).

Berikut adalah komponen penting KendoUI Mobile. Copy/paste sample kod dibawah dan fahamkan. 

**1. ActionSheet**

    <a data-role="button" data-rel="actionsheet" href="#actionsheet">Open</a>
      <ul id="actionsheet" data-role="actionsheet" data-cancel="Close">
        <li><a>Foo</a></li>
        <li><a>Bar</a></li>
      </ul>

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/actionsheet](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/actionsheet)

**2. BackButton**

    <a data-role="backbutton">Back</a>

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/backbutton](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/backbutton)

**3. Button**

    <a data-role="button" data-badge="10">Foo</a>
    
Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/button](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/button)

**4. ButtonGroup**

    <ul data-role="buttongroup" data-enable="false">
        <li>Option 1</li>
        <li>Option 2</li>
        <li>Option 3</li>
      </ul>

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/buttongroup](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/buttongroup)

**5. Collapsible**

    <div id="collapsible" data-role="collapsible" data-animation="false">
            <h2>Header</h2>
            <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Phasellus sed purus sed orci aliquet dapibus.</p>
    </div>

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/collapsible](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/collapsible)

**6. DetailButton**

    <ul data-role="listview">
        <li>Item 1<a data-role="detailbutton"></a></li>
        <li>Item 2<a data-role="detailbutton"></a></li>
      </ul>
      
Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/detailbutton](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/detailbutton)     
      
**7. Drawer**

Untuk Drawer, saya telah masukkan siap siap contoh dalam folder **src/menu/menu.html** . Ini kerana ia mengandungi
link kepada halaman (view) untuk Widget kendoUI yang terlibat dalam latihan ini.

Contoh kod : 

    <div id="drawer">
        <h3>Sports</h3>
        <a href="#" data-target="baseball" class="drawer-link active">Baseball</a>
        <a href="#" data-target="golf" class="drawer-link">Golf</a>
    </div>
    
    <div id="content-container">
        <a id="drawer-trigger" href="#"><span>Show drawer</span></a>
        <div id="baseball" class="inner-content">
            <h3>Baseball</h3>
        </div>
        <div id="golf" class="inner-content">
            <h3>Golf</h3>
        </div>
    </div>
    
    <script>
        $(function() {
            $("#drawer").kendoMobileDrawer({
                container: "#content-container"
            });
    
            $("#drawer-trigger").click(function() {
                $("#drawer").data("kendoMobileDrawer").show();
                return false;
            });
    
            $(".drawer-link").click(function() {
                $("#drawer").data("kendoMobileDrawer").hide();
                $(".drawer-link").removeClass("active");
                $(this).addClass("active");
                return false;
            });
    
            $(".drawer-link").click(function(){
                  $(".inner-content").hide();
                  $("#"+$(this).data("target")).show();
            });
        });
    </script>


Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/drawer](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/drawer)

**8. Layout**



Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/layout](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/layout)

**9. ListView**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/listview](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/listview)

**10. Loader**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/loader](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/loader)

**11. MobileWidget**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/mobilewidget](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/mobilewidget)

**12. ModalView**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/modalview](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/modalview)

**13. NavBar**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/navbar](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/navbar)

**14. Pane**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/pane](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/pane)

**15. PopOver**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/popover](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/popover)

**16. Scroller dan ScrollView**

Rujukan Scroller [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/scroller](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/scroller)

Rujukan ScrollView [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/scrollview](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/scrollview)
 
**17. SplitView**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/splitview](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/splitview)

**18. Switch**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/switch](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/switch)

**19. TabStrip**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/tabstrip](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/tabstrip)

**20. Touch**

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/touch](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/touch)

**21. View**

View adalah halaman aplikasi kita. Setiap **view** hendaklah mempunyai ID unik (tidak boleh nama serupa) dengan
lain lain **view**. Saya telah masukkan siap siap dalam aplikasi contoh UMTKENDO.

Contoh kod : 

    <div data-role="view" data-model="foo">
       <span data-bind="text:bar"></span>
    </div>
    
Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/view](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/view)

**22. Application**

Fungsi utama dalam index.html yang akan init kendoUI Mobile. Ini telah dimasukkan siap siap dalam aplikasi contoh
UMTKENDO.

Contoh kod : 

    <div data-role="view"><a data-role="button">Foo</a></div>
    
    <div data-role="view" id="bar"><a data-role="button">Bar</a></div>
    
    <script>
    new kendo.mobile.Application($(document.body), { initial: "#bar" });
    </script>
    
    
Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/application](http://docs.telerik.com/kendo-ui/api/javascript/mobile/application)


**Selamat Mencuba, Jika Ada Masalah Terus Tanya !**