
# 一、计算机的定义

# 二、计算机基本特点

# 三、计算机组成

# 四、计算机硬件系统

输入设备+输出设备+计算器+控制器+存储器

计算器和控制器统称为中央处理器（cpu）

存储器包括内存和外存，内存主要是内存条，外存主要是移动硬盘，内存分为只读内存（ROM）和随机内存（RAM）。



# 五、计算机软件系统

1、软件系统分为：系统软件（操作系统）+应用软件

2、常见的操作系统软件

​	i. 图形化桌面操作系统：windows、MacOS

​	ii. 移动设备操作系统：android、ios

​	iii. 服务器操作系统：Linux、windows server

3、应用软件：安装在操作系统上的第三方功能软件。eg:qq,wechat

# 六、进制基本介绍

1、二进制就是一种数学进制，只包含0和1两个基数（计算机底层用到二进制）

2、1代表高电位，0代表低电位。

3、常见数学进制：二进制（0-1）、八进制（0-7）、十进制（0-9）、十六进制（0-9、ABCDEF）。

# 七、编码与数据计量单位

编码：将人类可以理解自然语言翻译为计算机可理解的机器语言。

ascii码

常见的处理中文编码：UFT-8

计算机数据计量单位：

比特（bit 位），字节（bytes），一个字节等于8位。

常用单位及换算关系

1B（字节）=8b（位）

1KB=1024B

1MB=1024KB

1GB=1024MB

1TB=1024GB

1PB=1024TB

# 八、web网站与HTML

## 1、相关名词

web指的是www:万维网

web是一种基于https协议

网站：若干个网页组合而成的集合。

网页就是通过浏览器展示包含图片、文字、链接、声音...等内容的一种html文件

网页在浏览器上进行解析和展示。

## 2、html基本介绍

前端由三大部分组成：html负责结构，css负责样式，js负责行为（浏览器与用户间的交互）

ide：编译器。

DOCTYPE html 指的是html5的版本  

html是根标签，head是头部，<meta charset=utf-8 是国际编码，能让中文正常显示。

title是网页的标题，显示在浏览器的标签页上

body是网页主体内容。

1、基本标签

html标签分为：单标签，双标签

加转义符\即可写html标签

换行：\<br />

空格：\&nbsp;  使用utf-8编码，3个\&nbsp;相当于一个汉字。

标题标签：<h1></h1> h1-h6

段落标签：<p></p>

标签语义化：在合适的地方使用合适的标签，就算符合标签的语义化。符合语义化的网站可以在搜索引擎中排名更靠前。

弱语义：

\<b>加粗</b> 只代表加粗

\<s>删除线</s>

\<i>倾斜</i>

强语义：

\<strong>加粗</strong>  除了代表加粗，还是强调

\<del>删除线</del>

\<em>倾斜</em>

常用布局标签：

\<div>会独占一行</div>

\<span>可以和其它span在同一行</span>

注释：ctrl+？添加和取消注释都是这个快捷方式。

项目上线之前，代码里有注释内容，注意要删除，用户看不到，只会减慢网速。

2、图片标签

src代表资源，属性名=“属性值” 这种书写方式叫键值对语法也叫key value 对，用来引入图片位置，这个属性值也称为路径。

width表示宽度，height表示高度。若宽度和高度只设置了一个，则另外一个属性会按照原图的比例缩放。

title作用是鼠标悬停到图片时的提示文字 ，定义图片的标题。

alt属性定义图片的提示文字，当图片无法正常加载的时候才会显示出来  写的文字一般来说是对图片的描述信息

\<img src="01.jpeg"  width=""  height="" title="小孩"/> 

3、路径

在前端中不推荐使用绝对路径的方式，因为代码没有可移植性。

绝对路径：在计算机中的完整路径

相对路径：相对于当前文件

路径：

同级路径：html文件与被查找的图片放在同一级目录下，二者是“兄弟”关系，此时只需在src中写入图片名称即可。

\<img src="01.jpg"/>

