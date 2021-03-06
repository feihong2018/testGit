## 一、后端开发

### 一、node基础

#### （一）、基本概念

##### 1、语言与环境平台之间的关系

​	1）语言，是编写代码的语法规范；程序员遵循特定的语法规范，编写出来的代码，只是单纯的文本字符串而已，并不具备可执行特点

​	2）环境（平台），提供了执行代码的能力，如果程序员编写的代码想要成功执行，必须要依赖于特定的执行环境；

​	eg：JavaScript代码可以被浏览器中的js解析引擎执行；

​	浏览器就是一个JavaScript的执行环境；

##### 2、前端和后端

​	1）前端主要工作

​		1）编写页面结构

​		2）美化页面样式

​		3）书写页面的业务逻辑

​		4）使用ajax调用后台接口

​	2）后端主要工作

​		1）操作数据库

​		2）对外暴露操作数据库的API接口

​	3）前后端协作开发

​		后端不负责页面渲染，只负责暴露接口；前端只负责调用接口，不管数据怎么来的。

##### 3、Node.js介绍是一个基于Chrome V8引擎的JavaScript运行环境。

​	Node.js是一个基于Chrome V8引擎的JavaScript运行环境。Node.js使用了事件驱动、非阻塞I/O的模型，轻量又高效。

​	Node.js的包管理器npm，是全球最大的开源库生态系统。

​	1、事件驱动：绑定事件，并生成任务队列

​	2、阻塞式I/O：当前事件执行完后，后面的事件才能执行（CPU利用效率不高）

​	3、非阻塞式I/O：可同时执行多个事件

​	4、Node.js：JavaScript的服务器端执行环境

​	5、Node.js中JavaScript的组成部分

​		ECMAScript + 全局成员 + 核心API模块，由于运行环境是后端，没有浏览器环境，所以Node.js剔除了BOM和DOM。

​		全局成员：console,setInterval,setTimeout.......

​		核心API模块：Node平台单独提供的一些API，安装Node的时候就在Windows下默认安装了Node的这些核心模块

##### 4、ECMAScript规范，浏览器中的js和Node中js的关系

​	1、ECMAScript规范（标准）：只是一个语言标准，规定语言特性，具体实现由使用该语言的环境平台实现。

​	2、浏览器中的js（语言）：浏览器中的js组成部分

​	3、Node中的js（语言）：Node中的js组成部分

​	4、学习Node.js可以做什么

​	5、Node.js可以做什么

- ​	像PHP一样，使用JavaScript编写符合规范的后端API接口或网站
- ​	使用Node.js开发一些实用工具或包
- ​	基于Socket技术，开发类似于聊天室之类的即时通讯项目
- ​	基于Electron环境，开发桌面软件（如vscode)
- ​	ETC。。。。


##### 5、环境安装

​	1、LTS：推荐企业中使用，长期稳定版本的安装包。

​	2、Current：当前最新版本，一些新特性可能存在问题。

​	3、打开当前目录下命令窗口：<font color='blue'> shift + 鼠标右键</font> (推荐使用方式)，点击在此处打开Powershell窗口；win + R 中输入cmd，但是只能进入C盘目录；点击左下角 窗口，在输入中输入cmd，进入的是C盘。

##### 6、Path环境变量

​	1、Path环境变量的作用：能够让我们在终端中执行相关的命令，从而快速启动应用程序；

​	如果执行node -v当前文件夹中没有此程序，会默认在全局环境变量Path中查找应用程序;

​	2、查看环境变量：右键点击此电脑，属性/高级系统设置/环境变量（N），双击系统变量下的Path，即可编辑环境变量。

​	3、下载软件时，系统会默认设置一个环境变量记录程序路径，并保存到Path中，如Node在D盘下，我在C盘中打开Powershell窗口，输入node -v 会默认先在C盘中查找应用，找不到后在Path中查找，如果还是找不到就会报错，在Path环境中添加程序所在文件夹的路径，就可以快速打开应用程序。

​	4、系统环境变量与用户环境变量的区别

​		1）用户环境变量：不同用户的变量都是独有的，其他人不能使用

​		2）系统环境变量：都是共享的（实际开发中建议路径都设置到系统变量中去）

​	5、利用Node环境执行js

​		在当前js文件目录下打开Powershell窗口，执行命令node ./demo.js

​		小技巧：

​			1）终端中使用上箭头，快速定位到之前命令

​			2）终端中Tab键可以快速补全路径（文件名01.myfirstNodeJs.js，我们只需要输入./01+Tab键就能自动补全后缀，如果错了，继续Tab键即可）

​			3）cls：Windows终端命令，清屏操作

​	6、REPL环境

​		R:read读取，当我们输入完代码后，敲击回车，Node就会读取用户输入的代码（字符串）

​		E:evaluate解析，表示将读取的代码，调用类似于Eval的函数，解析执行

​		P:print打印，将解析执行的结果输出给用户

​		Ctrl + C 按两次就可以退出REPL执行环境

​		真正项目中很少使用。

#### （二）、ECMAScript 6学习

##### 			一、基本语法介绍

##### 					1、之前定义变量，用var关键字，有如下缺点

​	1）存在变量提升问题，降低js代码的可阅读性

​	2） 没有块级作用域，容易造成变量污染

##### 					2、let主要特性

​	1）不存在变量提升问题

​	2）有{}块级作用域，必须先定义后使用

##### 		3、const特性

