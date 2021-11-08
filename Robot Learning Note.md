# Robot Learning Note

## Linux基础命令

- $ cat file1 file2 ...：将文件file1, file2等的内容拼接起来并显示，然后退出。

  $ cat >> file：从键盘读取数据，将数据追加到已有文件中。

  $ cat file：显示file文件内容

- $ ls：显示指定目录内容，缺省参数为当前目录，ls -l显示详细列表，ls -F显示文件类型信息。

- $ cp：拷贝文件。

  $ cp file1 file2：将文件file1拷贝到文件file2。

  $ cp file1 ... fileN dir：将多个文件file1到fileN拷贝到目录dir。

- $ mv：重命名文件。

  $ mv file1 file2：将文件名从file1重命名为file2。

  $ mv file1 ... fileN dir：将多个文件移动到某个目录。

- $ touch file：创建一个文件，如果文件已经存在，则该命令会更新文件的时间戳。

- $ rm file：用来删除文件，文件一旦被删除通常无法恢复。

- $ echo s：将参数s显示到标准输出。

  $ echo s > file：将s内容显示到file文件

- 目录之间使用/分割，以/开头的路径叫绝对路径，不以/开头的路径叫相对路径。

  ..代表一个目录的上层目录。

  .代表当前目录。通常不需使用.，而是直接使用目录名来访问当前目录下的子目录。

- $ cd dir：切换当前的工作目录为dir。如果不带dir，cd命令会跳到你的个人根目录。

  $ cd ..：切换到上一目录。

- $ mkdir dir：创建一个名为dir的新目录。

- $ rmdir dir：删除一个目录。rmdir只能删除空目录。可以使用rm -rf来删除一个目录及其中的所有内容。