下级路径：html文件与图片不在同级目录，此时要查找的图片被放在了html文件的下级目录中，此时需要通过/来向下查找。

\<img src="img/1.jpg"/>

上级路径：仍以html文件为起点，此时图片被存放在了html文件上级目录，需要使用../来向上进行回退查找。

\<img src="../1.jpg"/>

4、超链接

跳转到线上网站，需要添加http:// 超文本传输协议，才可以正常跳转

\<a href="http://www.baidu.com">跳转到百度</a>

跳转到本地文件，直接写文件即可。

\<a href="01.html">打开本地文件</a>

新窗口打开，加属性target="_blank"

\<a href="01.html" target="_blank">点击可以新窗口打开</a>

有些情况下，无法确定链接的跳转，可以写空链接语法，注意一个#号的空链接，会让页面一瞬间返回顶部。

\<a href="##">空链接</a>
\<a href="javascript:;">空链接</a>
\<a href="javascript:void(0);">空链接</a>

5、表单

form标签就是作为表单数据的根标签。

前端把用户信息收集好之后，点击确定，发送给后端进行数据的保存。action属性的值就是把所有的表单内容，传给某个后台程序来解决。method代表传输数据时候的方法：get会显示在URL地址的后面，post会在http协议的请求体中。

\<form action="" method="post"></form>

type="text"，代表普通的输入框，type="password"代表密码框；placeholder属性可以设置用户的提醒文字

<input type="text" placeholder="请输入用户名"/>

**单选框**：type="radio" ；关注点击时是否实现单选效果，需要保持name一致，证明是一组；点击文字也可以实现切换效果，会提升用户体验，需要在input框中加入id属性，点文字能够切换，需要加label标签，添加for属性与联动的input的id需要一致。默认选中，checked="checked"

<input type="radio" name="sex" id="nan" checked="checked"/> <label for="nan" >男</label> 
			 <input type="radio" name="sex" id="nv" /><label for="nv">女</label>

**复选框（多选框）**：可以全部选，也可以只选一个；为了提升用户体验也要和单选框一样，点击提示文字，也可以选上。默认选中，checked="checked"。

爱好：<input type="checkbox" id="basketball" checked="checked"/> <label for="basketball">篮球</label>
			  <input type="checkbox" id="football"/><label for="football">足球 </label>

下拉框：注意默认选项是否符合要求；总共的下拉可选数也要符合要求。默认被选中，selected="selected"

<select name="">
			  	<option value="">北京</option>
				<option value="">上海</option>
				<option value="" selected="selected">广州</option>
				<option value="">深圳</option>
			  </select>

文本域：cols和rows分别代表列和行，程序员一般不适用这个属性，因为有兼容性问题，使用css来解决；右下角按钮要关闭，不允许用户自行改变大小，需要在表头加入css：

<style type="text/css">
			textarea{resize: none;}
		</style>

<textarea placeholder="请填写您的意见" cols="" rows=""></textarea>

按钮：普通按钮、重置按钮、提交按钮

普通按钮：type="button"；重置按钮：type="reset"，value属性也要设置，若不设置，浏览器会自己写入一个默认值。此按钮的效果是点击后重置页面中的表单数据，而非清空；提交按钮，type=submit;

6、列表

无序标签：ul li   有序标签：ol li

<ul>
			<li>111</li>
			<li>222</li>
		</ul>
```html
  <ol>
		<li>111</li>
		<li>222</li>
	</ol>
```
## 3、css

style写在head里边，type=“text/css”，此代码可有可无；div{}表示对div里的内容进行修改，color文字颜色，font-size字体大小，px代表像素，计算机中的计量单位。

<style type="text/css">
			div{color: maroon; font-size:30px;}
</style>

**css选择器**：简单选择器，复合选择器。

简单选择器：标签名选择器，类名选择器，id名选择器

<style type="text/css">
			/* div{color: maroon; font-size:20px;}
			p{color: aqua;}
			h2{color: blue;} */
			/* #p1{color: red;}
			#p2{color: green;}
			#p3{color: blue;} */
			.pname1{
				color: red;
			}