​	1）不存在变量提升 

​	2）无法被重新赋值

​	<font color='red'>3）定义常量必须有初始化的值</font>

​	4）定义复杂数据类型可以更改键值

​	5）能够声明块级作用域

```javascript
const d
//报错

const d = 3.1415
d = 20
//报错

for （let i = 0;i < 10;i++){
    const a = 'hello'
    console.log(a)
}

//复杂数据类型可以更改属性值
const person = {
	name: 'zs',
	age: 26
}
person.age = 28
console.log(person)		//{name:'zs',age:28}
```

##### 4、解构赋值	

```javascript
let user = {
    name: "zs",
    age: 28,
    gender: 'male'
}

let {name, age} = user //将对象属性从对象中解构成全局变量
console.log(name);	// zs
console.log(age);	// 28
console.log(gender); //报错,gender属性并没有解构

let {name:userName} = user  //将user中的name属性以userName名的形式放到全局中去

```

##### 5、箭头函数（常用）

​	1、箭头函数本质就是一个匿名函数

​	2、箭头函数内部的this与外部的this指向一致

​	3、写法： （形参1，形参2...）=> {函数体}

```javascript
btn.onclick = function () {
    setTimeout(function(){
        console.log(this); 	//this指向window
    },1000);
    setTimeout(() => {
        console.log(this);	//this指向btn
    },1000)   
}
```

​	4、箭头函数的变体

```javascript
//标准格式
var add = (x,y) => {return x + y;}

//变体1： 如果左侧的形参只有一个参数，小括号可以省略
var b = x => {return x;}

//变体2： 如果右侧只有一行代码，右侧花括号和return都可以省略，默认返回这一行代码
var c = (x, y) => x + y; 	//等价于return x + y;

//变体3： 如果左侧只有一个形参，右侧只要一行代码
var d = x => x + 20
console.log(d(3))	//23

```

​	5、对象中定义属性和方法的快捷方式

```JavaScript
//传统写法
let name = 'zs'
let age = 22
function show() {
    console.log('i am zs');
}
var per = {
    name: name,
    age: age,
    show: show
}

//es6写法：
var per = {
    name,	//相当于name: name
    age,
    show,
    say () { //相当于 say: function(){console.log('ok');}
        console.log('ok');
    }
}
```

##### 二、Node的API介绍

​	<b>1、</b>fs文件读取模块

​		访问核心成员，直接使用 require('核心成员名称')

​		fs.readFile()

```javascript
const fs = require('fs')
fs.readFile('./files/1.txt','utf-8',(err,data) => {
    console.log(err) 	//err为null的时候证明读取成功
    console.log(data)	//<Buffer 34 32 0d 0a 0d 0a b9 fe b9 fe 0d 0a>默认返回的是二进制形式编码，输出时以16进制buffer形式传给了data
})
//参数1： 读取文件路径
//参数2： 编码格式，默认为null，以二进制为默认编码，通常不写，最后数据传输还是二进制格式
//参数3： 读取成功后的回调函数
//函数第一个形参为error对象，第二个形参为获取的数据
```

​	<b>2、</b>文件写入

​		fs.writeFile('路径'，'写入数据'，'编码格式'，'执行操作')

```javascript
const fs = require('fs')
let data = 'hello world'
fs.writeFile('./1.txt',data,'utf-8',(err) => {
    if(err)return console.log('写入文件失败，信息：'+ err.message)
    console.log('文件写入成功！')
} )
//参数1：文件路径
//参数2：要写入的数据
//参数3：文件编码格式，默认为utf-8，通常不写
//参数4：回调函数，只有一个error形参，error为null时写入成功，否则为对象，显示错误的详细信息
//使用时，写入文件不存在，直接新建一个文件，如果文件已经存在，则直接覆盖原文件
```

​	<b>3、</b>文件追加

​		fs.appendFile(path,data[,options],callback)第三个参数可选

```javascript
let fs = require('fs');
let data = 'haha';
fs.appendFile('./1.txt','追加内容','utf-8',() => {})
//参数1：文件路径
//参数2：要写入的数据
//参数3：可选参数，规定文件编码格式，默认为utf-8，通常不写
//参数4：回调函数，只有一个error形参，error为null时追加成功，否则为对象，显示追加错误的详细信息
//如果追加文件不存在，会默认创建一个文件并追加内容
```

​	<b>4、</b>fs模块中路径操作问题

​		fs模块相对路径的问题：

```javascript
const fs = require('fs');
fs.readFile('./1.txt','utf-8',(err,data) => {
    if(err)return console.log('error:'+ err.meassage);
    console.log(data)
})
//查找时，Node会将相对路径直接拼接到Node命令所处的终端路径后
```

​		建议使用__dirname（执行时候代码文件所在目录）,windows中命令窗口\和/不作区别，但是\需要注意转义

​		__filename：指当前文件的完整路径，包含执行文件名和后缀

```JavaScript
let fs = require('fs');
let txt = '看看，写进来了';
fs.writeFile(__dirname + '\\2.txt','\n' + txt,(err) => {
    //注意使用\要转义,写为\\，用/2.txt就不需要转义
    if(err)return console.log('发生错误，错误信息：' + err.message);
    console.log('写入成功');
})
console.log(__dirname)
//PS C:\Users\Administrator\Desktop\nodeTask
console.log(__filename)
//PS C:\Users\Administrator\Desktop\nodeTask\mynode.js
```