- $ grep s dir：显示文件和输入流dir中和参数s匹配的行的内容。

  $ grep s /etc/*：查看目录/etc中所有包含s的文件。

  $ grep -i：不区分大小写。$ grep -v：反转匹配，显示所有不匹配的行。

- $ less file1：当要查看的文件过大或者内容多得需要滚动屏幕的时候，less将内容分屏显示，按空格查看下一屏，b键查看上一屏，q键退出。

- $ pwd：显示当前目录的绝对路径。

- $ diff file1 file2：查看两个文件之间的不同。

- $ file file：获取一个文件的格式信息。

- $ find [目录名] [选项] [查找条件]：在指定目录中寻找符合选项条件的文件。

- $ head -n file/ $ tail -n file命令显示文件的前n行内容，tail命令显示文件的最后n行内容，n参数缺省默认10行。如果要从第n行开始显示所有内容，使用tail +n。

- $ sort：将文件内的所有行按照字幕顺序排序，使用-n选项按照数字顺序排序那些以数字开头的行，使用-r选项反转排序。

- $ passwd username：更改用户密码。

- 命令路径PATH：存放路径，路径之间以冒号分隔。

  $ PATH=dir:$PATH：将路径dir加入到PATH的最前面。

  $ PATH=$PATH:dir：将路径加入到PATH变量的最后面。

- $ info [指令]：查看指令相关帮助信息。

- $ man [指令]：查看指令相关手册。

- $ clear：刷新屏幕，并保留历史命令操作记录。

- $ command > file：将命令的执行结果输出到文件（默认终端屏幕）。如果文件file不存在，则创建一个新的file文件；如果file文件已经存在，Shell会清空文件内容。

  $ command >> file：将命令的输出结果加入到文件尾部

  $ command1| command2：使用管道字符 | 将一个命令的执行结果输出到另一个命令。命令1的正确输出作为命令2的操作对象。

- 常见错误：

  No such file or directory：访问一个不存在的文件或者目录。

  File exists：新建文件的名称和现有的一个文件或者目录重名。

  Not a directory, Is a directory：把文件当作目录或者反过来，把目录当作文件。

  No space left on device：硬盘空间不足。

  Permission denied：读或写一个没有权限访问的文件和目录时。

  Operation not permitted：试图终止一个无权终止的进程时。

  Segmentation fault, Bus error：分段故障，总线繁忙，常因程序输入数据有问题。

- $ ps：列出所有正在运行的进程。PID：进程ID。TTY：进程所在的终端设备。STAT：进程状态，就是进程在内存中的状态。TIME：进程目前为止所用CPU时长。COMMAND：进程名。

- $ kill pid：终止一个进程。

  $ kill -STOP pid：被暂停的进程仍然停留在内存，等待被继续执行。

  $ kill -CONT pid：继续执行进程

- 在命令行末尾添加&操作符将进程设置为后台运行。

- $ chmod file：更改文件权限。

  $ chmod g+r file：为用户组（g）加上可读权限（r）。

  $ chmod o+r file：为其他用户（o）加上可读权限（r）。

- $ ln -s target linkname：创建符号链接，相当于文件的别名。linkname参数是符号链接名称，target参数是要指向的目标路径，-s选项表示这是一个符号链接。

- $ gunzip file.gz：解压缩.gz文件。

  $ gzip file：压缩文件并删除原有文件。

  $ gzip -l file：查看压缩文件内容。

  $ gzip -kd file：解压以.gz文件且保留原文件。

  $ gzip -k file：压缩文件且保留原文件。

- $ tar：多个文件的压缩与解压。

  $ tar cvf archive.tar file1 file2 ...：archive.tar参数是生成的归档文件名，file1 file2 ...是要归档的文件和目录列表。选项c代表创建文件，选项v用来显示详细的命令执行信息，选项f代表文件，后面需要指定一个归档文件名，如果不指定归档文件名，则归档到磁带设备，如果文件名为－，则归档到标准输入或者输出。

  $ tar xvf archive.tar：解压缩tar文件。选项x代表解压模式。还可以只解压归档文件中的某几个文件，只需要在命令后面加上这些文件的文件名。

- $ zcat file：显示压缩包中文件的内容。

- 其他压缩/解压缩命令：bzip2/bunzip2，xz/unxz。

- $ sudo：以root用户身份执行命令。

- $ ping：用于检测主机。

- $ htop：显示系统中正在运行的进程的实时状态。

- $ ps：显示当前进程的状态，参数：-A 列出所有的进程；-w 显示加宽可以显示较多的资讯；-au 显示较详细的资讯；-aux 显示所有包含其他使用者的行程。

- $ history n：显示历史执行过的n条命令。! number执行第几条命令；! command从最近的命令查到以command开头的命令执行；!!执行上一条 。

- $ ifconfig

  $ iwconfig

- $ apt-get install software_name：安装软件 

- $ sudo apt-get update：下载最新的软件列表

- $ sudo apt-get upgrade：安装更新

- Ctrl+C：结束当前命令进程。

- $ stty -echo #：设置输入字符不回显。

  $ stty echo #：设置输入字符回显。

  

## Git操作及命令

- 初始化Git仓库：

  ①创建一个空目录：

  ​    $ mkdir dir

  ​    $ cd learngit

  ​    $ pwd

  ②使用git init命令把当前目录变为git仓库。

- 把文件添加到库：

  ①把文件放到库目录下

  ②使用git add file命令，将文件添加到暂存区

  ③使用git commit -m “instruction”命令，把暂存区所有文件提交到仓库，引号内为此次提交的说明。

- git status：显示仓库当前的状态（是否有需提交的文件，是否有文件被修改但未提交）

- git diff：查看文件修改内容。

  git diff HEAD -- file：查看工作区和版本库里面最新版本的区别。

- git log：显示从最近到最远的提交日志

  git log --pretty=oneline：显示从最近到最远的提交日志（每次提交在一行中显示）

  git log --graph --pretty=oneline --abbrev-commit：显示分支合并图。

- git reflog：显示使用的每次命令（找回版本号）

- git reset -hard edition：将当前版本设置为edition版本（HEAD为当前版本，HEAD^为上一版本，HEAD^^为上两版本，HEAD~n为上n版本；edition也可是版本号）。

  git reset HEAD file：把暂存区的修改撤销掉，重新放回工作区。

- git checkout -- file：直接丢弃工作区的修改，将工作区文件还原到提交前版本。

  git checkout -b branch：创建并切换到branch分支。

  git checkout -b branch origin/branch：在本地创建和远程分支对应的分支。

  git checkout branch：切换到branch分支。

- git branch：查看当前分支。

  git branch -d branch：删除branch分支。

  git branch -D branch：强行删除一个没有被合并过的分支。

  git branch --set-upstream-to branch origin/branch：创建本地分支和远程分支的链接关系。

- git merge branch：将branch分支合并到当前分支。

  git merge --no-ff branch：禁用Fast forward（不覆盖分支信息，保留历史有分支），将branch分支合并到当前分支。

- git switch -c branch：创建并切换到branch分支。

  git switch branch：切换到branch分支。

- git rm file：从版本库中删除文件（删除后需commit提交修改）

- ssh-keygen -t rsa -C "youremail@example.com"：创建SSH Key。

- git remote add origin git@github:path/repo-name.git：关联github远程库（一个本地库可以关联到两个远程库，但需要起不一样的远程库名称，把origin默认名改掉）。

  git remote / git remote -v：查看远程库信息。

  git remote rm <name>：解除本地和远程库的绑定关系。

- git push -u origin branch：第一次向github远程库推送branch分支的所有内容。

  git push origin branch：向github远程库推送branch分支的所有本地提交。

  git push origin tagname：向github远程库推送某个标签。

  git push origin --tags：向github远程库推送所有未推送的标签。

  git push origin :refs/tags/tagname：删除github远程库中的tagname标签。

- git clone git@github.com:path/repo-name.git：克隆一个远程仓库到本地。

- git stash：保存当前工作状态，清理工作区，方便处理其他工作。

  git stash list：显示stash保存的工作状态。

  git stash apply：恢复保存的工作状态，不删除stash内容。

  git stash drop：删除stash内容。

  git stash pop：恢复保存的工作状态，并删除stash内容。

- git cherry-pick edition：将一个特定的提交复制到当前分支，edition为提交的版本号。

- git pull：把最新的提交从远程库对应分支抓下来，并在本地合并。

- git rebase：把本地未push的分支提交历史整理成直线。

- 创建标签：

  ①切换到需要打标签的分支上：git switch branch

  ②使用命令git tag tagname edition：为版本号为edition的commit打一个新标签tagname（edition缺省则默认打在最新提交的commit上）。

  git tag：查看所有标签。

  git tag -a tagname -m "instruction" edition：创建带有说明的标签。

  git tag -d tagname：删除tagname标签。

- git show tagname：显示标签说明文字。

- git config --global alias.abbr order：设置order命令的别名为abbr



## SSH操作及命令

- ssh-keygen：在本地计算机上生成 RSA 密钥对。

  ssh-keygen -t rsa -b 4096 -f ~/.ssh/user_ca -C user_ca

- ssh-copy-id username@remote_host：将公钥复制到服务器。

- ssh remote_host / ssh username@remote_host：连接到远程服务器。

  ssh username@remote_host command_to_run：在远程服务器上运行单个命令。

  ssh -p port_num username@remote_host：指定端口号，登录到具有不同端口的服务器。

- eval $(ssh-agent)

  ssh-add：启动代理程序并将私钥添加到代理，无需再次重新输入密码。



## Vim基本操作

- 模式：插入模式、命令模式、最后一行模式

  i：进入插入模式

   ‘：’：进入最后一行模式

  esc：退出插入模式

- 移动光标：在移动命令前加上数字表示执行次数

  H：将光标向左移动一个字符。

  j：将光标向下移动一行。

  k：将光标向上移动一行。

  l：将光标向右移动一个字符。

  0：将光标移动到行首。

  $：将光标移动到行尾。

  w：向前移动一个字。

  b：向后移动一个字。

  G：移动到文件末尾。

  gg：移动到文件的开头。

  `.：移至最后一次编辑。

- 删除和撤销（删除的文本存储在准备好粘贴回文档的缓冲区内）：

  x：将删除一个字符。

  d：开始删除操作。

  dw：将删除一个单词。

  d0：将删除到一行的开头。

  d$：将删除到行尾。

  dgg：将删除到文件的开头。

  dG：将删除到文件末尾。 

  u：将撤消最后一个操作。

  Ctrl-r：将重做最后一次撤消。

- 查找和替换：

  /text：搜索text文本。

  ?text：反向搜索text文本。

  n：再次查找上一次搜索的单词。

  N：反向再次查找上一次搜索的单词。

  :%s/ text / replacement text /g：在整个文档中搜索text文本并将其替换为替换文本。

  :%s/ text / replacement text /gc：在替换文本之前，搜索整个文档并确认。 

- 复制和粘贴



## Python

### NumPy

- import numpy as np：导入numpy库

- np.array([1, 2, 3, ...])：创建并初始化一个数组

  np.zeros((m, n))：创建m行n列的全0数组

  np.ones((m, n))：创建m行n列的全1数组

  np.arange(m, n)：创建一个从m到n的步长为1的递增或递减数列

  np.linspace(m, n, s)：创建一个从m到n的元素个数为s的等间距数组

  np.random.rand(m, n)：创建一个m行n列的随机数组

- a.shape：获取数组尺寸(m, n)

- 数组默认的类型为浮点型

  a = np.zeros((m, n), dtype = np.uint32 )：创建指定类型的数组

  b = a.astype(int)：转换数组数据类型:

- 两个相同尺寸的数组间可直接运算，同位置的数组元素直接运算

  np.dot(a, b)：a、b向量进行点乘运算

  a@b：矩阵的乘法运算

  np.sqrt(a)：对数组元素依次求平方根

  np.sin(a)、np.cos(a)：对数组元素依次进行三角函数运算

  np.log(a)、np.power(a, n)：对数组元素依次进行对数、指数运算

  a*n：数组与数单独运算，数组元素分别对这个数求积

  不同尺寸数组也可以运算。运算前会进行自我行/列复制至尺寸相同。

- a.min()、a.max()：返回数组最小、最大的元素

  a.argmin()、a.argmax() ：返回数组最小、最大元素的索引

- a.sum()：返回所有数组元素的总和

  a.mean()：返回所有数组元素的平均值

  a.median()：返回所有数组元素的中值

  a.var()：返回所有数组元素的方差

  a.std()：返回所有数组元素的标准方差

- 多维数组的数学运算：a.sum(axis = n)： axis代表维度。n=1时为行，逐行运算；n=2时为列，逐列运算...

- a[i, j]：获取数组第i行j列的元素

  a[逻辑运算符表达式]：筛选并获取符合条件的数组元素

  切片：a[0, 0:2]：获取数组第0行，[0, 2)列的数组元素

  ​           a[0, : ] / [0]：获取数组第0行，所有列的数组元素

  ​           a[m: n: s]：获取从m开始到n结束，跨度为s的数组元素（每隔s个取一个）（跨度可以为负）

  ​           a[: : -1]：获取逆序数组

  ​           a[: : -1, : , : ]：获取第一个维度逆序，其他维度不变的数组

  

### Matplotlib

- import matplotlib.pyplot as plot

  import numpy as np

#### 基本使用

- 定义数据：

  x = np.linspace(m, n, s)：创建一个从m到n的元素个数为s的等间距x数组

  y = f(x)

- 定义窗口：plt.figure(num = n, figsize = (x, y))：定义一个图像窗口，以下在定义新的图像窗口前，均为对当前窗口操作。参数num为窗口编号，参数figsize为窗口大小。

- 画曲线：plt.plot(x, y, color = 'red', linewidth = 1.0, linestyle = '--')：画出(x, y)曲线。参数color为线条颜色，参数linewidth为线宽，参数linestyle为线条样式。

- 显示图像：plt.show()：显示图像

- 设置坐标轴：

  plt.xlim((-1, 2)) / plt.ylim((-1, 2))：设置坐标轴范围

  plt.xlabel('text') / plt.ylabel('text')：设置坐标轴名称

  newticks = np.linspace(m, n, s)
  print(newticks)
  plt.xticks(newticks)：设置坐标轴刻度
  
  plt.xticks([1, 2, 3, ...] [r'$text1$'...])：设置坐标轴刻度及名称，名称与刻度一一对应，$符号转换字体，转义字符显示空格及其他字符，r为正则表达式。
  
  plt.xticks(())：隐藏坐标轴。
  
  

### PyQt5



## C++

#### 基础知识

##### 头文件

- 不以.c结尾：cmath、cstdio、cstring、iostream。

##### 名字空间

- namespace ns{}：名字空间，防止同名冲突。通过::运算符限定属于哪个namespace。

  有3种方法使用名字空间X的名字name：using namespace X：引入整个名字空间，使用时不再用::限制；using X::name：使用空间中的单个名字；X::name：程序中需加上名字空间前缀。

  using namespace std：使用标准名字空间std中所有名字。

##### 标准输入输出

- cout：标准输出流（屏幕窗口），cout << "text" << endl;。
- cin：标准输入流（键盘），cin >> a;。

##### 别名

- 引用类型：double &b = a;：b是a的别名。

  引用常用作函数形参，表示形参和实参是同一个对象（形参是实参的引用），则在函数中对形参的修改也就是对实参的修改：void fun(int &x, int &y) {} / fun(a, b);。若用const修改符修饰引用，如void fun(const int &x, int &y)，则函数中x不可被修改。

##### 内联函数

- inline double distance(double a, double b) {return ...}：类似宏定义，将函数直接替换为函数内语句展开，避免函数调用开销。

##### try-catch

- try-catch异常情况处理：try {throw x} catch (int result) { } catch (char * s){ }：正常代码放在try块，try通过throw抛出异常；catch中定义形参，捕获try块抛出的异常。

##### 重载

- 函数重载：C++允许函数同名，只要它们的形参不同，则在调用该名称函数时会自动识别形参类型，调用合适的函数。

- 运算符重载：重新定义运算，方便特殊类型的变量进行运算。

  [返回值类型] operator [原运算符] (参数1, 参数2) {
      [运算]
  	return [返回值];
  }

##### 模板函数

- 模板函数：通过模板函数，自动生成一个针对T类型的具体函数。

  ```c++
  template<class T1, class T2>
  	T1 minValue(T1 a, T2 b) {
  	if (a < b) return a;
  	else return (T2)b;
  }
  ```

##### 动态内存分配

- new：自动分配数个一定大小的内存块，返回连续内存的起始地址。如dp = new double[5];。
- delete[]：释放dp指向的多个double元素占据的内存块。若无[]，只释放第一个元素的内存块。

##### 类

- struct与class区别： class 类中的成员默认 private ，struct 结构体中的成员默认 public；class 继承默认 private 继承，而 struct 继承默认是 public 继承；class 可使用模板， struct 不能。

###### struct类

- struct类定义：

  ```c++
  struct Date {
  	int d, m, y;
  	void init(int dd, int mm, int yy) {
  		d = dd; m = mm; y = yy;
  	}
  	void print() {
  		cout << y << "-" << m << "-" << d << endl;
  	}
  };
  ```

- struct类使用：

  Date day;：创建Date类型的day对象。

  day.init(4, 6, 1999);：通过对象day调用类Date的init方法。

###### class类

- class类定义：

  ```c++
  class Student {
  private:    //使用public和private关键字设置访问限制
  	char *name;  //类的属性
  	int age;
  public:
  	Student(char *n = "no name", int a = 0) {  //构造函数
  		name = new char[100];
  		strcpy(name, n);
  		age = a;
  	}
  	virtual ~Student() { //析构函数
  		delete name;
  	}
  }
  ```

###### 构造函数与析构函数

- 构造函数：和类名同名且无返回类型的函数，在定义对象时会自动被调用，用于初始化类对象成用。

  - 构造函数定义：

  ```c++
  Date(int dd =1, int mm =1, int yy =1) {
  	d = dd; m = mm; y = yy;
  	cout << "构造函数" << endl;
  }
  ```

  - 构造函数使用：

    ```c++
    Date day(1, 1, 1);
    ```

  - 拷贝构造：用一个对象给另一个对象初始化：student s;  student m(s);

    拷贝构造函数：

    ```c++
    student(const student &s) { //拷贝构造函数
    	name = new char[100];
    	strcpy(name, s.name);
    	age = s.age;
    }
    ```

- 析构函数：在类对象销毁时被自动调用，用于释放该对象占用的资源，如释放占用的内存、关闭打开的文件。

  virtual ~Date() { }：析构函数名由~和类名组成，不带参数，无返回类型。

###### 类的成员函数的体外定义

- 类的成员函数可在类的定义外定义，必须在类定义中声明，且体外定义时应有类作用域：void Date::print() {}。

###### 类模板

- 将原类定义中所有类型改为T，并加上模板头template<class T>。

###### 类继承

- 

###### 虚函数

- 

##### 函数自引用

- this指向调用这个函数的类型对象指针，*this为调用这个函数的那个对象，即调用这个函数的对象本身。

  通过返回自引用return *this，可连续调用对象的函数，如day.add(3).add(7);。

##### 容器Vector

##### 其他

- 用程序块{ }形成内部作用域，可定义域外部作用域同名的变量，在该块里隐藏外部变量。
- 访问和内部作用域变量同名的全局变量，要用全局作用域限定符 ::
- 默认形参：函数的形参可带有默认值，但必须在最右边。
- string类：string s2("text"); / string s3(s1);：使用构造函数定义字符串变量，可以赋初值。

## ROS

### ROS常用命令及知识

- $ roscore：启动ROS master。

- $ rosnode list：显示当前正在运行的ROS节点信息。

  $ rosnode info [node_name]：显示某个指定节点的信息

- $ rosrun [package_name] [node_name]：运行指定包中的指定节点。

- $ rospack find [package_name]：获取软件包有关信息，find参数返回软件包所在路径。

- $ roscd [locationname[/subdir]]：直接切换目录到某个软件包或软件包子目录中。

  $ roscd log：切换目录至ROS日志文件的目录。

- $ rosls [locationname[/subdir]]：显示指定目录内容。

- TAB补全：当按TAB键后，命令行会自动补充剩余部分。

- 创建工作空间：

  $ mkdir -p ~/workspace_name/src

  $ cd ~/workspace_name/src

  $ catkin_init_workspace：初始化工作空间文件夹

  $ catkin_init_workspace install：创建安装文件夹

  编译工作空间：

  $ cd ~/workspace_name/

  $ catkin_make

  设置环境变量：$ source devel/setup.bash

  检查环境变量：$ echo $ROS_PACKAGE_PATH

- 创建功能包：

  $ cd ~/workspace_name/src

  $ catkin_create_pkg <package_name> [depend1] [depend2] ...

  编译功能包：

  $ cd ~/workspace_name/

  $ catkin_make

  $ source devel/setup.bash

- $ roslaunch [package] [filename.launch]：启动定义在指定package功能包中的launch。

  <launch></launch>：根元素

  <node>：启动节点。pkg：节点所在功能包名称；type：节点可执行文件名称；name：节点运行时的名称。

  <param>：设置ROS运行系统中的参数，存储在参数服务器中。name：参数名；value：参数值。

  <rosparam>：加载参数文件中所有参数，存储在参数服务器中。file：文件路径。

  <arg>：launch文件内部局部变量。name：参数名；value：参数值。调用：value="$(arg arg_name)"。

  <remap>：重映射ROS计算图资源命名。from：原命名；to：映射之后的命名。

  <include>：包含其他launch文件。file：文件路径。

- 创建发布者publisher代码：

  初始化ROS节点->向ROS Master注册节点信息->创建消息数据->按照一定频率循环发布消息

  ```c++
  #include "ros/ros.h"    //包含头文件
  #include "std_msgs/String.h"
  #include <sstream>
  
  int main(int argc, char **argv){
      ros::init(argc, argv, "file_name");    //初始化ROS
      ros::NodeHandle n;    //为节点创建句柄
      ros::Publisher topic_pub = n.advertise<std_msgs::String>("topic_name", 1000);    //向ROS Master注册节点信息，包括发布的话题名、话题中的消息类型和队列大小
      ros::Rate loop_rate(10);    //指定循环发布的频率
      int count = 0;
      while (ros::ok()){
          std_msgs::String msg;    //创建一个消息
          std::stringstream ss;
          ss << "hello world " << count;
          msg.data = ss.str();
          ROS_INFO("%s", msg.data.c_str());    //输出有关信息
          topic_pub.publish(msg);    //把信息广播给已连接的节点
          
          ros::spinOnce();    //调用回调函数
          loop_rate.sleep();    //使用sleep方法等待一定时间，以达到设定的发布速率
          ++count;
      }
      return 0;
  }
  ```

  配置CMakeList.txt中编译规则：

  add_executable(node_name src/node_name.cpp)

  Target_link_libraries(node_name ${catkin_LIBRARIES})

- 创建订阅者subscriber代码：

  初始化ROS节点->订阅需要的话题->循环等待话题消息，接收到消息后进入回调函数->在回调函数中完成消息处理

  ```c++
  #include "ros/ros.h"
  #include "std_msgs/String.h"
  
  void topicCallback(const std_msgs::String::ConstPtr& msg){    //回调函数，当有新消息到达话题时被调用
      ROS_INFO("I heard: [%s]", msg->data.c_str());
  }
  
  int main(int argc, char **argv){
      ros::init(argc, argv, "listener");
      ros::NodeHandle n;
      ros::Subscriber sub = n.subscribe("topic_name", 1000, topicCallback);    //订阅topic话题，每当有新消息到达时，ROS调用回调函数，第二个参数是队列大小
      ros::spin();    //启动自循环，等待调用回调函数
      return 0;
  }
  ```

- 创建服务端server代码：

  初始化ROS节点->创建server实例->循环等待服务请求，进入回调函数->在回调函数中完成服务功能的处理，并反馈应答数据

  ```c++
  #include "ros/ros.h"
  #include "beginner_tutorials/AddTwoInts.h"
  
  bool pubCommand = false;
  
  bool commandCallback(std_srvs::Trigger::Request  &req, std_srvs::Trigger::Response &res){
      ROS_INFO("Publish turtle velocity command [%s]", pubCommand==true?"Yes":"No");    //显示请求数据
  
    	res.success = true;   	//设置反馈数据
  	  res.message = "Change turtle command state!"
      return true;
  }
  
  int main(int argc, char **argv){
      ros::init(argc, argv, "add_two_ints_server");
      ros::NodeHandle n;
  
      ros::ServiceServer service = n.advertiseService("/spawn", commandCallback);    //创建一个名为service的实例，注册回调函数commandCallback
      ROS_INFO("Ready to add two ints.");
      //循环等待回调函数
      ros::Rate loop_rate(10);
    
      while(ros::ok()){
          ros::spinOnce();
  		    if(pubCommand){    //如果标志为true则发布指令
  			      geometry_msgs::Twist vel_msg;
  			      vel_msg.linear.x = 0.5;
  			      vel_msg.angular.z = 0.2;
  			      turtle_vel_pub.publish(vel_msg);
  		    }
  	      loop_rate.sleep();    //按照循环频率延时
      }
  
      return 0;
  }
  ```

- 创建客户端client代码：

  初始化ROS节点->创建一个client实例->发布服务请求数据->等待server处理后的应答结果

  ```c++
  #include "ros/ros.h"
  #include "beginner_tutorials/AddTwoInts.h"
  #include <cstdlib>
  
  int main(int argc, char **argv){
      ros::init(argc, argv, "add_two_ints_client");
      ros::NodeHandle n;
    
      ros::service::waitForService("/spawn")    //发现/spawn服务
      ros::ServiceClient client = n.serviceClient<beginner_tutorials::AddTwoInts>("service_name");    //为服务创建一个客户端，并连接名为service_name的服务
      beginner_tutorials::AddTwoInts srv;    //初始化一个服务类，并赋值
      srv.request.a = atoll(argv[1]);
      srv.request.b = atoll(argv[2]);
      if (client.call(srv)){    //调用服务，直到调用完成后返回
          ROS_INFO("Sum: %ld", (long int)srv.response.sum);
      }
      else{
          ROS_ERROR("Failed to call service add_two_ints");
          return 1;
      }
    
      return 0;
  }
  ```

- $ rosrun rqt_graph rqt_graph：用动态图显示系统中正在发生的事情。

- $ rostopic：获取ROS话题信息。

  $ rostopic echo [topic]：显示在某个话题上发布的数据。

  $ rostopic list ：列出当前已被订阅和发布的所有话题。

  $ rostopic type [topic]：查看所发布话题的消息类型

  $ rostopic pub [-r f] [topic] [msg_type] [args]：把数据发布到当前正在广播的话题上，-r f表示以每分钟f次循环。

  $ rostopic hz [topic]：查看数据发布的频率。

  $ rosrun rqt_plot rqt_plot：在滚动时间图上显示发布到某个话题上的数据。

- $ rosservice：通过服务附加到ROS客户端/服务器框架上。

  $ rosservice list：输出活跃服务的信息。

  $ rosservice call [service] [args]：用给定参数调用指定服务。

  ​		$ rosservice call /clear：清屏。

  $ rosservice type [service]：输出指定服务的类型。

  $ rosservice find：按服务的类型查找服务。

  $ rosservice uri：输出服务的ROSRPC uri。

- $ rosparam：让我们在ROS参数服务器上存储和操作数据。

  $ rosparam list：列出节点的参数名。

  $ rosparam set [param_name]：设置指定参数的参数值。

  $ rosparam get [param_name]：获取指定参数的参数值。

  $ rosparam load [file_name] [namespace]：从指定文件中加载参数。

  $ rosparam dump [file_name] [namespace]：向指定文件中写入参数。

  $ rosparam delete：删除参数。

### 常用可视化工具箱

- QT工具箱rqt：

  $ rosrun rqt：打开rqt工具箱。

  $ rosrun rqt_console rqt_console：连接到ROS日志框架，以显示节点输出信息。

  $ rosrun rqt_logger_level rqt_logger_level：允许我们在节点运行时改变输出信息的详细级别。

  $ rosrun rqt_graph rqt_graph：计算图可视化工具。

  $ rosrun rqt_plot rqt_plot：数据绘图工具。

  $ rosrun rqt_image_view rqt_image_view：图像渲染工具（摄像头）。

- Rviz工具箱：三维数据可视化工具

  $ roserun rviz rviz：打开rviz工具箱。

- Gazebo工具箱：三维物理仿真平台

  $ roslaunch gazebo_ros：打开gazebo工具箱。
  
  

## OpenCV

#### 图像操作

##### 图像读写及基本操作

- cv2.imread('picture.jpg', 0)：加载图片

  参数1：图片的文件名。

  参数2：读入方式，省略即采用默认值。cv2.IMREAD_COLOR：彩色图，默认值(1)；cv2.IMREAD_GRAYSCALE：灰度图(0)；cv2.IMREAD_UNCHANGED：包含透明通道的彩色图(-1)

- cv2.imshow(’window_name‘,img)：显示图片

  参数1：窗口名称；参数2：要显示的图片变量

- cv2.imwrite('picture.jpg', img, save_type)：保存图片。参数1位包含后缀名的文件名，参数2为图片变量，参数3为保存质量。

- cv2.waitKey(n)：程序等待。参数为等待毫秒数，若为传入0则一直等待，可以通过k = cv2.waitKey(0)获取键盘输入。

- cv2.namedWindow(’window_name‘, cv2.WINDOW_NORMAL)：创建一个窗口。参数1是窗口名称，参数2默认是cv2.WINDOW_AUTOSIZE，表示窗口大小自适应图片；也可设置为cv2.WINDOW_NORMAL，表示窗口大小可调整。

- px = img[m,n]：通过行列坐标来获取像素点的值，返回值为BGR的列表，m为行号n为列号。

  img[m,n] = [b, g, r]：通过行列坐标来设置像素点的值。

- img.shape()：获取图像形状，返回包含行数（高度）、列数（宽度）和通道数的元组。

- Img.dtype()：获取图像数据类型。

- Img.size()：获取图像总像素数。

- b, g, r = cv2.split(img)：分开访问图像的BGR三通道。

  img = cv2.merge((b, g, r))：将单独的BGR三通道合一为一个图像。

  b = img[:, :, 0]：提取BGR通道。img列表参数1、2为行列，参数3为通道（0b，1g，2r）。

##### 颜色转换

- cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)：转换颜色。参数1为图片变量，参数2为转换方式。

  ​	cv2.COLOR_BGR2GRAY：彩色图转成灰度图

  ​	cv2.COLOR_BGR2HSV：将彩色图转化为HSV

##### 阈值分割

- cv2.inRange(img, lower, upper)：将图像实现二值化，阈值内像素设置为白色，阈值外像素设置为黑色。参数1为要处理的图像变量，参数2位下边界，参数3位上边界。

- ret, th = cv2.threshold(img, lower, upper, type)：实现阈值分割。

  返回值ret为当前阈值，th为处理后的图像。

  参数1为图像变量（一般为灰度图）

  参数2为下阈值，参数3位上阈值（一般为255）

  参数4为阈值方式：

  ​	cv2.THRESH_BINARY：高于阈值的设为黑色，低于的设为白色；

  ​    cv2.THRESH_BINARY_INV：高于阈值的设为白色，低于的设为黑色；	

  ​	cv2.THRESH_TRUNC：高于阈值部分不变，低于部分设为阈值；

  ​	cv2.THRESH_TOZERO：高于阈值部分设为黑色，低于部分不变；

  ​	cv2.THRESH_TOZERO_INV：高于阈值部分不变，低于部分设为黑色。

  ​	cv2.THRESH_OTSU：使用Otsu算法计算阈值。使用Otsu算法前先进行滤波。

- th2 = cv2.adaptiveThreshold(img, upper, cv2.ADAPTIVE_THRESH_MEAN_C, cv2.THRESH_BINARY, 11, 4)：自适应阈值，每次取图像小部分计算，适用于明暗分布不均的图片。

  参数1为图像变量，参数2为最大阈值

  参数3为小区域内阈值计算方式：

  ​	cv2.ADAPTIVE_THRESH_MEAN_C：小区域内取均值

  ​	cv2.ADAPTIVE_THRESH_GAUSSIAN_C：小区域内加权求和

  参数4为阈值方法，只能使用THRESH_BINARY、THRESH_BINARY_INV

  参数5为小区域的边长

  参数6：最终阈值等于小区域计算出的阈值减去此值

##### 图像几何变换

- roi = img[m:n , p:q]：截取(m,n)到(p,q)矩形范围部分的图像。

- cv2.resize(img, output, size, fx, fy, interpolation)：图片缩放。

  参数1为图片变量，参数2为输出图片变量

  参数3位输出图片尺寸，参数4为沿x、y轴缩放系数

  参数5为插入方式：

  ​	cv2.INTER_NEAREST：最近邻插值

  ​	cv2.INTER_LINEAR：双线性插值（默认）

  ​	cv2.INTER_AREA：使用像素区域关系进行重采样

  ​	cv2.INTER_CUBIC：4×4像素邻域双三次插值

  ​	cv2.INTER_LANCZOS4：8×8像素邻域的Lanczos插值

- cv2.flip(img, 0)：图片翻转。参数1为图片变量；参数2=0为垂直翻转，>0为水平翻转，<0位中心对称翻转。

- cv2.warpAffine(img, M, (cols, rows))：图片仿射变换。参数1为图片变量，参数2为变换矩阵，参数3为输出图片大小。

  M = np.float32([[1, 0, tx], [0, 1, ty]])：生成平移变换矩阵，tx、ty为x、y轴平移距离。

  M = cv2.getRotationMatrix2D((cols / 2, rows / 2), 45, 0.5)：生成旋转变换矩阵。参数1为图片旋转中心，参数2为图片旋转角度（正为逆时针），参数3为缩放比例。

- cv2.warpPerspective(img, M, (w, h))：图片透视变换。参数1为图像变量，参数2为变换矩阵，参数3为生成目标图像大小。

  M = cv2.getPerspectiveTransform(pts1, pts2)：生成透视变换矩阵。参数1为原图四个顶点坐标的矩阵，参数2为目标图片四个顶点坐标的矩阵。

  ```python
  例：# 原图中卡片的四个角点
  pts1 = np.float32([[148, 80], [437, 114], [94, 247], [423, 288]])
     # 变换后分别在左上、右上、左下、右下四个点
  pts2 = np.float32([[0, 0], [320, 0], [0, 178], [320, 178]])
  ```

##### 图像叠加

- cv2.add(x, y)：叠加两张大小和通道数相同的图像。

  cv2.addWeighted(img1, a, img2, b, c)：按照权重叠加两张大小和通道数相同的图像，dst=a×img1+b×img2+c。

- cv2.bitwise_and(img1, img2, mask)：对图像进行按位与运算。参数1、2为输入图像变量，参数3为图像掩膜。

  创建掩膜，并覆盖在图片的一部分上：

  ```python
  img1 = cv2.imread('lena.jpg')
  img2 = cv2.imread('opencv-logo-white.png')
  
  # 把logo放在左上角，所以我们只关心这一块区域
  rows, cols = img2.shape[:2]    #图片2的长宽
  roi = img1[:rows, :cols]    #剪下图片1中左上角等于图片2大小的部分
  # 创建掩膜
  img2gray = cv2.cvtColor(img2, cv2.COLOR_BGR2GRAY)    #图像2转化为灰度图
  ret, mask = cv2.threshold(img2gray, 10, 255, cv2.THRESH_BINARY)    #图像2转化为黑白图即掩膜1
  mask_inv = cv2.bitwise_not(mask)    #创造图片2自身的掩膜2（黑白反色）
  # 保留除logo外的背景
  img1_bg = cv2.bitwise_and(roi, roi, mask)    #掩膜1覆盖在图片1剪切部分
  img2_bg = cv2.bitwise_and(img2, img2, mask_inv)    #掩膜2覆盖在图片2上
  dst = cv2.add(img1_bg, img2)    #掩膜覆盖后的图片1与覆盖后的图片2融合
  img1[:rows, :cols] = dst    #融合后将剪切部分恢复到原图上
  ```

  cv2.bitwise_not()，cv2.bitwise_or()，cv2.bitwise_xor()：执行按位或/非/异或运算

##### 图像滤波

- cv2.blur(img, (x, y))：均值滤波，取卷积核区域内元素的均值。参数1为图像变量，参数2为卷积核大小。
- cv2.boxFilter(img, -1, (x, y), normalize=True)：方框滤波，取卷积核区域内的像素和。参数1为图像变量，参数3为卷积核大小，参数4为状态，normalize=True时为均值滤波，normalize=False时为方框滤波。

- cv2.GaussianBlur(img, (x, y), sigmaX)：高斯滤波，取卷积核内部按正态分布的加权平均值。参数1为图像变量，参数2为卷积核大小，参数3为正态分布中的σ。

- cv2.medianBlur(img, d)：中值滤波，将方框内元素比较，取中值为当前值。参数1为图像变量，参数2为方框边长。

- cv2.bilateralFilter(img, d, sigmacolor, sigmaspace)：双边滤波，在高斯滤波过程中考虑不融合、保留线条边缘信息。参数1为图像变量，参数2为方框边长，参数3为空间高斯函数标准差，参数4为灰度值相似性高斯函数标准差。

- 优先高斯滤波cv2.GaussianBlur()，然后均值滤波cv2.blur()。

  斑点和椒盐噪声优先使用中值滤波cv2.medianBlur()。

  要去除噪点的同时尽可能保留更多的边缘信息，使用双边滤波cv2.bilateralFilter()。

  线性滤波方式：均值滤波、方框滤波、高斯滤波（速度相对快）。

  非线性滤波方式：中值滤波、双边滤波（速度相对慢）。

##### 边缘检测

- cv2.Canny(img, lower, upper)：边缘检测。参数1为图像变量，参数2、3为最低、高阈值。

  推荐先进性阈值分割（Otsu）再边沿检测。

##### 轮廓与轮廓特征

- image, contours, hierarchy = cv2.findContours(thresh, cv2.RETR_TREE, cv2.CHAIN_APPROX_SIMPLE)：寻找轮廓。

  返回值1为原图，返回值2为轮廓间的层级关系，参数3为找到的轮廓（数组存储坐标形式）。

  参数1为阈值分割二值化后的图像变量；参数2为轮廓查找方式，一般使用cv2.RETR_TREE，表示提取所有的轮廓并建立轮廓间的层级；参数3为轮廓的近似方法，使用cv2.CHAIN_APPROX_SIMPLE就表示用尽可能少的像素点表示轮廓。

- cv2.drawContours(img, contours, -1, (b, g, r), thickness)：绘制轮廓。参数1为要绘制的图像变量，参数2为轮廓间的层级关系，参数3为-1表示绘制所有轮廓，参数4为轮廓颜色bgr值，参数5为线宽。

- cv2.countNonZero(cnt)：求轮廓面积（像素点个数）。参数1为轮廓坐标数组。

- cv2.arcLength(cnt, True)：求轮廓周长。参数1为轮廓坐标数组，参数2表示轮廓是否封闭。

- x, y, w, h = cv2.boundingRect(cnt)：求轮廓的外接矩形。返回值分别为矩形左上角坐标和矩形宽高。参数1为轮廓坐标数组。

  cv2.rectangle(img_color1, (x, y), (x + w, y + h), (b, g, r), thickness)：绘制出轮廓外接矩形。

- rect = cv2.minAreaRect(cnt)：寻找轮廓外接最小矩形。参数1为轮廓坐标数组。

  box = np.int0(cv2.boxPoints(rect)) ：矩形的四个角点坐标取整。cv2.drawContours(img_color1, [box], -1, (b, g, r), thickness)：绘制轮廓外接最小矩形。参数1为目标图像变量，参数2为矩形轮廓列表，参数3为-1表示绘制列表中所有轮廓。

- (x, y), radius = cv2.minEnclosingCircle(cnt)：寻找轮廓最小外接圆。参数1为轮廓坐标数组。

  (x, y, radius) = np.int0((x, y, radius))： 圆心和半径取整。

  cv2.circle(img_color2, (x, y), radius, (b, g, r), thickness)：绘制轮廓外接最小外接圆。参数1为目标图像变量，参数2、3为圆心位置与半径。

- ellipse = cv2.fitEllipse(cnt)：寻找轮廓拟合椭圆。参数1为轮廓坐标数组。

  cv2.ellipse(img_color2, ellipse, (b, g, r), thickness)：绘制轮廓拟合椭圆。参数1为目标图像变量，参数2为椭圆变量。

- cv2.matchShapes(cnt_a, cnt_b, method, 0.0)：比较两个形状之间的相似度，返回值越小，越相似。参数1、2为两个形状的轮廓坐标数组，参数3为匹配方法。

- cv2.approxPolyDP(cnt, epsilon, close)：多边形轮廓逼近。参数1为轮廓坐标数组；参数2表示多边形轮廓接近实际轮廓的程度，值越小越精确；参数3表示轮廓是否闭合。

- cv2.convexHull(cnt)：寻找轮廓凸包。返回值为凸包顶点坐标列表，参数1为轮廓坐标数组。

- cv2.pointPolygonTest(cnt, (x, y), True)：计算点到轮廓的最短距离。参数1为轮廓坐标数组；参数2为点坐标，参数3为True时表示计算距离（点在轮廓外为负，在内为正），为False时只返回-1/0/1表示相对轮廓位置，不计算距离。

##### 腐蚀与膨胀

- cv2.erode(img, kernel)：对二值化图像白色部分进行腐蚀。参数1为图像变量，参数2为用于腐蚀的结构元素。可使用kernel = np.ones((d, d), np.uint8)创建结构元素。
- cv2.dilate(img, kernel)：对二值化图像白色部分进行膨胀。参数1为图像变量，参数2为用于膨胀的结构元素。
- cv2.morphologyEx(img, cv2.MORPH_OPEN, kernel)：开运算（先腐蚀后膨胀），消除物体外的小白点。参数1为图像变量，参数2为开/闭运算状态，参数3为结构元素。
- cv2.morphologyEx(img, cv2.MORPH_CLOSE, kernel)：闭运算（先膨胀后腐蚀），消除物体内的小白点。参数1为图像变量，参数2为开/闭运算状态，参数3为结构元素。

##### 直方图

- cv2.calcHist([img], channels, mask, histSize, ranges)：计算直方图。参数1为图像变量（以方括号传入），参数2为图像通道数（灰度图为[0]，彩色图B/G/R分别传入[0]/[1]/[2]），参数3为要计算的区域（计算整幅图的为None），参数4为直方图子区段数目，参数5为要计算的像素值范围。

  ```python
  hist = cv2.calcHist([image],[0],None,[256],[0,256])    #灰度图，传入一个通道
  hist= cv2.calcHist([chans[0],chans[2]],[0,1],None,[32,32],[0,256,0,256])    #BG图，传入两个通道
  ```

- Matplotlib绘制直方图：

  ```python
  plt.hist(img.ravel(), 256, [0, 256])    #计算并绘制直方图
  或者 plt.plot(hist)    #用上文的计算结果绘制
  plt.show()
  ```

- cv2.equalizeHist(img)：直方图均衡化。参数1为图片变量。

  cv2.createCLAHE(clipLimit=2.0, tileGridSize=(8, 8))：对比度受限的自适应直方图均衡化。参数1为颜色对比度的阈值；参数2为进行像素均衡化的网格大小。

##### 模板匹配

- cv.matchTemplate( img, templ, result, match_method)：模板匹配。

  参数1为原始图像变量，参数2为模板图像变量

  参数3为目标存放矩阵，矩阵每个位置都存有匹配值（最白的地方表示匹配程度最高）。

  参数4为匹配方法：

  ​    CV_TM_SQDIFF：平方差匹配，越小越好

  ​    CV_TM_SQDIFF_NORMED：标准平方差匹配，越小越好

  ​    CV_TM_CCORR：相关匹配（乘法操作），越大越好

  ​    CV_TM_CCORR_NORMED：标准相关匹配，越大越好

  ​    CV_TM_CCOEFF：相关匹配（先减去平均值），越大越好

  ​    CV_TM_CCOEFF_NORMED：标准相关匹配，越大越好

- min_val, max_val, min_loc, max_loc = cv2.minMaxLoc(result, minVal, maxVal, minLoc, maxLoc, Mat())：确定矩阵最大值和最小值的位置。参数1为匹配结果矩阵，参数2、3为在矩阵中存储的最小值和最大值，参数4、5为矩阵中最大值和最小值的坐标，参数6为可选的掩膜。

- 画出矩形：

  ```python
  left_top = max_loc  #左上角
  right_bottom = (left_top[0] + w, left_top[1] + h)  #右下角
  cv2.rectangle(img, left_top, right_bottom, 255, 2)  #画出矩形
  ```

- 匹配多个物体：设定一个匹配阈值，输出所有高于阈值的匹配结果。

  ```python
  loc = np.where(res >= threshold)  # 匹配程度大于threshold的坐标y，x
  for pt in zip(*loc[::-1]):  #loc[::-1]逆序矩阵，zip函数转置矩阵
      right_bottom = (pt[0] + w, pt[1] + h)
      cv2.rectangle(img_rgb, pt, right_bottom, (0, 0, 255), 2)
  ```

##### 霍夫变换

- 标准霍夫直线变换（整条直线）：lines = cv2.HoughLines(edges, 0.8, np.pi / 180, 90)。

  返回值为每行2个元素的列表。

  参数1为图像变量（一般为阈值分割或边沿检测后的图）；参数2为距离r的精度，越大考虑的线越多；参数3为角度θ的精度，越小考虑的线越多；参数4为相同点的累加数阈值，值越小，考虑的线越多。

  绘制标准霍夫直线变换的直线：（极坐标）

  ```python
  for line in lines:
      rho, theta = line[0]
      a = np.cos(theta)
      b = np.sin(theta)
      x0 = a * rho
      y0 = b * rho
      x1 = int(x0 + 1000 * (-b))
      y1 = int(y0 + 1000 * (a))
      x2 = int(x0 - 1000 * (-b))
      y2 = int(y0 - 1000 * (a))
      cv2.line(drawing, (x1, y1), (x2, y2), (0, 0, 255))
  ```

- 统计概率霍夫变换（部分直线）：lines = cv2.HoughLinesP(edges, 0.8, np.pi / 180,  90, minLineLength=50, maxLineGap=10)。

  返回值为每行4个元素x1、y1、x2、y2的列表。

  参数1为图像变量；参数2为距离r的精度，越大考虑的线越多；参数3为角度θ的精度，越小考虑的线越多；参数4为相同点的累加数阈值，值越小，考虑的线越多；参数5为最短长度阈值，比该长度短的线会被排除；参数6为同一直线两点之间的最大距离。

  绘制统计概率霍夫直线变换的直线：

  ```python
  for line in lines:
      x1, y1, x2, y2 = line[0]
      cv2.line(drawing, (x1, y1), (x2, y2), (0, 255, 0), 1, lineType=cv2.LINE_AA)
  ```

- 霍夫圆变换：circles = cv2.HoughCircles(edges, cv2.HOUGH_GRADIENT, 1, 20, param2=30)。

  返回每行3个元素x，y，r的列表。

  参数1为图像变量；参数2为变换方法，一般使用霍夫梯度法cv2.HOUGH_GRADIENT；参数3dp=1，表示霍夫梯度法中累加器图像的分辨率与原图一致；参数4为两个不同圆圆心最短距离；参数5为相同点的累加数阈值，值越小，考虑的圆周越多。

  绘制霍夫圆变换的圆：

  ```python
  for i in circles[0, :]:
      cv2.circle(drawing, (i[0], i[1]), i[2], (0, 255, 0), 2)  # 画出外圆
      cv2.circle(drawing, (i[0], i[1]), 2, (0, 0, 255), 3)  # 画出圆心
  ```

##### Example：车道线识别

<img src="http://cos.codec.wang/cv2_lane_detection_roi_sample.jpg" alt="img" style="zoom:33%;" />

1. 灰度化

   ```python
   gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
   ```

2. 高斯滤波

   ```python
   blur_gray = cv2.GaussianBlur(gray, (blur_ksize, blur_ksize = 5), 1)
   ```

3. Canny边缘检测

   ```python
   edges = cv2.Canny(blur_gray, canny_lth = 50, canny_hth = 150)
   ```

   <img src="C:\Users\user\Desktop\cv2_lane_detection_canny_result.jpg" alt="cv2_lane_detection_canny_result" style="zoom: 33%;" />

4. 不规则ROI区域选取

   创建梯形的mask掩膜，与边缘检测结果图混合运算，掩膜中白色的部分保留，黑色的部分舍弃。

   ```python
   rows, cols = edges.shape
   points = np.array([[(0, rows), (460, 325), (520, 325), (cols, rows)]])    #标记四个坐标点用于ROI截取
   
   mask = np.zeros_like(img)    #创建掩膜
   cv2.fillPoly(mask, corner_points, 255)    #绘制多边形并填充
   masked_img = cv2.bitwise_and(img, mask)    #覆盖掩膜
   roi_edges = masked_img    #赋值给roi图
   ```

   <img src="http://cos.codec.wang/cv2_lane_detection_masked_roi_edges.jpg" alt="只保留关键区域的边缘检测图" style="zoom:33%;" />

5. 霍夫直线变换

   ```python
   #霍夫直线提取
   drawing, lines = hough_lines(roi_edges, rho = 1, theta = np.pi/180, threshold = 15, min_line_len = 40, max_line_gap = 20)
   
   def hough_lines(img, rho, theta, threshold, min_line_len, max_line_gap):
       # 统计概率霍夫直线变换
       lines = cv2.HoughLinesP(img, rho, theta, threshold, minLineLength=min_line_len, maxLineGap=max_line_gap)
       # 新建一副空白画布
       drawing = np.zeros((img.shape[0], img.shape[1], 3), dtype=np.uint8)
       # draw_lines(drawing, lines)     # 画出直线检测结果
       return drawing, lines
   
   def draw_lines(img, lines, color=[0, 0, 255], thickness=1):
       for line in lines:
           for x1, y1, x2, y2 in line:
               cv2.line(img, (x1, y1), (x2, y2), color, thickness)
   ```

   <img src="http://cos.codec.wang/cv2_lane_detection_hough_lines_direct_result.jpg" alt="霍夫变换结果图" style="zoom:33%;" />

6. 车道线计算：只得到左右两条车道线

   1. 根据斜率正负划分线是左车道还是右车道
   2. 迭代计算各直线斜率与斜率均值的差，排除掉差值过大的异常数据（第一次计算完斜率均值并排除掉异常值后，再在剩余的斜率中取均值，继续排除）
   3. 最小二乘法拟合左右车道线：拟合出一条直线f(xi)=axi+b，使得误差平方和最小E=∑(f(xi)−yi)^2。

   ```python
   draw_lanes(drawing, lines)  #车道拟合计算
   result = cv2.addWeighted(img, 0.9, drawing, 0.2, 0)  #将结果按权重叠加合在原图上
   
   #车道拟合计算
   def draw_lanes(img, lines, color=[255, 0, 0], thickness=8):
       # a.划分左右车道
       left_lines, right_lines = [], []
       for line in lines:
           for x1, y1, x2, y2 in line:
               k = (y2 - y1) / (x2 - x1)
               if k < 0:
                   left_lines.append(line)
               else:
                   right_lines.append(line)
       if (len(left_lines) <= 0 or len(right_lines) <= 0):
           return
   
       # b.清理异常数据
       clean_lines(left_lines, 0.1)
       clean_lines(right_lines, 0.1)
   
       # c.得到左右车道线点的集合，拟合直线(将所有端点表示成元组（x，y）的列表)
       left_points = [(x1, y1) for line in left_lines for x1, y1, x2, y2 in line]
       left_points = left_points + [(x2, y2) for line in left_lines for x1, y1, x2, y2 in line]
       right_points = [(x1, y1) for line in right_lines for x1, y1, x2, y2 in line]
       right_points = right_points + [(x2, y2) for line in right_lines for x1, y1, x2, y2 in line]
   
       left_results = least_squares_fit(left_points, 325, img.shape[0])
       right_results = least_squares_fit(right_points, 325, img.shape[0])
   
       # 注意这里点的顺序
       vtxs = np.array([[left_results[1], left_results[0], right_results[0], right_results[1]]])
       # d.填充车道区域
       cv2.fillPoly(img, vtxs, (0, 255, 0))
       # d.或者只画车道线
       # cv2.line(img, left_results[0], left_results[1], (0, 255, 0), thickness)
       # cv2.line(img, right_results[0], right_results[1], (0, 255, 0), thickness)
   
   # 迭代计算斜率均值，排除掉与差值差异较大的数据
   def clean_lines(lines, threshold):
       slope = [(y2 - y1) / (x2 - x1) for line in lines for x1, y1, x2, y2 in line]
       while len(lines) > 0:
           mean = np.mean(slope)
           diff = [abs(s - mean) for s in slope]
           idx = np.argmax(diff)
           if diff[idx] > threshold:
               slope.pop(idx)
               lines.pop(idx)
           else:
               break
   
   # 最小二乘法拟合
   def least_squares_fit(point_list, ymin, ymax):
       # 得到x、y的点列
       x = [p[0] for p in point_list]
       y = [p[1] for p in point_list]
   
       # np.polyfit：最小二乘多项式拟合。参数1、2为点列坐标，第参数3为拟合多项式的阶数（1代表线性）
       fit = np.polyfit(y, x, 1)  #polyfit返回值为系数列表
       fit_fn = np.poly1d(fit)  # 获取拟合的结果直线函数
   
       xmin = int(fit_fn(ymin))  #获取直线端点坐标
       xmax = int(fit_fn(ymax))
   
       return [(xmin, ymin), (xmax, ymax)]
   ```

   <img src="http://cos.codec.wang/cv2_lane_detection_result_sample.jpg" alt="img" style="zoom:33%;" />

   7. 摄像头/视频处理

   ```python
   capture = cv2.VideoCapture(0) #打开摄像头
   fourcc = cv2.VideoWriter_fourcc(*'MJPG')
   outfile = cv2.VideoWriter('output.avi', fourcc, 25., (640, 480))  #定义编码方式并创建VideoWriter对象
   
   while(True):
       ret, frame = capture.read()  # 获取一帧
       
       # 将这帧进行上述转换
       #......
       
       outfile.write(result)
       cv2.imshow('result', result)capture = cv2.VideoCapture(0) #打开摄像头
   fourcc = cv2.VideoWriter_fourcc(*'MJPG')
   outfile = cv2.VideoWriter('output.avi', fourcc, 25., (640, 480))  #定义编码方式并创建VideoWriter对象
   
   while(True):
       ret, frame = capture.read()  # 获取一帧
       
       # 将这帧进行上述转换
       #......
       
       outfile.write(result)
       cv2.imshow('result', result)
   ```

#### 摄像头/视频

- capture = cv2.VideoCapture(0)：创建VideoCapture对象，参数为摄像头编号，或视频的路径。

  capture.read()：获取一帧，返回两个参数。第一个返回参数为当前帧获取是否正确标志，第二个返回参数为当前帧的图像。

  capture.get(propId)：获取摄像头属性，参数为获取的属性名称。

  capture.set(propId, value)：设置摄像头属性，参数1为是属性名称，参数2为设定值。

- writer = cv2.VideoWriter('file_name.avi', fourcc, fps, (m,n) )：保存视频。参数1为包含后缀名的文件名，参数2位编码方式fourcc，参数3位帧率，参数4位分辨率大小。

  fourcc = cv2.VideoWriter_fourcc(*'MJPG')：指定视频编码方式fourcc。

#### 绘制图形

- 导入模块与通用代码：

  ```
  import cv2
  import numpy as np
  import matplotlib.pyplot as plt
  
  cv2.imshow('img', img)
  cv2.waitKey(0)
  ```

  img = np.zeros/ones((512, 512, 3), np.uint8)：创建一幅黑色/白色的图片。

- cv2.line(img, (x0, y0), (x1, y1), (b, g, r), thickness)：画直线。参数1为图片变量，参数2为起点，参数3为终点，参数4为颜色bgr值，参数5为线宽。

- cv2.rectangle(img, (x0, y0), (x1, y1), (b, g, r), thickness)：画矩形。参数1为图片变量，参数2为左上角坐标，参数3为右下角坐标，参数4为颜色bgr值，参数5为线宽。

- cv2.circle(img, (x0, y0), r, (b, g, r), thickness)：画圆。参数1为图片变量，参数2为圆心坐标，参数3为半径，参数4为颜色bgr值，参数5为线宽（-1表示填充）。

- cv2.ellipse(img, (x0, y0), (a, b), angle, startAngle, endAngle, (b, g, r), thickness)：画椭圆。参数1为图片变量，参数2为椭圆中心，参数3为x、y轴长度，参数4为椭圆旋转角度，参数5、6为椭圆起始角度和结束角度，参数7为颜色bgr值，参数8为线宽（-1表示填充）。

- cv2.polylines(img, [pts], True,  (0, 255, 255))：画多边形或连续的多条直线。参数1为图片变量，参数2为顶点坐标矩阵，参数3设置多边形是否闭合，参数4为颜色bgr值。

  顶点坐标矩阵：为顶点数×1×2维矩阵。pts = np.array([[x0, y0],  [x1, y1], [x2, y2], ......], np.int32)。

- cv2.fillPoly(img, [pts], npt, n, (0, 255, 255))：画多边形并填充。参数1为图片变量，参数2为顶点坐标矩阵，参数3为多边形顶点数目，参数4为绘制多边形数量，参数5为颜色bgr值。

- cv2.putText(img, 'text', (x, y), font_style, font_size, (b, g, r), thickness, lineType)：参数1为图片变量，参数2为要添加的文本，参数3为文字坐标（左下角），参数4为字体，参数5为字体大小，参数6为颜色bgr值，参数7为字体粗细，参数8为线型。

- cv2.createTrackbar('trackbar_name', 'window_name', num, upper, call_back)：创建滑动条。参数1为滑动条名称，参数2为窗口名称，参数3为当前的值，参数4为最大值，参数5为回调函数名称。

  cv2.getTrackbarPos('trackbar_name', 'window_name')：获取滑动条当前的值。参数1为滑动条名称，参数2为窗口名称。 

- cv2.setMouseCallback('window_name', mouse_event_name, param)：创建鼠标回调函数。

  参数1为窗口名称，参数2为鼠标响应回调处理函数，参数4为处理函数ID。

  def mouse_event(event, x, y, flags, param)：定义鼠标回调函数。

  参数1为鼠标事件：

  ​	EVENT_LBUTTONDBLCLK：左键双击

  ​	EVENT_LBUTTONDOWN：左键点击

  ​	EVENT_LBUTTONUP：左键释放

  ​	EVENT_MBUTTONDBLCLK：中间释放

  ​	EVENT_MBUTTONDOWN：中间点击

  ​	EVENT_MOUSEHWHEEL：滚轮事件

  ​	EVENT_MOUSEMOVE：滑动

  ​	EVENT_MOUSEWHEEL：滚轮事件

  ​	EVENT_RBUTTONDBLCLK：右键双击

  ​    EVENT_RBUTTONDOWN：右键点击

  ​	EVENT_RBUTTONUP：右键释放

  参数2、3为鼠标当前位置

  参数4为鼠标事件状态：

  ​    EVENT_FLAG_ALTKEY：按Alt不放事件

  ​    EVENT_FLAG_CTRLKEY：按Ctrl不放事件

  ​    EVENT_FLAG_LBUTTON：左键拖拽

  ​    EVENT_FLAG_MBUTTON：中键拖拽

  ​    EVENT_FLAG_RBUTTON：右键拖拽

  ​    EVENT_FLAG_SHIFTKEY：按Shift不放事件

  参数5为鼠标事件ID。