</style>

		<p id="p1" class="pname1">段落1</p>
		<p id="p2" class="pname1">段落2</p>
		<p id="p3" class="pname1">段落3</p>
		<div class="pname1">
			使用css改变样式1
		</div>
标签名选择器：通过标签名称来选中元素；

<style type="text/css">
			div{color: maroon; font-size:20px;}
			p{color: aqua;}
			h2{color: blue;}
</style>

类名选择器(class)：通过标签的类名来选中元素；累选择器使用.类名；类名可以重复使用；同一个标签可以设置多个类名，使用空格分割即可，id选择器只允许每个标签有一个id名。class不允许数字开头命名；class不允许使用符号，除了下划线_和中划线-可以使用；class不推荐使用中文；名字最好见名知意。

.pname1{color: red;}

id名选择器：通过标签的id名来选中元素；#id的属性值，叫做id选择器。id的值一定不能重复；id命名数字不能开头；id不推荐使用中文；id不允许使用符号，除了下划线_和中划线-可以使用；名字最好见名知意。

#p1{color: red;}

**css特性**：继承性、覆盖性

继承性：只要给祖先标签设置的css文字属性，都可以继承给后代。比如div里有span标签，修改div颜色，span颜色也修改。

覆盖性：权重相同的时候，先写的样式会被后写的覆盖。

**复合选择器**：后代选择器，并列选择器

**后代选择器**，使用空格来实现；后代指的是儿子、孙子等。div下所有span标签。

同一个标签设置id和class不会有冲突，哪怕id和class的值一样也不会有问题。

可以使用标签、类名、id

<style type="text/css"> div span{color:red;} .bz span{color: red;} #div1 span{color: red;} </style>

<div class="bz" id="div1">
			<p>
				<span>span内容</span>
			</p>
</div>

**并列（并集）选择器**：用逗号分隔；可以使用任意一种普通选择器来进行书写。

div与p是同一级：

div,p{color: red;}

#div1,#div2,.p1{color: red;}

**基础选择器权重**：针对同一个标签设置css才有权重：id>class>标签；继承的权重最低

复合选择器权重：针对同一个标签设置css属性，最终计算权重最大的才会生效。

css文件存放位置：内嵌css、外链式css、行内css

**内嵌css**：css与html写在同一文件中，位于head中，style。

**外链式css**：link将css文件引入到html的方法。

需要重新写一个css文件，并在head中引入到当前html文件中。<link rel="stylesheet" type="text/css" href="css.css">

**行内css**：写在标签内部

<div style="color: red; font-size: 12px;">哈哈哈</div>

总结：

内嵌式css不用加载外部的css文件，网页的加载速度就更快一些，电商网站的首页对于网站的打开速度有更高的要求。

对比内嵌式，外链式可以实现css代码和html代码的分离效果，方便代码的修改。除了电商网站的首页外，都使用外链式即可。

行内式css一定不要写，因为修改十分不方便，还会导致页面混乱，加载速度会变慢。

外链link和内嵌css权重一样，先写的被后写的覆盖。都比行内样式的权重低。

css盒子模型：

内容，内容与边框之间的距离为内边距padding，边框线为属性border，边框与边框（两个盒子）之间的距离为外边距margin。

盒子模型边框属性border：

<style type="text/css">
			div{width: 100px; height: 100px;background: pink;
			/* 最基本的边框写法 */
			/* border: 1px solid red; */
			/* 单独设置每个方向的边框效果 solid为实线，dashed为虚线*/
			border-top: 1px solid red;
			border-bottom: 2px dashed blue;
			border-left: 5px solid yellow;
			border-right: 10px dashed green;
			}
</style>

盒子模型内边距padding：