​	<b>5、</b>读取文件信息

​		fs.stat(path,callback)，详细使用查看<a href='https://nodejs.org/en/'>Node.js</a>中文文档

​	<b>6、</b>路径操作模块path

```javascript
// 路径操作path.join([...paths])，会将路径片段链接起来
let path = require('path');
let result = path.join('c:/','a','b','c','d/e','../');
//../会上翻一级 打印结果:c:/a/b/c/d/
console.log(result)
```

​	<b>7、</b>path模块操作

```javascript
//注意：只要涉及到路径拼接，一定要使用path.join方法，不容易出错
let fs = require('fs')
let path = require('path')
fs.readFile(path.join(__dirname,'./files/1.txt'),'utf-8',(err,data) => {
    if (err) return console.log('错误信息：' + err.message);
    console.log(data);
})
```

​	<b>8、</b>路径操作其他方法

```javascript
let path = require('path');
const str = 'c:/a/demo.html';
console.log(path.basename(str));//demo.html获取文件名称
console.log(path.dirname(str));//c:/a/获取文件所在路径
console.log(path.extname(str));//.html获取文件扩展名
```

##### 三、node的模块化

​	<b>1、</b>JavaScript的单线程和异步

​		JavaScript的解析和执行一直是单线程的（解析引擎），但是**宿主环境（浏览器或node）**是多线程的；

​		异步任务是由宿主环境开启子线程完成，并通过**事件驱动、回调函数、队列**，把完成的任务交给主线程执行；

​		JavaScript解析引擎一直在做一个工作，就是**从任务队列里提取任务，放到主线程里执行**。

​	**2、**node为什么大量使用异步方法

​		需要使用异步处理的操作：耗时的操作（要把耗时的操作放到子线程中异步执行，保证解析引擎的效率）

​	**3、**认识模块化

​		模块化是一种约定，一定规范（比如USB接口都按照规范设计，方便用户使用）

​		模块化：**为了解决文件之间的依赖关系**，模块化是一种开发思想，大家都按照模块化规范书写代码，减少了不必要的沟通成本，极大方便了各个模块之间的调用。

​	**4、CommonJS规范**

​		1）作用：一套JavaScript的模块化规范，规定了模块的特性和各模块之间如何相互依赖。require导入模块（函数），通过exports暴露接口（对象），module（对象）获取想要的模块；

​		2）特点：同步加载模块的规范，必须模块加载完毕后才执行后面JS代码；不适合在浏览器（使用AMD/CMD规范）中使用，因为浏览器需要请求外部资源，而node只需要在本机执行可以方便加载模块；

​	**5、**模块作用域和全局作用域

​	1）全局作用域使用global来访问，类似于浏览器中的window；

​	2）程序员编写的每个JavaScript文件都是一个单独的一个作用域（一个模块），外界在require这个文件的时候，默认无法访问JS文件中的任何私有成员；

​	3）global与window的差别：node不会自动将文件中变量挂载到global上

```javascript
var b = 20;
console.log(global.b); //undefined
global.b = b;//这样才能挂载私有成员到global上
```

​	**6、**将私有变量通过global挂载使不同文件都可以使用该变量或属性方法，但企业开发中**不推荐使用**，因为存在环境污染问题。

```javascript
//demo.js 
let a = 333;
function say() {
    console.log('happy new year');
}
global.a = a;
global.say = say;

//work.js
let demo = require('./demo.js');
say(); //happy new year
console.log(a);//333
//可以这样共享，但是不推荐使用，污染全局环境
```

​	**7、**模块作用域

​		1）**module（模块标识）**：默认是一个空对象，require,exports是module的方法和属性

​		2）**require（引用模块）**

​		3）**exports（暴露模块成员）**

```JavaScript
//demo.js
var a = 10;
var b = 20;
exports.a = a;//暴露的成员会放入module中
function say() {
    console.log(b);
}
exports.say = say

//work.js
var module1 = require('./demo.js');//获取的是demo的module.exports对象
console.log(module1); //{a:10,say:[Function: say]}
console.log(module1.a); //打印10
module1.say(); //打印20
```

​		**module.exports与exports的关系**：默认引用同一个空对象，作用一致，都可以向外暴露成员，但是一个模块作用域，永远以 module.exports为主。

```javascript
//demo.js
let a = 10;
let b = 20;

exports = a;
module.exports = b;

//work.js
let module1 = require('./demo.js');
console.log(module1); 	//{b:20}
//开发中尽量使用module.exports向外暴露成员
```

​	**8、**AMD规范和CMD规范

​		1）AMD模块化规范代表：RequireJS

​			主要特性1：对于依赖的模块，AMD是提前执行

​			主要特性2：推崇依赖前置

​		2）CMD模块化规范代表：SeaJS

​			主要特性1：对于依赖的模块， CMD是提前延迟执行（as lazy as possible）

​			主要特性2：推崇依赖就近

​		3）ES6的模块化（**大趋势**）

​			es6是在语言标准层面上，实现了模块功能，而且实现得简单，完全可以取代

​		CommonJS和AMD规范，成为浏览器和服务器通用的模块解决方案。

​	**9、**Node.js中<font color='brown'>模块</font>和<font color='brown'>包</font>的概念

​		一）模块成员的分类，根据一些区别，可分为：核心模块（module，require等）、第三方模块（npm install的安装包）、用户自定义模块（程序员的代码）

​		1）核心模块：随着Node.js的安装包，一同安装到本地的模块

