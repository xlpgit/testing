# 1、操作系统

操作系统将自然语言翻译到硬件中（二进制形式），软件只需要支持操作系统即可，不用支持硬件。

操作系统主要作用是管理好硬件设备，并为用户和应用程序提供一个简单的接口，以便于使用。作为中间人，连接软件和硬件。

主流操作系统：

桌面操作系统（windows、macOS、Linux）；

服务器操作系统（Linux：安全、稳定、免费；Windows Server：付费，占有率低），一般只有主机没有显示器，一般放在机房或者租用；

嵌入式操作系统：Linux，比如扫地机器人、手表；

移动设备操作系统：ios、android（基于linux）。

虚拟机（virtual Machine），本身是一个软件，里边可以装各种操作系统。

linux发展历程：unix->minix->linux

linux内核：与驱动（硬盘）打交道。

linux发行版：与用户打交道，通常包含了包括桌面环境、办公软件、媒体播放器、数据库等软件。Ubuntu、CentOS

linux的应用领域：服务器领域、嵌入式领域（手机、机顶盒）、个人桌面（薄弱）

# 2、Linux文件和目录

linux只有根目录，不再有c、d等盘。

/home：系统默认的用户家目录；

/root:系统管理员root的家目录

/bin：可执行二进制文件的目录

/mnt：挂载。android基于linux，在mnt下

# 3、常用的命令

用终端terminal中输入命令

命令格式：command [-options] [parameter]

command --help 帮助文档

cd 切换文件夹：

​	绝对路径：以根目录开头，比如/home

​	相对路径：不以根目录开头

​	cd .. 回到上一级目录；

​	cd ~ ：到自己的家目录(~) /Users/xuleping；

​	cd - 电视回看功能

pwd查看当前路径；

ls 显示当前目录下的内容

​	ls -a：显示当前目录下的所有文件（包括隐藏文件，隐藏文件是以.开头的文件）

​	ls -l（ll）：显示详细列表信息

​	ls -lh（ll-h）：大小默认为字节B，加上h会显示单位，把文件大小以人性化方式显示。1B（字节）=8b（位）

​	ls -al：显示包含隐藏文件在内的详细列表信息

​	ls -alh：显示包含隐藏文件在内的详细列表信息，文件大小可显示单位

mkdir 创建文件夹

​	mkdir test：在当前目录下创建文件夹；也可以指定目录创建文件夹

​	mkdir -p test/test1：递归创建文件夹，如果上级目录不存在，加上-p自动创建父目录

​	mkdir test1 test2：在当前目录下创建多个文件夹，用空格分隔

​	mkdir test/{test1,test2}：在指定目录下创建多个文件夹，用{}

​	mkdir .test 以.开头，创建隐藏文件夹

​	.和.. 隐藏文件夹是任何目录下的隐藏文件夹，.代表当前目录，..代表上一级目录。

touch 创建空文件

​	touch a.txt 在当前目录创建空文件，如果指定了目录，必须保证上级目录存在。

​	touch a b 同时创建多个文件，用空格分开

​	touch .a 创建隐藏文件

vim 创建并编辑，若已经创建，直接编辑即可

rm 删除文件

​	rm a.txt 删除文件

​	rm a.txt b.txt 同时删除多个文件

​	rm -r test 删除文件夹

​	rm -r *：删除当前目录下所有文件，不包括隐藏文件

常用的快捷方式：

​	clear：翻屏

​	tab键：自动补全

​	上下键可以切换到以前使用过的命令

​	ctrl(control)+c：强制退出

​	ctrl+ 可以使字体变大

​	ctrl- 可以使字体变小

ls -l：xuleping当前用户，staff表示组用户

d rwx r-x r-x：d 代表文件夹，- 代表文件；r可读 w可写 r执行，三组分别代表当前用户（文件拥有者）权限，文件拥有的组权限，其他用户权限。

<img src="/Users/xuleping/Library/Application Support/typora-user-images/image-20201202191458302.png" alt="image-20201202191458302" style="zoom:50%;" />

ls查看其它目录的内容

ls可以直接定位来查找，不用通过cd再查找，比如：ls -l test，查看test文件夹下的目录

通配符 :

​	*：任意 ，比如：ls *txt 查看当前目录下所有以txt结尾的文件。

​	？：一个，文件名中任意一个字符

​	[] 匹配字符组中的任意一个

​	[abc] 匹配a b c中的任意一个

​	[a-x] 匹配字符组 a-x 的任意一个

​	\  转义

cp 拷贝文件：

​	cp -a a.txt b.txt：复制目录时使用，保留文件原有属性，包括链接、文件属性、时间等。直接覆盖

​    cp a.txt b.txt：拷贝文件，源文件->目标文件

​	cp -r test1 test2：拷贝文件夹，若给出的源文件是目录文件，则cp将递归复制该目录下所有的子目录和文件，目标文件必须为一个目录名。

​	cp -i a.txt b.txt：提示是否覆盖

​    cp -v a.txt btxt：显示移动过程

mv 移动 重命名

​	mv a.txt b.txt：重命名文件

​	mv a.txt test：移动文件到文件夹中，默认为原文件名称

​	mv a.txt test/b.txt：移动文件同时并重命名

​	mv test1 test2：移动文件夹，将test1文件夹移动到test2文件夹下

​	-i提示是否覆盖，-v显示移动进度

重定向 >

​	ls > a.txt 把命令返回的结果重定向（输出）到文件中，并覆盖原文件内容。默认情况命令返回的结果显示在屏幕中

​	ls >> a.txxt 把命令返回的结果重定向（输出）到文件中，追加的方式，不覆盖原文件内容

