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

**基础选择器权重**：

针对同一个标签设置css才有权重：id>class>标签；继承的权重最低

复合选择器权重：

针对同一个标签设置css属性，最终计算权重最大的才会生效。