​			使用核心模块：require('模块')

​		2）第三方模块：由非官方提供的模块，叫做第三方模块

​			先从npm官网上下载指定的第三方模块，使用require('模块')，根据文档尝试使用。

​		3）用户自定义模块

​			如何使用用户自定义模块：require('路径名称')；

​		二）包的定义和使用 

​			一个具有特定功能的文件夹

​			规范的包结构：（加粗为必须遵守）

​			**1）**包都要以一个单独的目录而存在

​			**2）**package.json必须在包的顶层目录下

​			**3）** package.json文件必须符合JSON格式，并且必须包含如下三个属性：name（包的名字），version（包的版本号），main（表示包的入口文件 ）

​			4）二进制文件应该在bin目录下

​			5）JavaScript代码应该在lib目录下

​			6）文档应该在doc目录下

​			7）单元测试应该在test目录下

​			8）Node.js对包要求没有那么严格，只要顶层目录下有package.json，并符合基本规范即可。

​			9）建议：README.md：包的使用说明文档

​		三）自定义calc包

​		引入包的两种方式：用户模块与包在同一目录下，使用路径标识符（require('./path')）或者node_modules（只需要require('包名')就能引入包）;如果不在同一目录下，使用路径标识符使用包。

​		npm的两层含义：

​		1）npm英文网站：https://www.npmjs.com

​		2）npm：node package manager node包管理器

​		3）包的安装卸载

​		安装：npm install 包名 -g      包的位置(默认路径c:\用户\Administrator\AppData\Roaming\npm)

​		卸载：npm uninstall 包名 -g

​		**初始化**：**npm init -y**初始化，给包自动增加配置文件package.json,package-lock.json（记录项目中下载过得包和下载地址）

​		<font color='red'>注意：必须初始化才会自动生成package.json配置文件</font>

​		四）npm的常用命令

​		1）npm install jquery --save（5.xx及以上版本不需要--save，以下的必须有--save，-s与--save作用一样）

​		2）npm install webpack --save-dev（会将下载的包放到devDependencies节点下，表示开发阶段需要使用的包，产品上线不需要，--save下的包是上线也需要用到的包）

​		3）i是install的缩写，npm i jquery这样就可以下载包

​		4）快速安装依赖项(会根据package.json和package-lock.json中依赖下载所有项，开发中删除node_modules文件夹发给成员即可)，运行npm i 就可以下载所有依赖的包

​		5）--production只下载产品上线需要的包（不会下载devDenpendencies节点下的包，只下载dependencies下的包）：npm i --production

​		6）**解决npm下载慢的问题：**npm默认在下载的时候，连接的是国外的服务器，所以网速不好时，包可能下载不下来

​		解决办法：npm i cnpm -g下载cnpm，走中国服务器下载包，下载速度快

#### 四、构建web应用

##### 一、B/S交互模型

​	1）服务器：在网络节点中，专门对外提供资源服务的电脑

​	2）客户端：在网络节点中，专门用来消费服务的电脑

​	3）HTTP协议的通信模型

​		请求：客户端发起请求

​		处理：由服务器端处理请求

​		响应：服务器端把处理的结果，通过网络发送给客户端

​	4）静态资源：服务器端只需要读取并发送给客户端、不需要进一步处理的资源，叫做静态资源

​	5）动态资源：需要进一步处理才能发送给客户端的资源

##### 	二、实现一个静态资源服务器

​	1） 创建最基本的web服务器

​		创建服务器：使用const  server = http.createServer()

​		绑定监听事件：通过server.listen(端口，IP地址，回调函数)

```javascript
//1.导入http核心模块
const http = require('http');

//2.调用http.createServer()方法，创建一个web服务器对象
const sever = http.createServer();

//3.为server服务器绑定监听函数，通过on方法，绑定request事件，来监听客户端的请求
server.on('request',function(req,res){
    //req表示客户端相关的参数
    //res表示和服务器相关的参数和方法
    //解决node服务器返回的中文乱码
    //req.url表示请求的url，必须写响应头
    res.writeHeader(200,{'Content-Type':'text/plain;charset=utf-8'})
    //req.end结束请求时返回的资源
    //想要以h3标签显示，要将请求头改为text/html
    res.end('<h3>hello world<h3>');
})

//4.server.listen来启动服务器
//127.0.0.1默认打开端口，可以不写
//Ctrl + C 停止服务器
server.listen(3000,'127.0.0.1',function(){
    console.log('server is running at http://127.0.0.1:3000');
})

```

**res.end()**:接收两种数据格式string 二进制，尽量能使用二进制传递就用二进制传递(不推荐写utf-8，会将二进制格式转换为utf-8编码格式的字符串,数据走网络必然是以二进制格式传输的，多了一次不必要的转码)

​	2）优化服务器（HTML的中路径也会发送请求，服务器端也要写处理编码）

```javascript
//html文件里有css和js请求
<link href='./ccs/1.css'>
<script src='./js/1.js'></script>

//node.js代码
const http = require('http')
const server = http.createServer()
const path = require('path')
const fs = require('fs')
server.on('request',(req,res) => {
 let url = req.url
 if(url === '/' || url === '/index.html'){
     fs.readFile(path.join(__dirname,'/index.html'),(err,buffer) => {
         if(err) console.log('错误信息:'+ err.message)
         res.end(buffer);//给客户端传递二进制数据
     })
 }else if (url === '/css/1.css'){
      fs.readFile(path.join(__dirname,'/css/1.css'),(err,buffer) => {
         if(err) console.log('错误信息:'+ err.message)
         res.end(buffer);
     })
 }else if (url === '/js/1.js'){
      fs.readFile(path.join(__dirname,'/js/1.js'),(err,buffer) => {
         if(err) console.log('错误信息:'+ err.message)
         res.end(buffer);
     })
 }
})
```

