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

​	cd .. 回到上一级目录；cd ~ ：到自己的家目录(~) /Users/xuleping；cd - 电视回看功能

pwd查看当前路径；

ls 显示当前目录下的内容

​	ls -a：显示当前目录下的所有文件（包括隐藏文件，隐藏文件是以.开头的文件）

​	ls -l（ll）：显示详细列表信息

​	ls -lh（ll-h）：大小默认为字节B，加上h会显示单位，把文件大小以人性化方式显示。1B（字节）=8b（位）

​	ls -al

​	ls -alh

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

​	rm -r 删除文件夹

​	rm -r *：删除当前目录下所有文件，不包括隐藏文件

clear：翻屏

tab键：自动补全

上下键可以切换到以前使用过的命令

ctrl(control)+c：强制退出

ctrl+ 可以使字体变大

ctrl- 可以使字体变小

ls -l：xuleping当前用户，staff表示组用户

d rwx r-x r-x：d 代表文件夹，- 代表文件；r可读 w可写 r执行，三组分别代表当前用户（文件拥有者）权限，文件拥有的组权限，其他用户权限。

![image-20201202191458302](/Users/xuleping/Library/Application Support/typora-user-images/image-20201202191458302.png)

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

​	cat a.txt 查看文件内容

​	cat a.txt 把文件内容全部显示到屏幕中

​	cat a.txt b.txt 同时查看多个文件的内容，按顺序进行显示

​	cat a.txt b.txt > c.txt 把多个文件的内容合并到一个新的文件

more 查看文件内容，可以分页显示

​	ls / >> a.txt

​	more a.txt 查看内容多的文件，按空格往下翻页，按enter往下翻一行，按b往回翻页，按q键退出。

管道 ｜把左边命令返回的结果交给右边命令进行处理，比如 ls -l / | more