cat 查看文件内容，直接显示到屏幕上，不能修改。文件内容比较多时，屏幕显示不全，cat默认情况是翻到最后一行；

​	cat a.txt 把文件内容全部显示到屏幕中

​	cat a.txt b.txt 同时查看多个文件的内容，按顺序进行显示

​	cat a.txt b.txt > c.txt 把多个文件的内容合并到一个新的文件

more 查看文件内容，可以分页显示

​	ls / >> a.txt

​	more a.txt 查看内容多的文件，按空格往下翻页，按enter往下翻一行，按b往回翻页，按q键退出。

管道 ｜把左边命令返回的结果交给右边命令进行处理，比如 ls -l / | more

windows桌面上的图标，是引用了某个位置，直接在桌面打开，不用找到文件安装目录打开。快捷方式

ln 链接

​	软链接：链接本身不存储内容，只记录源文件名称

​	ln -s 1.txt 1_soft_link ，文件创建软链接。给1.txt创建一个软链接，相当于windows中的快捷方式。

​	1_soft_link是快捷方式，指向了1.txt。原文件内容发生变化，快捷方式下的文件也发生变化。链接方式下的文件发生变化，源文件也变化。删快捷方式不影响源文件，删源文件影响快捷方式。   --软链接，不存文件里的内容，只记录名称，只要名称一样就可链接。类似于别名。（比如，删除源文件，快捷方式失效，再重新新建一个相同名称的文件，仍可以进行链接）。

​	注意：如果软链接和源文件不在同一个目录，源文件要使用绝对路径，不能使用相对路径。

​	ln -s test1 test_soft_link，文件夹（目录）创建软链接

硬链接：本身占空间，相当于把源文件复制一份，与源文件同步变化。使用ll查看时，有一个数字，代表有几个文件能同步发生变化。删除硬链接文件，不影响源文件，不能给目录创建硬链接。

​	ln 1.txt 1_hard_link：文件创建硬链接

grep 文本搜索（查找文件内容）

​	grep hello a.txt：在某个文件中查找保护hello的内容，之一一行中有hello会把整行显示

​	grep -niv hello a.txt：在指定文件查找，-n显示查找到的内容的行号，-i查找时忽略大小写，-v反向查找，查找不包含hello的行

​	grep -n hello . -r：.代表当前目录，在当前目录下查找文件内容中包含hello

正则表达式：

​	grep -n ^h a.txt：在文件中查找以h开头的行

​	grep -n o$ a.txt：在文件中查找以o结尾的行

​	grep -n h. a.txt：在文件中查找以h开头且后面有一个字符

​	*匹配零个或多个字符，[ ]匹配指定范围内的字符

find 查找文件

​	find . -name 1.txt：在当前文件夹下查找文件名为1.txt的文件

​	find . -name '*txt'：在当前文件夹下查找以txt结尾的文件，需要加单引号

tar 归档管理 文件打包，解包

​	-c 生成压缩包文件（compress)；-f 指定压缩文件(file)；-t 列出压缩文件中的内容；-x 从压缩包中抽取文件（解）；-v 显示操作过程

​	tar cvf first.tar 1.txt 2.txt ：打包，f必须放在最后，f后面的第一个参数代表要生成的文件名，后面的所有参数是要打包的文件。将文件1，2打包到first

​	tar xvf first.tar：在当前目录下解压。如果没写目录，把包里面的文件解开放到当前目录

​	tar xvf first.tar -C tar：解压到指定文件夹，文件夹需要提前创建好。

gzip 文件压缩，解压；-r压缩，-d解压

​	生成压缩文件：先打包后压缩；tar cvf first.tar 1.txt 2.txt 生成first.tar文件；gzip -r first.tar 生成压缩后的first.tar.gz文件

​	解压压缩文件：先解压后解包；gzip -d first.tar.gz 生成first.tar文件；tar xvf first.tar -C test/ 解包到指定文件中

实际应用中可以tar与gzip可以结合使用：

​	一步到位，打包并压缩：tar zcvf two.tar.gz *.txt 以gzip的方式打包并压缩。

​	一步到位，解压并且解包：tar zxvf two.tar.gz -C test/ 以gzip的方式解压并且解包。

bzip2 文件压缩解压

​	一步到位，打包并压缩：tar jcvf three.tar.bz2 *txt   以bzip2方式

​	一步到位，解压并解包：tar jxvf three.tar.bz2 -C test3/  以bizp2方式

zip,unzip文件压缩，解压

​	zip -r four *txt  four表示要生成的压缩文件，不需要写扩展名，会自动生成zip扩展名

​	unzip -d four four.zip 解压时会自动创建目录

压缩率，zip<gzip<bzip2

通用性：zip>gzip>bzip2

which 查看命令位置

su 	切换管理员权限，su root; su xuleping; su admin

passwd 设置密码

exit 退出登录

who 查看当前登录的用户

pst/0 代表一个终端；tty代表用户登录了操作系统

reboot重启，不需要权限，shutdown关机 shutdown -h +10 设置10分钟后关机  --需要root权限

chmod 修改文件权限 字母法+数字法

字母法：

​	r/w/x/-：可读，可写，可执行，无权限

​	u/g/o/a对应：user/group/other/all   文件的拥有者，文件的拥有的组，其他用户，所有用户

​	+-=：当前权限基础上增加权限，当前权限基础上减权限，赋值权限(把之前的权限换成新的权限)

​	chmod u+r test.txt 给文件的拥有者添加r（读）权限

数字法：

​	r/w/x/-：分别对应的数字上4，2，1，0

​	chmod 123 test.txt  第一位数字代表自己的权限；第二位代表自己组的权限，第三位代表其他人的权限。执行；写权限；读和执行权限