```JavaScript
//优化服务器代码
//html文件里有css和js请求
<link href='./ccs/1.css'>
<script src='./js/1.js'></script>

//node.js代码
const http = require('http')
const server = http.createServer()
const path = require('path')
const fs = require('fs')
server.on('request',(req,res) => {
 let url = req.url
 if(url === '/') url = '/source/inde.html'
    fs.readFile(path.join(__dirname,url),(err,buffer) => {
        if(err) res.end(err.message)
        res.end(buffer)
    })
 }）
     
```

##### 三、express框架

​	**1、**下载nodemon:node i nodemon -g 下载全局包

​	**2、**使用nodemon + 路径执行文件，Crrl + S 后会自动重启服务器，刷新页面就能看到更改的后的执行结果

​	**3、**express框架

​		1）npm i express -S安装框架

​		2）创建基本的express服务器

​			导入express第三方模块

```javascript
const express = require('express')

//创建服务器实例
const app = express()

//通过app.post(),app.get()方法监听客户端的get或post请求
app.get('请求地址',(req,res) => {
    //处理代码
})

//启动express服务器
app.listen(端口，IP地址，启动成功后的回调函数)

//express的快捷方法
//res.end()不支持中文,必须写请求头，使用express封装的res.send()方法不用
//res.send()发送字符串直接显示，发送对象会转换为JSON格式，发送数组也会转换为JSON格式字符串，发送二进制res.send(new Buffer(data))
res.send({
    name: '张三',
    age: 18
})

//res.sendFile()向客户端发送文件
//1.如果只给定一个参数，必须是绝对路径，表示发送给客户端文件的绝对路径
//2.第一个参数为相对路径，第二个参数必须为绝对路径
res.sendFile(path.join(__dirname,'/source/index.html'))
res.sendFile('./source/index.html',{root: __dirname})

```

​		3）使用express.static()快速托管静态资源

```javascript
const express = require('express')
const app = express()
//app.use()作用就是托管中间件
//express.static()方法，可以把指定目录托管为静态资源目录
//第一种使用：直接托管
app.use(express.static('./source'))
//第二种使用：虚拟路径托管,访问http://127.0.0.1:3000/source/index.html
app.use('/source',express.static('./source'))
//托管后html文件直接使用link rel="stylesheet" href="/source/css/1.css"
```

​		4）为express框架配置模板引擎渲染动态页面

​			安装ejs模板引擎npm i ejs -S

```javascript
// 使用ejs模板引擎渲染页面
const express = require('express')
const app = express()

//设置引入的模板引擎,除了ejs还有Pug
app.set('view engine', 'ejs')
// 设置存放模板格式对应文件的路径，默认到./source文件夹下找指定后缀文件（index.ejs）
app.set('views','./source')

app.get('/', (req, res) => {
    // 注意：调用前要配置模板引擎
    res.render('index.ejs',{
        name: 'chen',
        age: 18,
        hobby: ['sing','dance','cooking']
    })
    //渲染看ejs模板
})

app.listen(3000, () => {
    console.log('server running at http://127.0.0.1:3000')
})
```

​		5）express中配置art-template

​			1.安装两个包  npm i art-template express-art-template -S

​			2.自定义一个模板引擎  app.engine('自定义模板引擎名称',渲染函数)

​			//<font color='red'>注意：模板引擎名称与指定目录下文件后缀名是一样的</font>

​			3.app.set('view engine','具体模板引擎的名称')

​			4.配置模板页面的存放路径 app.set('views','路径')

​		6）封装路由模块

```javascript
//server.js
const express = require('express')
const app = express()
//导入路由模块
const router = require('./router.js')
//注册中间件
app.use(router)

app.listen(3000,() => {
    console.log('server running at http://127.0.0.1:3000')
})

//router.js
const express = require('express')
const router = express.Router()

router.get('/',(req,res) => {
    res.send({status: 200,msg: 'ok',data: null})
})
```

​		7）循环注册路由文件夹下所有路由模块

```javascript
const express = require('express')
const app = express()
const fs = require('fs')
const path = require('path')
fs.readdir(path.join(__dirname,'/router'),(err,filenames) => {
    if(err) return console.log('读取失败')
    filenames.forEach(fname => {
        const router = require('./router' + fname)
        app.use(router)
    })
})
```

​	**4、**express中间件

​		1）中间件：本质上就是一个处理函数，包含三个参数:

​			req:请求对象；

​			res:响应对象；

​			next:next()，表示调用下一个中间件的方法

​			具体：实际开发中多个模块对数据进行共享并一起操作数据，每个模块的功能更改都会影响到数据上

​		2）express框架中对中间件的分类

​			应用级别中间件：app.use(),app.get(),app.post()

​			路由级别中间件：路由对象下的方法，如router.get(),router.post()就是路由级别中间件

​			错误处理级别中间件：app.use(err,req,res,next)

​			内置中间件：唯一内置中间件，express.static()

​			第三方中间件：非express框架提供的，需要自己安装的，比如body-parser

