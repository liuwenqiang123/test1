# 流行框架第一天：Angular简介和入门
## 前端流行技术的历史
- 之前时代，是桌面应用的天下，客户端服务器的天下，本没有前端这样的职位，网站设计师
- 石器时代，互联网开始发展网站设计师（静态）-不过是html、css、js、flash，页面设计师
- 青铜时代，yui、prototype、extjs、dojo等等框架的时代，美工、页面设计师 前端工程师
- 黑铁时代，jquery和jquery的一堆衍生品jqueryui、easyui、ligerui等 ui设计 前端工程师
- 白银时代，angularjs、react
- 黄金时代，现在前端技术和后端平起平坐的时代 跨平台开发


## 前端缘何一地鸡毛？
- 一地鸡毛，书名，刘震云的中篇小说，意思是说琐事特别多，并非贬义词。
- 说前端一地鸡毛，既是机遇又是挑战
- 这几年前端技术迅速发展，特别是在nodejs的基础之上发展，
- 分工协作前后端分离，给前端带来的机会

## 什么是库（包），什么是框架？
 - jQuery ：库
  + 封装了一些常用的方法，我们主动的调用这些方法
    -- 提高了代码的利用，以及代码后期的维护

 - Angular: 前端框架  react vue
  + 框架提供了一些结构或者模式，
  + 我们是根据框架提供的结构或者模式去书写代码
  + 由框架帮助我们去执行相应的操作。
 
## 什么是 Angular

- 一款非常优秀的前端高级 JS 框架
- 最早由 Misko Hevery 等人创建
- 2009 年被 Google 公式收购，用于其多款产品
- 目前有一个全职的开发团队继续开发和维护这个库
- 有了这一类框架就可以轻松构建 SPA 应用程序
- 单页面应用程序 模拟cs结构 客户端服务器 作出的bs的结构的网站，但是带有客户端的功能性、页面局部刷新特点

- 其核心就是通过指令扩展了 HTML，通过表达式绑定数据到 HTML。
- *Angular不推崇DOM操作，也就是说在NG中几乎找不到任何的DOM操作*

###
写一个输入框一个按钮
### 案例1
<body>
<input type="text" name="" id="num" value="">
<input type="button" name="" id="add" value="值+1">
<script>
      var add=document.getElementById("add");
      add.onclick=function(){
         var num=document.getElementById("num");
         //注意点需要-0，从字符串变成数字
         num.value=(num.value-0)+1;
      }
</script>
</body>
###案例2
<body ng-app> 
    <input type="text" ng-model="val" name="" value="">
    <input type="button" ng-click="val=(val-0)+1" name="" value="+1">
    <script src="node_modules/angular/angular.js"></script>
</script>
</body>
### 安装 Angular


- 暴力安装: 直接从本地硬盘中复制一个angular.js文件到项目中

- 通过工具安装
  + npm 方式 `npm install angular`  npm i angular  当前目录下的node_modules
 
  + bower 方式 'bower install angular'
- bower 
 安装 'npm install -g bower'

## CDN - 扩展内容
百度静态资源公共库 http://cdn.code.baidu.com/
content delivery network 
内容分发网络

*注意，每一种安装方式，本质都是为了拿到angular.js文件*

### 指令
内置指令   angular自带的
ng- 已ng-开头的标签里面的属性的扩展形式称之为指令
ng-app 告诉angular从这里开管理代码了
ng-controller 定义控制器范围
ng-model 绑定input输入框的值
ng-click 添加点击事件
ng-init 初始化一个对象的值

### Angular 表达式
{{}}表示一个表达式，像模板引擎
 <p>hello:{{user.name}}</p>
 <p>{{"hello:"+user.name}}</p>
 <p>{{1+1}}</p>
 <p>{{[1,2,3,4]}}</p>
 //注意不能写json或对象
<!--<p>{{{"a":"123"}}}</p>-->


## Angular 基础概念

### Angular 的核心特性

- 指令

- MVC

- 模块化  angular.module()

- 双向数据绑定

### 模块(module)
- angular.module('myApp',[])
  > 第一个参数是模块的名字
  > 第二个参数是一个数组，数组的元素是该模块所依赖其他模块的名字
*注意,即使不依赖任何模块，也需要给第二个参数传递一个空数组*
*否则angular.module('myApp')就是去获取名为myApp的模块对象*

### 控制器(controller)
- angular.module('myApp',[]).controller('demoController',function($scope){})
> 第一个参数，是控制器的名字
> 第二个参数，是一个回调函数，在回调函数里写我们想要的js代码。
###依赖注入
我需要什么，我就在参数上面去定义，要是调用我的方法就给我传
//angular
var controller =function(callback){
   setTimeout(function(){
    //写了一堆逻辑
      callback($scope);
   },2000)
}
//我们按照angular逻辑去写的代码
controller(function($scope){
   $scope
})
依赖注入的参数是不能修改的
### 双向数据绑定
- 数据模型的值发生改变，就会导致页面值的改变.
  页面值的改变，就会导致数据模型值的改变，这各种相互影响的关系就是双向数据绑定。
- ng-model

### 单向数据绑定
- 使用表达式显示数据模型的值。

### MVC 思想

#### 什么是 MVC 思想
- M:Model 模型  :数据存储，一些业务逻辑
- V:View  视图 ：就是用来展示数据
- C:Controller 控制器: 调度业务逻辑
### mvvm
- M:Model 模型  :数据存储，一些业务逻辑
- V:View  视图 ：就是用来展示数据
- vm:ViewModel $scope

### $watch
- 用于监视数据模型的变化（并且只能监视数据模型的变化）
- $scope.$watch('数据模型名的字符串形式',function(变化后的值,变化前的值){})
- $scope.$watch里的回调函数会默认执行一次。
- 速度快
- 减轻了服务器自身在带宽压力。

### 相关链接

- AngularJS 1.x 官方网站
  + https://angularjs.org/
- AngularJS 2.x 官方网站
  + https://angular.io/
- Google Material Design for Angular
  + https://material.angularjs.org
- Angular UI（Angular最大的第三方社区）
  + http://angular-ui.github.io/
- AngularJS中文社区
  + http://www.angularjs.cn/
- AngularJS中文社区提供的文档（不用翻墙）
  + http://docs.angularjs.cn/api
  + http://www.apjs.net/