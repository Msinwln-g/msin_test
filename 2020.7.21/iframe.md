## iframe  注意
1：iframe是独立窗口，有window 对象
2；浏览器窗口也有window对象
3：窗口之间通信：按照同源策略 -----》启动页面的时候需要服务启动  live serve
4：浏览器窗口中页面为父页面   window为父window
  4.1：如何获取子window
   ~~~ js
   var childWindow = document.getElementsByTagetName('iframe')[0].contentWindow
   ~~~
   4.2  如何获取子window的 dom
   ~~~js
    var childDom = childWindow.document.xxx()//dom的api
    ~~~
    4.3：如何将父页面中数据传入子页面
    ~~~js
    var date = window.data //父页面的数据 
    childWindow.data = data//给子window添加全局属性，并 赋值父页面的数据data 
5：iframe加载的页面为子页面，该页面中的window对象为iframe中的window对象
  5.1：如何获取父window
  ~~~js
  var parentWindo = window.parent
  ~~~
  5.2：如何将子页面数据a传递给父页面
  ~~~js
  var data = window.a //获取子页面数据
  parentWindow.b = data //把子页面的数据传递给父页面变量b
  ~~~
6：注意
  - 1:每个window都都有location   localstorage  document....
  - 2:在子页面中 location.href重新加载的是子窗口页面，而不是父窗口的
  - 3：localstorage是所有窗口公用的数据
### 相邻的iframe是如何传递数据
 - 1，localstorage
 - 2，存到共同的父窗口  