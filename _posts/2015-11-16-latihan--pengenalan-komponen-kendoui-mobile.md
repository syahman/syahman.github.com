---
layout: post
title: "Latihan : Pengenalan Komponen KendoUI Mobile"
description: ""
category: 
tags: [kendo]
---
{% include JB/setup %}


**Latihan Pengenalan KendoUI Mobile**

Untuk live demo keseluruhan penggunaan widget [http://demos.telerik.com/kendo-ui/m/index](http://demos.telerik.com/kendo-ui/m/index)

atau capture QR-CODE dibawah : 

<img src="{{ASSET_PATH}}/images/qrkendodemo.png"/>

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

Layout juga telah dimasukkan. Ia merupakan template yang akan mempengaruhi semua paparan (view). Boleh
rujuk dalam folder **src/shared/layouts**

Contoh kod : 
    
    <div data-role="view" data-layout="default">
      Foo view
    </div>
    
    <div data-role="layout" data-id="default">
      <header data-role="header"><p>the header</p></header>
    
      <div data-role="footer"><p>the footer</p></div>
    </div>    


Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/layout](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/layout)

**9. ListView**

     <ul data-role="listview" data-source="foo" data-pull-to-refresh="true" data-append-on-refresh="true" data-template="foo-template">
      </ul>
    </div>
    
    <script type="text/x-kendo-template" id="foo-template">
        #: name # - #: modified #
    </script>
    
    <script>
    var i = 0;
    
    // datasource below is customized for demo purposes.
    var foo = new kendo.data.DataSource({
      transport: {
        read: function(options) {
          var max = i + 5;
          var data = [];
          for (; i < max; i ++) {
            data.unshift({ name: "record" + i, modified: +new Date() });
          }
          // illustration purposes only
          setTimeout(function() {
              options.success(data);
          }, 1000);
    
        }
      }
    });
    
    
    </script>


Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/listview](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/listview)

**10. Loader**

Loader untuk menunjukkan loading animation. Kod telah dimasukkan siap siap.
    
    <div id="foo" data-role="view" data-show="onShow"></div>
    <script>
    
    function onShow() {
      umt.app.pane.loader.show();
      setTimeout(function() {
        umt.app.pane.loader.hide(); //hide loading animation
      }, 7000);
    }
    </script>


Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/loader](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/loader)

**11. MobileWidget**

    <a id="button" data-role="button">I am a mobile button</a>

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/mobilewidget](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/mobilewidget)

**12. ModalView**

    
    <a data-role="button"  data-click="openModal">open</a>
   
    
    <div data-role="modalview" id="foo" style="width: 200px; height: 200px">
        <a data-role="button"  data-click="closeModal">Close</a>
    </div>
    
    <script>
    function openModal() {
       $("#foo").data("kendoMobileModalView").open();
    }
    
    function closeModal() {
       $("#foo").data("kendoMobileModalView").close();
    }
    
   
    </script>


Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/modalview](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/modalview)

**13. NavBar**

   
      <header data-role="header">
        <div data-role="navbar">
          <a class="nav-button" data-align="left" data-icon="action" data-role="button"></a>
          <span data-role="view-title"></span>
          <a class="nav-button" data-align="right" data-icon="refresh" data-role="button"></a>
        </div>
      </header>
      <a data-role="button" data-click="onClick">Button</a>
    
    
    <script>
    
    function onClick(e) {
      var navbar = umt.app.view()
        .header
        .find(".km-navbar")
        .data("kendoMobileNavBar");
    
      navbar.destroy();
    }
    </script>
    

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/navbar](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/navbar)

**14. Pane**

    <div data-role="splitview">
        <div data-role="pane" data-initial="#bar">
    
          <div data-role="view" id="foo">
            Foo
          </div>
    
          <div data-role="view" id="bar">
            Bar
          </div>
        </div>
     </div>

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/pane](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/pane)

**15. PopOver**

      <a data-role="button" href="#foo" data-rel="popover">Open PopOver</a>
    
      <div id="foo" data-role="popover" data-pane='{ "initial": "#view2" }'>
        <div data-role="view" id="view1" data-title="view1">
          View 1
        </div>
        <div data-role="view" id="view2" data-title="view2">
          View 2
        </div>
      </div>
    </div>

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/popover](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/popover)

**16. Scroller dan ScrollView**

Scroller : 

    <div data-role="scroller" style="width: 200px; height: 200px" data-elastic="false">
        <div style="width: 500px; height: 500px">Content</div>
      </div>
    
ScrollView agak tricky. **Pay close attention to instructor guide !**

ScrollView : 

    <div data-role="view" data-stretch="true">
      <div data-role="scrollview"
        data-auto-bind="false"
        data-source="dataSource"
        data-template="scrollview-template"
        data-content-height="120px"
        data-enable-pager="false">
      </div>
    </div>
    
    <script id="scrollview-template" type="text/x-kendo-template">
      <div style="width: 110px; height: 110px; background-image: #=setBackground(ProductID)#;"></div>
      <p>#= ProductName #</p>
    </script>
    
    <script>
    
    
    var dataSource = new kendo.data.DataSource({
      type: "odata",
      transport: {
        read: {
          url: "http://demos.telerik.com/kendo-ui/service/Northwind.svc/Products"
        }
      },
      serverPaging: true,
      pageSize: 30
    });
    
    function setBackground(id) {
      return "url(http://demos.telerik.com/kendo-ui/content/web/foods/" + id +".jpg)";
    }
    </script>


Rujukan Scroller [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/scroller](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/scroller)

Rujukan ScrollView [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/scrollview](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/scrollview)
 
**17. SplitView**

    <div data-role="splitview" data-style="vertical">
      <div data-role="pane">
          <div data-role="view" id="foo">Pane 1 </div>
      </div>
      <div data-role="pane">
          <div data-role="view" id="foo">Pane 2 </div>
      </div>
     </div>

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/splitview](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/splitview)

**18. Switch**
    
    <input type="checkbox" data-role="switch" data-checked="false" />
    <input type="checkbox" data-role="switch" data-checked="true" />
    
Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/switch](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/switch)

**19. TabStrip**

    <div data-role="footer">
        <div data-role="tabstrip" data-selected-index="1">
          <a data-icon="contacts">foo</a>
          <a data-icon="contacts">bar</a>
          <a data-icon="info">baz</a>
        </div>
    </div>
    

Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/tabstrip](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/tabstrip)

**20. Touch**

    <ul id="list">
        <li class="touch">Foo</li>
        <li>Not selected</li>
        <li class="touch">Foo</li>
        <li>Not selected</li>
    </ul>
    
    <script>
    $("#list").kendoTouch({
        filter: ".touch",
        drag: function(e) {
            console.log("you dragged a list item");
        }
    });
    </script>
    
    
Rujukan [http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/touch](http://docs.telerik.com/kendo-ui/api/javascript/mobile/ui/touch)

Rujukan Touch Event yang lain : [http://docs.telerik.com/kendo-ui/mobile/touch](http://docs.telerik.com/kendo-ui/mobile/touch)

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