##### 四、数据库MySql的操作

​	**1、**	下载phpStudy软件后的配置

​	1)	停止/其他选项菜单/服务器管理器/开启MySQL

​	2） 下载navicat premium

​	3） 新建连接，在Mysql/my.ini中[mysqld]下面添加skip_grant_tables保存后关闭可以跳过密码登陆

​	4） 重启mysql

​	5） 双击新建连接，右键新建数据库	

​	**2、**使用node.js操作数据库

​	1）安装mysql模块： npm i mysql

​	2）具体代码

```javascript
const express = require('express')
const app = express()

// 导入MySQL模块
const mysql = require('mysql')

// 创建连接对象,以下是默认配置
const connect = mysql.createConnection({
    host: 'localhost',
    user: 'root',
    password: 'root',
    database: 'mysql01'
})

// connect.query('要执行的sql语句',(err,res) => {})
//以下是查询语句，获取表格users中的所有数据
const sqlStr = 'select * from users'
connect.query(sqlStr,(err,res) => {
    if(err) console.log('查询失败')
    console.log(res)
})

// 监听端口
app.listen(3000,(req,res) => {
    console.log('server running at http:127.0.0.1:3000')
})
```

​	3）MySQL的查询语句

```javascript
//查询语句
const userName = req.seession.user.username
const sql = 'select * from users where username=?'
connect.query(sql,userName,(err,result) => {
    if(err) return res.send({status: 500,msg: 'query failed'})
    res.render('index.ejs',{
        user: req.session.user,
        islogin: req.session.islogin 
    })
})

//增加数据
const users = {id: 1,username: '新宇',age: 10,gender: '男'}
//问号？表示占位符，是node的用法
const sqlStr = 'insert into users set ?'
connect.query(sqlStr,users,(err,result) => {
    if(err) console.log('插入失败')
    console.log(result)
})

//改变数据
const user2 = {id: 2,username:'小黄',gender: '男'}
const sqlStr2 = 'update users set ? where id=?'
connect.query(sqlStr2,[user2,user2.id],(err,res) => {
    if(err) console.log('改变失败：' + err.message)
    console.log(res)
})

//删除数据
const sqlStr3 = 'delete from users where id=?'
connect.query(sqlStr3,2,(err,res) => {
    if(err) console.log('删除失败：' + err.message)
    console.log(res)
})


```

​	**3、**模块加载机制

​	1）当一个模块初次被require的时候，会执行模块中的代码，当第二次加载模块的时候会优先从缓存中查找

```javascript
//1.js
console.log('hello world')

//2.js
require('./1.js') //只打印一次
require('./1.js')
require('./1.js')
```

​	2）后缀名

```
require('./index')
//项目中有index,index.json,index.js,inde.node文件
//查找顺序：index,index.js,idnex.json,index.node

```

​	**4、**第三方模块加载机制

​	1） 现在node_modules文件夹查找，模块相关的文件夹

​	2） 查找package.json

​	3） 查找main属性，路径存在尝试加载，main或package.json都不存在，会尝试加载与查询名字相同的文件

​	4） 依旧没找到指定文件会上翻一个文件夹，如果到了根盘目录依旧没有，报错：cannot fidn module ***

​	**5、**获取参数

```javascript
const express = require('express')
const app = express()
//第一种查询方式：查询url携带参数
//url-->http://127.0.0.1:3000/users?name=zs&age=18
app.get('./users?name=zs&age=18',(req,res) => {
    console.log(req.query())
    //使用req.query.name就可以获取name属性
    res.send('ok')
})
//{name:'zs',age: 18}

//第二种查询方式：查询路径中参数
//url规则中的:表示参数项
//url-->http://127.0.0.1:3000/users/zs/22
app.get('./users/:name/:age',(req,res) => {
    console.log(req.params())
    //使用req.params.name就能获取到属性值
    res.send('ok')
})
//{name: 'ls',age: 18}

app.listen(3000,() => {
    console.log('server running at http://127.0.0.1:3000')
})

//第三种查询方式：查询post的参数
//安装npm i body-parser -S
const bodyParser = require('body-parser')
// 注册body-parser中间件
app.use(bodyParser.urlencoded({extended: false}))

// 监听post事件
app.post('/user',(req,res) => {
    console.log(req.body)
    res.send('你好')
})

app.listen(3000,() => {
    console.log('server running at http://127.0.0.1:3000')
})

```

​	**5、**web开发模式

​	1）混合模式（传统开发模式）

​		后端干所有的活，后端页面.php,.jsp,.aspx,.cshtml

​	2）前后端分离（趋势）

​		后端负责操作数据库，给前端暴露接口，前端负责调用接口和渲染数据

​	**6、**CORS与JSONP区别

​	1）JSONP的原理：动态创建script标签；JSONP发送的不是AJAX请求，不支持Post请求，发送的是Get请求

​	2）CORS发送的是真正的AJAX请求，CORS支持AJAX跨域，CORS跨域资源共享，关键在于服务器端CORS资源共享，就像发送普通Ajax请求一样，没有任何代码上的变化

​	3）对于Node来说，如果向开启CORS跨域资源共享只需要安装CORS模块就可以

​	安装：npm i cors -S

```javascript
const express = require('express')
const app = express()
//导入cors包
const cors = require('cors')
//使用cors中间件
app.use(cors)
```

​	**7、**数据库设计