<style type="text/css">
			div{width: 100px; height: 100px;background: pink;
			/* 最基本的内边距、内填充、padding写法 四个方向间距一致 */
			/* padding:10px; */
			/* 以下是单独设置每个方向的语法 */
			/* padding-left: 10px;
			padding-right: 20px;
			padding-top: 30px;
			padding-bottom: 40px; */
			/* 如果写两个值代表：值1上下内边距，值2左右内边距 */
			padding: 10px 20px;
			/* 三个值代表：上 左右 下 */
			padding: 10px 20px 30px;
			/* 四个值：上 右 下 左 顺时针 */
			padding: 10px 20px 30px 40px;
			}
</style>

盒子模型外边距margin：

<style type="text/css">
			div{width: 100px; height: 100px;background: pink;
			/* 最基本的边框写法 */
			/* border: 1px solid red; */
			/* 单独设置每个方向的边框效果 */
			border-top: 1px solid red;
			border-bottom: 2px dashed blue;
			border-left: 5px solid yellow;
			border-right: 10px dashed green;
			/* 最基本的内边距、内填充、padding写法 四个方向间距一致 */
			/* padding:10px; */
			/* 以下是单独设置每个方向的语法 */
			/* padding-left: 10px;
			padding-right: 20px;
			padding-top: 30px;
			padding-bottom: 40px; */
			/* 如果写两个值代表：值1上下内边距，值2左右内边距 */
			/* padding: 10px 20px; */
			/* 三个值代表：上 左右 下 */
			/* padding: 10px 20px 30px; */
			/* 四个值：上 右 下 左 顺时针 */
			padding: 10px 20px 30px 40px;
			/* 一个值代表四个方向的外边距、外填充、margin相同 */
			/* margin: 10px; */
			/* 外边距也可以单独设置四个方向  */
			/* margin-left: 10px;
			margin-right: 20px;
			margin-top: 30px;
			margin-bottom: 40px; */
			/* 上下 左右 */
			/* margin: 10px 20px; */
			/* 上 左右 下 */
			/* margin: 10px 20px 30px; */
			/* 顺时针，上 右 下 左 */
			margin: 10px 20px 30px 40px;
			}
		</style>

## 4、html5

h5指的是：html5+css+javascript

html5结构标签：

<body>
		<!-- 在html5中这些结构标签都可以增加网站的语义化，从而提升搜索引擎对网站的排名 -->

		<header>头</header>
		<nav>导航</nav>
		<aside>侧边栏</aside>
		<article>文章块</article>
		<footer>底部</footer>
​	</body>

**数据列表标签**：下拉表可以手动输入

<!-- 数据列表标签：input中要设置list属性，里面值等于想要对应的数据datalist的id值，他们两个才能对应起来;option中的value要删掉，否则无法实现效果。-->

![image-20201126165034097](/Users/xuleping/Library/Application Support/typora-user-images/image-20201126165034097.png)

**html5新增表单验证相关属性：**

<form action="" method="get">
			<!-- required属性就是来设置空判断，输入框为空时提醒;autofocus自动获取焦点，光标自动在输入框 -->
			<input type="text" required="required" autofocus="autofocus"/><br />
			<!-- 属性autocomplete设置为on，默认为off，name的值对应着我们提交的数据所保存的文件夹一样的地方。再次填写时，会有以前填写内容的提示 -->
			<input type="text" autocomplete="on" name="hd"/>
			<input type="submit" value="提交" />
		</form>

**html5新增表单标签：**

<form action="" method="get">
			<!-- type="email" 实现邮箱地址的验证 -->
			邮箱：<input type="email"><br />
			<!-- type="url"就可以实现验证是否为网址，必须包含http://协议 -->
			网址：<input type="url" /><br />
			<!-- type="number" 让输入框只输入数字 -->
			数字：<input type="number" /><br />
			<!-- type="search" 可以在文本框中的最后位置出现一个x，点击后可把内容清空 -->
			搜索：<input type="search" /><br />
			<!-- type="datetime-local 让用户可以直接通过此文框弹出的时间日期来进行选择 -->
			详细日期时间：<input type="datetime-local" /><br />
			<!-- type="month" 可以直接选择月份 -->
			月份：<input type="month" /><br />
			<!-- type="week" 显示星期 -->
			星期：<input type="week" /><br />
			<!-- type="time" 显示时间 -->
			时间：<input type="time" /><br />
			<!-- type="date" 只显示日期 -->
			年月日：<input type="date" /><br />
			<!-- type="range"显示滑块 -->
			<input type="range" />
			<input type="submit" value="提交"/><br />