| 字段名 | 字段类型 | 字段描述       |
| ------ | -------- | -------------- |
| id     | int      | 主键id（自增） |
| name   | varchar  | 英雄名称       |
| gender | varchar  | 性别           |
| ctime  | int      | 创建时间       |
| isdel  | tinyint  | 是否被删除     |

​	**8、**数据库注意事项

```javascript
// node博客项目注册新用户遇到问题
//1、connect.query()是一个异步执行函数，所以每个判断必须是在回调中进行的
//2、数据库返回的result是一个数组:[ RowDataPacket { count: 0 } ]，所以要用result[index].attr
router.post('/register', (req, res) => {
    // 获取用户提交表单数据
    const userInfo = req.body
    // 查询昵称是否重复
    const sql2 = 'select count(*) as count from blog where nickname=?'
    connect.query(sql2, userInfo.nickname, (err, result) => {
        if (err) return res.send({ status: 502, msg: err.message, data: null })
        if (result[0].count !== 0) return res.send({ status: 502, msg: '昵称已存在', data: null })
        // 查询用户名是否重复
        const sql1 = 'select count(*) as count from blog where username=?'
        connect.query(sql1, userInfo.username, (err, result) => {
            if (err) return res.send({ status: 502, msg: err.message, data: null })
            if (result.count !== 0) return res.send({ status: 502, msg: '用户名已存在', data: null })
            // 新建用户账号
            const sql3 = 'insert into blog set ?'
            userInfo.ctime = moment().format('YYYY-MM-DD HH:mm:ss')
            connect.query(sql3, userInfo, (err, result) => {
                if (err) return res.send({ status: 500, msg: '注册用户失败', data: null })
                res.send({ status: 200, msg: '创建成功', data: null })
            })
        })
    })
})
```

​	**9、**通过循环形式注册路由

```javascript
//router1.js
const express = require('express')
//router1也可以是函数，其他类型不可以
const router1 = express.Router()

module.exports = router1

//加入task文件夹下有server.js，router文件夹（router1.js...routerN.js）
const express = require('express')
const fs = require('fs')
const path = require('path')
const app = express()

//fs.readdir(要读取路径的文件夹,(错误,当前文件夹下所有文件名组成的数组)=>{})
fs.readdir(path.join(__dirname,'./router'),(err,filenames) => {
    filenames.forEach(filename => {
        //const会声明块级作用域，会把所有模块导入进来
        const router = require(path.join(__dirname,'/router',filename))
        //注意：注册中间件必须是函数
        app.use(router)
    })
})
app.listen(3000,() => {
    console.log('server running at http://127.0.0.1:3000')
})
```



##### 五、MVC三层架构

​	**1、**MVC ：就是**分层**开发的思想；把复杂的业务处理，分为职能单一的小模块；各个模块之间看似相互独立，其实又有依赖关系；好处：保证了模块职能的单一性，方便项目的维护、开发和拓展。

​	M：M表示Model，是数据操作层（db.js）

​	V：V表示View，是视图层（前端展示页面）

​	<font color='red'>C：</font>C表示Controller，是业务处理层，或业务逻辑层（server.js,router.js,controller.js），最重要的一层

​	**2、**服务器端状态保存技术

​	1）cookie技术

​		cookie就是存储在客户端的一小段文本

​		是一门客户端技术，存储在客户端浏览器中

​		目的：实现客户端与服务器端之间的状态保持

​		cookie技术不安全，容易篡改，不要使用cookie保存敏感信息

​		客户端会在每次请求时会检查cookie并将合法的cookie携带送给后端

​		cookie默认关闭浏览器失效，所以要给cookie设置过期时间（expires）

```javascript
//使用cookie技术实现一个小需求
const http = require('http')

const server = http.createServer()

server.on('request',(req,res) => {
    //获取到cookie文本（字符串）
    const cookie = req.headers.cookie
    //创建一个对象保存cookie信息
    const cookieObj = {}
    //cookie存在就对cookie进行操作
    cookie && cookie.split(';').forEach(item => {
        const partial = item.split('=')
        cookieObj[partial[0]] = partial[1]
    })
    // console.log(cookieObj)
    //cookie存在返回欢迎再次登录文本
    if(cookieObj.isvisit == 'yes'){
        res.writeHeader(200,{
            'Content-Type': 'text/plain;charset=utf-8',
            // 'Set-Cookie': ['isvisit=yes','test=ok']
     })
        res.end('欢迎再次登录')
    }else{
        //cookie不存在返回奖励
        //设置
        const expiresTime = new Date(Date.now() + 10*1000).toUTCString()
        res.writeHeader(200,{
            'Content-Type': 'text/plain;charset=utf-8',
            'Set-Cookie': ['isvisit=yes;expires='+expiresTime,'test=ok']
     })
        res.end('第一次登陆，奖励一朵小红花')
    }
})

server.listen(5000,() => {
    console.log('server running at http://127.0.0.1:5000')
})
```

​	2）保存用户登录状态

​	node中使用express-session用来保存登录状态

![](C:\Users\Administrator\Desktop\关于session的图示.png)

​	3）配置session

​		1）安装：npm i express-session -S

​		2）引入模块：const session = require('session')

​		3）配置session

```javascript
//只要注册了session中间件，今后访问req这个对象，必然能访问到req.session
const session = requrie('express-session')
app.use(session({
    //这里尽量不要用中文，使用英文的随机字符串
    secret: '这是加密的密钥',
    resave: false,
    saveUninitialized: false
}))
```

​		4）博客项目注销逻辑

```javascript
// 注销用户逻辑
const withdraw = (req,res) => {
    //会释放session的内存空间
    req.session.destroy(() => {
        //重定向
        res.redirect('/')
    })
}
```

​		5）ejs语法

```html
//'='表示以文本转义形式输出（字符串），'-'以未转义形式输出
//导入公共的文件(通常放入一个layout文件夹)
<%- include('../layout/header.ejs') %>

<h1>文章添加页面</h1>

<%- include('../layout/footer.ejs') %>
```

​		6）使用mditor插件，导入文本编辑器

​		1）安装 ： npm i mditor -S

​		2）导入

```html
<link rel="stylesheet" href="/node_modules/mditor/dist/css/mditor.min.css">
<script src="/node_modules/mditor/dist/js/mditor.min.js"></script>
//设置id为editor
<textarea id="editor"></textarea>
<script>
    //初始化编辑器的值
  var mditor = Mditor.fromTextarea(document.getElementById('editor'));

  //获取或设置编辑器的值
  mditor.on('ready', function () {
    // mditor.value = '** hello **';
  });
</script>
```

​		3）npm i marked -S：安装marked中间件，将文本以markdown文本格式输出

```javascript
const moment = require('moment')
const con = require('./db.js')
const show = (req,res) => {
    const id = req.session.user.id
    const sql = 'select * from users wehre id=?'
    con.query(sql,id,(err,result) => {
        if(err) return res.send({status: 500,msg: '查询异常'})
        if(result.lenght !== 1) return res.send({status: 500,msg: '查询失败'})
        //将存入的markdown文本以markdown语法格式输出，否则就是以字符串形式输出
        result[0].text = marked(result[0].txt)
        res.render('index.ejs',{
            
        })
    })
}
```

**3、**node博客项目发表文章

​	1）设计文章表的字段

| 名       | 类型                          | 长度 | 小数点 | 不是null |
| -------- | ----------------------------- | ---- | ------ | -------- |
| id       | int                           |      |        |          |
| title    | varchar                       |      |        |          |
| content  | <font color='red'>text</font> |      |        |          |
| ctime    | varchar                       |      |        |          |
| authorid | int                           |      |        |          |

​	2）注意session默认过期时间是30分钟

​	**4、**使用bcrypt加密，2015前使用md5加密（但是可以通过暴力破解）

​	1）安装模块加密模块：npm i node-pre-gyp -g

​	2）在项目终端中导入加密模块：cnpm install bcrypt -S

​	3）导入bcrypt：const bcrypt = require('bcrypt')

​	4）定义幂次：const saltRounds = 10

​	5）调用bcrypt.hash()加密：

```javascript
bcrypt.hash('123',saltRounds,(err,pwdCryped) => {
	console.log(pwdCryped)
})
```

​	6）登录时使用bcrypt.compare(password,result.password,(err,compareRes))

```javascript
const bcrypt = require('bcrypt')
//在query数据库后比对，使用bcrypt方法验证登录密码
bcrypt.compare(password,result.password,(err,compareRes) => {
    //如果compareRes为true时表示密码与登录密码一致
    if(!compareRes) return res.send({status: 500,msg: '请检查登录密码'})
    do something...
})
```

##### 六、Node实现图片上传功能

​	1、流程：

​		（1）搭建静态服务器

​		（2）客户端通过post提交图片到服务器

​		（3）服务器接收客户端提交的图片

​		（4）将图片路径和地址发送到客户端

​		（5）客户端接收渲染图片		

​	2、搭建静态服务器

node代码：

```js
//1.安装express,安装模板引擎
npm i express -S
npm i ejs -S
mpm i jquery -S
npm i formidable -S

//2.基于服务器渲染index.html
const express = require('express')
const app = express()

//使用formidable对上传的图片进行处理
//根据npmjs官网介绍进行操作
const formidable = require('formidable')
app.engine('html',require('ejs'))
app.set('view engine','html')
app.set('views','art_views')

//2.托管静态资源
app.use(express.static('./art_views'))
app.use(express.static('./node_modules'))
app.use(express.static('/upload','/upload/imgs'))

//3.监听端口，启动服务器
app.listen(3000, () => {
    console.log('server running at http:127.0.0.1:3000')
})

app.get('/',(req,res) => {
    res.render('idnex.html')
})

var form = new formidable.InComingForm();
//编码格式
form.encoding = 'utf-8';
//上传的文件目录
form.uploadDir = '/upload/imgs';
//保持文件后缀名
form.keepExtensions = true;
app.post('/upload',(req,res) => {
    //将获取客户端上传的图片进行解析
    form.parse(req, (err,fields,files) => {
        res.send(files.File.path)
    })
})

```

index.html代码：

```html
<script>
    $(function () {
        var formdata = new FormData();
//将添加的图片信息添加到Formate对象上，并添加到data属性上 
formdata.append('file',$('#file').files[0])
        $('#btn').on('click',function () {
            $.ajax({
                url: '127.0.0.1:300/upload',
                type: 'post',
                data: formdata,
   //告诉jQuery不要序列化data数据，默认为true
                processData: false,
   //告诉jQuery不要更改content-type
                contentType: false,
                success: function (data) {
					 $('.avatar').attr('src',data)
            }
            })
        //阻止默认提交事件
        return false;
        })
    })
</script>
```