</form>

html5音频标签：

<!-- 音频标签价值很高，浏览器都想以自己为标准，所以W3C联盟组织，就规定了浏览器对音频标签的兼容性要求。
		 如果想要主流的浏览器都能很好的播放音频，就需要把音频设置为不同的格式，都加载到页面中，这样就可以保证浏览器兼容性。-->
		<!-- <audio src="shenshi.mp3" controls="controls" autoplay="autoplay" loop="loop"></audio> -->
		<!-- 一个audio标签可以添加多个音频的源 -->
		<!-- controls音频条，autoplay自动播放，loop循环播放-->

		<audio controls="controls" autoplay="autoplay" loop="loop">
			<source src="shenshi.mp3"></source>
			<source src="shenshi.ogg"></source>
		</audio>

html5视频标签：

<!-- 视频标签 -->

		<video controls="controls" autoplay="autoplay" loop="loop">
			<!-- 执行顺序，由上向下，能识别哪个就直接播放 -->
			<source src="video.mp4" type="video/mp4"></source>
			<source src="video.ogg" type="video/ogg"></source>
			<!-- 浏览器无法识别以上视频时，才会显示给用户看，用户可以点击链接下载视频，使用本地的播放器来看 -->
			当前浏览器不支持video直接播放，点击这里下载视频：<a href="">下载视频</a>
		</video>

## 5、css3

**css3圆角属性**：border-radius设置div椭圆形

**css3渐变颜色属性**在background中的linear-gradient（渐变方向也可以写角度的具体值180deg，色值，色值）颜色值后面添加百分比，从0开始到100%设置颜色渐变的区域：background: linear-gradient(to right,red,blue)

**css3盒子阴影效果：**

/* 盒子阴影效果 */
			div{width: 200px; height:100px; background: gold; margin: 10px; border-radius: 10px;
			 border: 1px solid black;}
			 /* box-shadow：水平方向 垂直方向 阴影大小 阴影颜色*/
			 .div1{box-shadow: 0px 0px 30px red;}
			 /* inset实现的效果就是内阴影 */
			 .div2{box-shadow: 0px 0px 30px red inset;}

**css3半透明背景：**

/* 透明背景 */
			 body{background:url(01.jpeg)}
			 /* background:rgba（红，绿，蓝，透明度值）
			 红绿蓝都是色值号设置的，可以使用浏览器调试工具来把想要的色值拿到；
			 透明度的值：0到1之间，0代表全透明，1代表全不透明。可以设置0到1之间的小数来代表透明度的百分比。 */
			 div{width: 300px; height: 300px; border-radius:10px; background:rgba(85,124,173,0.5); 
			 box-shadow: 3px 3px 8px black;}

css3文字阴影：text-shadow属性：x轴 y轴 阴影大小 色值；div{text-shadow:1px 1px 0px white}

css3旋转、缩放、位移

/* 翻转：transform: rotate(角度值) */
			 .div1{transform: rotate(90deg);}
			 /* 缩放：transform: scale(缩放比例) */
			 .div2{transform: scale(0.3);}
			 /* transform: translate(x轴位移,y轴位移) */
			 .div3{transform: translate(100px,100px);}

css3过渡属性：

 /* 过渡属性 */
			 div{width: 200px; height: 50px; background: rgba(255, 0, 56, 0.3); margin: 50px;
			 transition: all 1s;}
			 /* transition：想要过渡的属性，一般都写all，代表所有属性只有变化了都以过渡动画的形式展示，时间代表动画的执行时间 */
			 /* hover叫css伪类，鼠标悬停时候的样式 */
			 .div1:hover{transform: scale(1.5);background: rgba(25, 0, 56, 0.3);}

css3属性hover同时实现放大和旋转效果

div:hover{
				/* 同一个属性名，值使用空格分隔即可实现多个值书写 */
				transform:scale(1.3) rotate(360deg);
				}

/* 会旋转的头像 */
				/* border-radius: 50% 代表设置成正圆形（前提是形状为正方形） */
				/* transition 第一个时间代表动画的运行时间，第二个时间代表延迟时间，默认的为ease的匀速，ease-in变加速，ease-out变减速；ease-in-out先加速后减速 */
				img{width: 50px;height: 50px;border: 5px solid cadetblue; border-radius: 50%;margin:10px;transition:all 1s 2s ease-in;}
				img:hover{transform:rotate(360deg)}

/* 图片放大并旋转，transform */
				img{margin:30px; border: 1px solid red; transition:all 1s .5s;}
				/* 时间如果o.x，前面的0可以省略 */
				img:hover{transform:scale(1.2) rotate(5deg);}

/* 图片y轴旋转 */
				img{border: 1px solid red; margin:10px;transition:all 1s;}
				/* transform:roateY沿着y轴旋转；roateX沿着x轴旋转；默认是沿中心旋转 */
				img:hover{transform:rotateY(180deg)}

/* css自定义样式  animation调用动画,infinite无限循环动画 alternate逆向动画  颜色渐变，左右移动*/
			div {
				width: 100px;
				height: 30px;
				border: 1px solid red;
				border-radius: 10px;
				animation: go 1s infinite alternate;
			}

			/* 使用keyframes定义动画 */
			@keyframes go {
	
				/* 开始时候状态 */
				from {
					background: red;
					transform: translate(0px, 0px);
				}
	
				/* 结束时候状态 */
				to {
					background: blue;
					transform: translate(100px, 0px)
				}
			}
卸载应用程序时出现颤抖效果：

img:hover{animation:dou .1s 1s infinite alternate}
			/* 可以使用百分比替代默认的from、to */
			/* animation：时间如果出现两个，第一个代表动画运动时间，第二个代表延迟时间，也可以设置ease等变速效果 */
			@keyframes dou{
				0%{transform:rotate(-5deg)}
				50%{transform:rotate(0deg)}
				100%{transform:rotate(5deg)}
			}

## 6、js（JavaScript）

简介：初期是为了验证表单数据是否合法。比如用户名、密码等格式的提醒，写完输入框直接进行验证，而不是提交的时候进行验证。

现在是控制html和css的结构和样式。

<script type="text/javascript">
	// 弹出对话框 所有的js代码都要使用英文状态下的符号。小括号中可以使用双引号或者单引号来包裹文字。
	alert("登录过期");
</script>

**js找元素、找标签、找标记**

// 找元素 document代表页面文档；getElementById 命名方式为驼峰命名法，用法是使用id获取页面中的标签、标记、元素；验证的使用可以用浏览器，打开f12调试工具下的console，输入此命令即可。

​	document.getElementById("div1");

**js实体化**：

// js实体化 先找到，再用英文状态下的点进行连接 可定义变量进行简化，var elementStyle=document.getElementById("div2").style;以后直接用变量使用就行。变量起名字注意事项：可以使用中文，可以使用符号_$，命名不可以使用数字开头，不允许使用js已经占用的单词（保留字）
	document.getElementById("div2").style.width="200px";
	document.getElementById("div2").style.height="200px";
	document.getElementById("div2").style.background="blue";

**js点击事件**：点击三个按钮分别变宽、变高、变色


	<script type="text/javascript">
	// 事件：在什么情况下做了什么事情； 事件三要素：事件源.事件类型=匿名函数里边写的就是要执行的命令。
	// 找到页面中的id元素后，习惯性的保存到变量中，方便后续的使用
	var btn_w = document.getElementById("btn_w");
	var box = document.getElementById("box");
	var btn_h=document.getElementById("btn_h");
	var btn_c=document.getElementById("btn_c");
	btn_w.onclick = function() {
		// 点击后执行的命令
		box.style.width="200px";
	}
	btn_h.onclick = function(){
		box.style.height="200px";
	}
	btn_c.onclick = function(){
		box.style.background="red";
	}
	</script>
**js找页面标签的方法：**

通过id定位元素：document.getElementById("div1");

// 通过类名定位元素，必须在后面添加[数字] 数字计数从0开始 点击div弹框
	// document.getElementsByClassName("div1")[0].onclick=function(){
	// 	alert();
	// }

	// 通过标签名字定位元素，也要加[数字]
	// document.getElementsByTagName("div")[0].onclick=function(){
	// 	alert();
	// }
	 
	 // 通过name属性值定位元素，也需要加[数字] name的值可以重复出现
	 document.getElementsByName("hbu")[0].onclick=function(){
		 alert();
	 }
js事件总结：

<script>
	// 点击div执行弹出对话框操作
	var div1=document.getElementById("div1");
	div1.onclick = function(){
		alert("单击事件被捕获");
	}
	// ondblclick代表双击事件
	var div2=document.getElementById("div2");
	div2.ondblclick=function(){
		alert("双击事件被捕获");
	}
	// onmouseover代表鼠标移入事件
	var div3=document.getElementById("div3");
	div3.onmouseover=function(){
		alert("鼠标移入事件被捕获");
	}
	// onmouseout 代表鼠标移出事件
	var div4=document.getElementById("div4");
	div4.onmouseout=function(){
		alert("鼠标移出事件被捕获");
	}
</script>

js书写位置：

内嵌js：在html底部添加<script></script>

外链js：添加另外的js文件，引入到src属性中

<script type="text/javascript" src="19js.js"></script>

强烈推荐外链js，实现了代码的分离，修改会很方便。

注意：html中写js代码，行内js html的标签属性值要使用双引号，里面的js代码使用单引号；行内js强烈不推荐使用，因为没有实现代码的分离效果，语法修改不方便。

js代码搬家：

js代码<script></script>也应该放在head标签最后，而不是html后面。放在head里需要加window.onload

<!-- 代码由上向下运行，没有获取到box。需要添加window.onload，当页面所有html内容都加载完毕后才执行此处的代码 -->

		<script type="text/javascript">
			window.onload=function(){
				var box=document.getElementById("box");
				box.onclick=function(){
					alert("点击成功")
				}
			}	
		</script>

**js动态添加和删除文本：**

<!-- innerHTML作用是设置标签的中间内容 -->

		<script type="text/javascript">
			window.onload=function(){
				var box=document.getElementById("box");
				var btn_add=document.getElementById("btn_add");
				var btn_del=document.getElementById("btn_del");
				btn_add.onclick=function(){
					// 点击后设置div中的html显示文字
					box.innerHTML="点击后此处文字才会被innerHTML设置成功";
				}
				btn_del.onclick=function(){
					// 点击删除按钮，让文字清空
					box.innerHTML="";
				}
			}
		</script>

js函数：

<script type="text/javascript">
			window.onload=function(){
				// 自定义函数作用：简化代码，实现重复性代码的简单调用；
				// function 名字(){自己的js程序}
				// 如果要执行这个函数中的js程序，必须要写 函数名（）才能执行函数中的命令
				// 自定义函数在js运行时会优先执行函数；函数必须调用才可以执行其中的js代码
				function hi(){
					alert("弹出");
				}
				hi();
			}
		</script>

## 7、xml

<!-- xml传输数据，自定义标签，双标签，标签嵌套不能出问题 -->
<person>
	<height>1.8</height>
	<age>18</age>
	<wight>100</wight>
</person>

## 8、软件测试质量

为什么需要软件测试：对软件要求越来越高，不仅关注于当前软件的主体功能是否可用，还会对软件的外观、易用性、执行效率等方面考虑

为什么选择软件测试：创造世界从事开发工作，世界变得更美好从事软件测试；国内对软件测试的需求量非常大。

为什么不让开发自己做测试：专业度：测试和开发属于软件行业不同的技术方向；思维定式：软件开发周期，开发人员主要思考软件功能如何实现，而不会主动从用户角度出发，如何使用此功能；测试力度，测试者测试深度更高。

软件测试：通过手工或者工具对被测对象操作，从而验证实际结果与预期结果之间是否存在差异。

测试工作的目的就是通过尽可能少的人力、财力、物力才查找并解决软件中存在的缺陷从而降低商业风险等。

### 1、测试原则：

测试证明软件存在缺陷：测试工作只能证明当前软件存在缺陷而不能证明它没有缺陷；

不能执行穷尽测试：具体的测试操作不可能将所有的情况一一罗列出来，应该分类别测试；

测试应尽早介入：一般不要在开发完成后才执行测试，这样不利于缺陷的尽早发现；

缺陷存在群集现象：2 8原则，软件的核心功能只占20%，出现bug的总量占总个比例的80%左右；非核心模块80%的代码，出现bug数量占总量的20%左右。所以在测试的时候会花更多的时间去专门测试核心功能。

某些测试操作依赖于特定的测试环境；

杀虫剂现象：不要过多使用同一条测试案例来对软件进行问题查找。解决办法多采用交叉测试，a测试b，b测试a。

不存在缺陷的缪论：任何软件不可能是完美的；

### 2、常见软件架构：

最常见的两种架构：B/S（浏览器--服务器模型）和C/S（客户端--服务器模型）

b/s与c/s比较：

标准：bs架构无论是浏览器还是服务器都有现成软件使用，而cs架构的客户端一般根据不同的操作系统自定义开发，因此相对来说bs标准些。

效率：bs架构中所有数据的处理都发生在服务器端；cs的客户端可以分担一些服务器数据处理工作， 有默认导航栏之类的，因此cs的处理效率相对较高；

升级：bs架构只需要将服务器进行更新，那么前台页面会自动刷新；而cs架构如果想要升级，需要删除老版本，安装新版本。

安全性：bs安全性低一些，用户量大；cs安全性高些；

开发成本：浏览器不需要开发，cs开发成本高些。

### 3、常见的图片类型：

.jpg：颜色信息比较丰富的一种图片格式；

.png：可以支持透明的一种图片格式；

.gif：支持动图，占用体积小；

.psd：分层的图片【常见于psd设计稿】

### 4、域名和服务器

域名：为了方便用户记忆而自己设计的一个名字，需要花钱购买，比如在万网下阿里云购买域名。域名一般分为三个部分：

一级域名：最后一个点后面的内容：.com .cn .net

二级域名：一级左边,baidu,一般都是需求方自己设计，一级域名和二级域名连在一起应该是全世界唯一。

三级域名：一般都是用户自定义，最常见的是www

服务器：认为是一台电脑，，它的上面可以安装相应的服务器软件，为用户提供服务操作。

URL：在浏览器地址栏中的一长串：协议+域名+端口号+路径+具体的文件名称组成。

网站的访问过程：

在浏览器中输入URL；

解析URL，找到相应的IP；

查找IP，首先会从本地的hosts文件开始，如果找不到则去DNS服务器查找；

如果DNS找到了目标的IP，先发送一个测试的请求，通过之后再发送正式请求；

服务器接收到正式的请求之后，并验证通过之后，会找到当前请求想要的文件；

服务器处理请求；

服务器处理完成之后通过http协议还给浏览器。（浏览器用渲染引擎来进行渲染展示）

### 5、网络基本概念

客户端（Client）：移动应用（IOS、Android、Web等应用）；

服务器（Server）：为客户端提供服务、提供数据、提供资源的机器；

请求（Request）：客户端向服务器索取数据的一种行为；

响应（Response）：服务器对客户端的请求作出反应，一般指返回数据给客户端；

协议：计算机通信网络中两台计算机之间进行通信所必须遵守的规则或规定。

HTTP协议：超文本传输协议，是一种规定了浏览器和服务器之间通信的规则；

URL（统一资源定位符）：互联网上资源的地址、位置。每个资源都有一个唯一的URL。

格式：协议：//主机地址/路径