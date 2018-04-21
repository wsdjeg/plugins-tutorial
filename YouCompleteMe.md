# 声明
- 以下内容适用于**Ubuntu**,**Fedora**,**Mac OS X**,**Windows**,**arch**
- **注意**笔者只在**ubuntu**以及**arch**行进行测试,并未在其余平台进行测试
- 安装过程大多来源于项目的README,望有能力阅读英文文档的同学直接去项目主页参阅README进行安装
- 以下内容截止于**2018年4月20日**均为正常,笔者不保证后续会持续进行进行更新,如有变动请参阅项目主页

# 项目主页
[YCM](https://github.com/Valloric/YouCompleteMe)

# 简介
YCM是一个非常有名的vim自动补全插件之一,他的特点是基于语义进行补全,同时反应速度非常之快.
缺点也很明显,就是安装困难.

## 安装
**注意** 以下安装方式为快捷安装,可能并不适合每个人.如果你参照下面的快速安装,安装YCM失败的话,请跳到最后的完全安装指导.

####Arch
- 请参照安全安装指导
- 无需安装python头文件

#### ubuntu
- 以下内容是基于Vundle插件管理器来进行说明.其他插件管理器同样可以进行参考,详情请参阅你所使用的插件管理的项目主页中的关于手动插件安装的说明


- 由于YCM内容较多,服务器在国外(~~最近两次用arch进行安装速度都挺快,不知道原因~~),不推荐直接使用Vundle进行安装.其他插件管理器同样不推荐,原因同上

- 需要vim版本为7.4.1578+支持python2或者python3.X,可以使用```vim --version```命令来查看vim是否编译有python支持.如果支持则该命令会有**+python**或**+python3**分别对应python2及python3支持.

- 从[项目主页](https://github.com/Valloric/YouCompleteMe)下载源码,或者直接执行以下内容
```git clone https://github.com/Valloric/YouCompleteMe ~/.vim/bundle/```

- 安装Cmake开发者工具```sudo apt install build-essential cmake```

- 若使用的系统版本为14.04及以下则需要安装以下内容,否则```cmake```会报错.```sudo apt-get install build-essential cmake3```

- 确认python头文件已经正确安装```sudo apt-get install python-dev python3-dev```

**前期准备已经完成,加油!你已经快要能使用YCM了!**

- **使用**c语言的语义支持编译YCM
```cd ~/.vim/bundle/YouCompleteMe```
```./install.py --clang-completer```
(推荐使用)

- **不使用**c语言的语义支持进行编译YCM
```cd ~/.vim/bundle/YouCompleteMe```
```./install.py```

可以在调用安装脚本时参照以下内容来增加对不同语言的支持
- C#: 安装 [Mono](http://www.mono-project.com/docs/getting-started/install/linux/#debian-ubuntu-and-derivatives) 在调用安装脚本```./install.py```添加```--cs-completer```即
```
./install.py --cs-completer
```
(ps: 下同)

- Go: 安装[Go](https://golang.org/doc/install)然后执行```./install.py --cs-completer```

- TypeScript: 安装[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node) 然后执行```npm install -g typescript```安装 TypeScript SDK

- JavaScript: 安装[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node) 然后执行```./install.py --js-completer```

- Rust: 安装[Rust](https://www.rust-lang.org/en-US/)然后执行```./install.py --rust-completer```

- Java: 安装[JDK8 (version 8 required)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)然后执行```./intall.py --java-completer```

是不是觉得很麻烦?别着急有个简单的方法开启全部的语义支持那就是```--all```标志!在此之前,你要先确认下```xbuild```,```go```,```tsserver```,```node```,```node```,```npm```,```rustc```,```cargo```这行工具已经安装.然后执行
```
cd ~/.vim/bundle/YouCompleteMe
./install.py --all
```

恭喜!你已经安装好了YCM!!但是先别着急我们需要一点别的配置才能让他完美的工作

#### Fedora

- 以下内容是基于Vundle插件管理器来进行说明.其他插件管理器同样可以进行参考,详情请参阅你所使用的插件管理的项目主页中的关于手动插件安装的说明


- 由于YCM内容较多,服务器在国外(~~最近两次用arch进行安装速度都挺快,不知道原因~~),不推荐直接使用Vundle进行安装.其他插件管理器同样不推荐,原因同上

- 需要vim版本为7.4.1578+支持python2或者python3.X,可以使用```vim --version```命令来查看vim是否编译有python支持.如果支持则该命令会有**+python**或**+python3**分别对应python2及python3支持.

- 安装CMake开发环境
```sudo dnf install automake gcc gcc-c++ kernel-devel cmake```

- 确认Python头文件已经安装
```sudo dnf install python-devel python3-devel```

**前期准备已经完成,加油!你已经快要能使用YCM了!**

- **使用**c语言的语义支持编译YCM
```cd ~/.vim/bundle/YouCompleteMe```
```./install.py --clang-completer```
(推荐使用)

- **不使用**c语言的语义支持进行编译YCM
```cd ~/.vim/bundle/YouCompleteMe```
```./install.py```

可以在调用安装脚本时参照以下内容来增加对不同语言的支持
- C#: 安装 [Mono](http://www.mono-project.com/docs/getting-started/install/linux/#debian-ubuntu-and-derivatives) 在调用安装脚本```./install.py```添加```--cs-completer```即
```
./install.py --cs-completer
```
(ps: 下同)

- Go: 安装[Go](https://golang.org/doc/install)然后执行```./install.py --go-completer```

- TypeScript: 安装[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node) 然后执行```npm install -g typescript```安装 TypeScript SDK

- JavaScript: 安装[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node) 然后执行```./install.py --js-completer```

- Rust: 安装[Rust](https://www.rust-lang.org/en-US/)然后执行```./install.py --rust-completer```

- Java: 安装[JDK8 (version 8 required)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)然后执行```./install.py --java-completer```

是不是觉得很麻烦?别着急有个简单的方法开启全部的语义支持那就是```--all```标志!在此之前,你要先确认下```xbuild```,```go```,```tsserver```,```node```,```node```,```npm```,```rustc```,```cargo```这行工具已经安装.然后执行
```
cd ~/.vim/bundle/YouCompleteMe
./install.py --all
```

恭喜!你已经安装好了YCM!!但是先别着急我们需要一点别的配置才能让他完美的工作


#### Windows
**注意**: 以下内容是建立在你会使用```CMD.ext```并知道如何把可执行文件添加到环境路径中的假设上的.
请确认你的vim版本为7.4.1578+并支持python2或python3.你可以在vim中执行```:version```命令来可查看特性中是否包含```+python2/dyn```或```+python3/dyn```.请注意vim的版本是32位或者64的.这关系到你安装32位或者64python.请将python版本与vim版本保持一致.以下内容默认你使用的是64为的vim及python

在你的vimrc文件中如果不存在```set encoding=utf-8```那么请添加上以上内容.这个设置是安装YCM所必须的.请注意这并不意味着你不能使用别的编码方式,你可以通过[the```++enc```argument](http://vimdoc.sourceforge.net/htmldoc/editing.html#++enc)来执行```:e```命令.

使用[Vundle](https://github.com/VundleVim/Vundle.vim#about)来安装YCM.

下载并安装以下软件:
- [python2 或 python3](https://www.python.org/downloads/windows/)请再次确认你所安装的vim版本和python版本一致(x86对应32位,x86_64对应64位)建议安装Python3.在vim中输入```:version```并在页面的底部查看与下面类似的内容```-DDYNAMIC_PYTHON_DLL=\"python27.dll\```,```-DDYNAMIC_PYTHON3_DLL=\"python35.dll\```前者表示需要python版本为python2.7,后者表示需要python3.5,你需要按照版本号下载对于版本的python.

- [CMake](https://cmake.org/download/)把CMake加入环境路径中.

- [Visual Studio](https://www.visualstudio.com/downloads/)下载社区版即```community edition```并在开发环境中选择```C++ in Workloads```(小提示:在安装过程中请关闭一切国产杀软,要不然容易出现各种莫名奇妙的BUG)

- **使用**C语言的语义来编译YCM:
```
cd %USERPROFILE%/vimfiles/bundle/YouCompleteMe
python install.py --clang-completer
```

- **不使用**C语言的语义来编译YCM:
```
cd %USERPROFILE%/vimfiles/bundle/YouCompleteMe
python install.py
```

可以在调用安装脚本时参照以下内容来增加对不同语言的支持
- C#: 执行```install.py --cs-completer```.请确认下the build utility msbuild is in your PATH.
```
./install.py --cs-completer
```
(ps: 下同)

- Go: 安装[Go](https://golang.org/doc/install)然后执行```./install.py --go-completer```

- TypeScript: 安装[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node) 然后执行```npm install -g typescript```安装 TypeScript SDK

- JavaScript: 安装[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node) 然后执行```./install.py --js-completer```

- Rust: 安装[Rust](https://www.rust-lang.org/en-US/)然后执行```./install.py --rust-completer```

- Java: 安装[JDK8 (version 8 required)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)然后执行```./install.py --java-completer```

是不是觉得很麻烦?别着急有个简单的方法开启全部的语义支持那就是```--all```标志!在此之前,你要先确认下```msbuild```,```go```,```tsserver```,```node```,```node```,```npm```,```rustc```,```cargo```这行工具已经安装在你的```PATH```.然后执行
```
cd %USERPROFILE%/vimfiles/bundle/YouCompleteMe
python install.py --all
```

你可以通过使用```--msvc```来改变使用的C++版本.YCM支持MSVC 12(Visual Studio 2013) ,14(2015),and 15(2017)

恭喜!你已经安装好了YCM!!但是先别着急我们需要一点别的配置才能让他完美的工作

# 完全安装指导
下面是YCM在unix os 和 windows中正常工作所需要的每个步骤

**Windows用户注意事项** 假定你会使用```cmd.exe```且所需的可执行文在```PATH```路径中,你不能全部复制命令要用```%USERPROFILE%```替代```~```,并且使用正确的vim路径.默认使用```vimfiles```来代替```.vim```.

有问题的话详参[FAQ](https://github.com/Valloric/YouCompleteMe#faq)

**注意**: YCM是一个带有编译组件的插件,如果您使用Vundle更新YCM且ycm_core库的API已经更改(很少出现),YCM将会通知您重新编译他.这时,你可以参照该指南在此进行安装.

**请仔细阅读以下说明内容,最好一字不漏的进行细读**
- 1.**请确认你的vim版本为7.4.1578 且支持Python2 或 Python3脚本.**

  在vim中执行```:version```.看前三行的输出, 他应该包含```Vi IMproved X.Y```其中X.Y就是vim的主要版本.如果你的版本大于7.4那么这块就没问题了.如果你的vim版本为7.4则需要查看```Include patches:1-Z```Z应该是一些数字,这些数字最低为1578.

  如果你的版本太旧的话,你可以从[从vim的源代码进行编译](https://github.com/Valloric/YouCompleteMe/wiki/Building-Vim-from-source)(别担心,非常的简单的).

  当你的版本为7.4.1578+时在vim中输入```:echo has('python') || has('python3')```.正常情况下输出应该为1. 如果输出是0的话,你需要为当前版本的vim提供python支持.

  在 Windows 中你还需要检查vim的版本是32位还是64位,因为你安装的python版本必须与vim版本相符才可以调用YCM的库.推荐使用64位的vim.

- 2.**使用Vundle安装YCM(或者是Pathogen等插件管理器),使用Vundle管理器的话,你需要在你的[vimrc](https://vimhelp.appspot.com/starting.txt.html#vimrc)中添加```Plugin 'Valloric/YouCompleteMe'```

  如果你未使用Vundle进行安装的话,请运行```git submodule update --init --recursive```对下载的YCM文件与仓库进行对比检查并更新依赖等内容.

- 3.[当你需要c语言的语义时需要以下步骤,否则请跳过下面步骤]
  **下载最新版本的```libclang```.Clang 是一个可以编译C/C++/Objective-C/objective-C++/的开源编译器.他提供的```libclang```库用于为这些语言提供YCM语义补全引擎.YCM需要3.9+版本的```libclang```
  当你确定你的系统里的libclang版本为3.9+的话,你可以直接使用.如果你不确定的话,推荐使用[llvm.org官方的二进制文件](http://releases.llvm.org/download.html)请确认你下载的版本适用于你的系统.
  **再次建议**不要使用系统自带的libclang来代替上游的二进制文件.任意使用的话可能会损坏上游的libclang使用的依赖.
- 4.YCM需要编译ycm_core库文件.这些库是基于C++引擎的,YCM可以使用这个库来达到高速的目的.
  你要正确的安装```cmake```才可以编译生成YCM所需的文件.Linux用户可以使用包管理来进行安装(例如ubuntu用户可以使用```sudo apt install cmake```)其他用户可以从[官方网站](https://cmake.org/download/)下载安装.Mac用户可以通过Homebrew来进行安装```brew install cmake```
  对于unix os用户来说,你需要确认Python的头文件已经安装(ps: arch用户可忽略)对于Debain类用户来说你可以通过使用```sudo apt-get install python-dev python3-dev```来进行安装.对于Mac用户来说,这些应该都已经预装在系统中了.
  对于Windows用户来说,你需要下载并安装[Python2 或 Python3](https://www.python.org/downloads/windows/).别忘了选择跟你系统vim版本一致的安装包.你同样需要安装Microsoft Visual C++(MSVC)来编译YCM.你可以通过[官方网站](https://www.visualstudio.com/downloads/)来安装MSVC.MSVC 12(VS2013),14(VS 2015)和15(2017)都被YCM支持.
  这里我们假设你通过Vundle来安装YCM那么Ycm的根目录位于```~/.vim/bundle/YouCompleteMe```.
  我们需要建一个新的文件夹来放置编译的文件,按照下面的内容来进行操作
  ```
  cd ~
  mkdir ycm_build
  cd ycm_build
  ```
  现在我们需要生成编译文件了.如果你不需要支持C系语言,那么你可以在```ycm_build```目录中执行以下命令:
  ```cmake -G "<generator>" . ~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp```
  ```<generator>```是```Unix Makefiles```是对Unix来讲的.windows用户可以用以后内容之一来代替```<generator>```
  - ```Visual Studio 12 Win64```
  - ```Visual Studio 14 Win64```
  - ```Visual Studio 15 Win64```

  如果你使用的是32位的vim那么请移除```Win64```

  对于想要使用系统自带的 boost(额,你懂得)你需要把```-DUSE_SYSTEM_BOOST=ON```参数传递给cmake.
  这一些捆绑版本的boost导致不能直接编译的系统来说,上面的命令是必须的.

  **小心**我们再次**强烈建议**不要使用系统自带的boost来替代捆绑版本(version of boost).可能会有一些莫名的bug.请一定要使用捆绑版本的boost.

  如果你需要c系语言的语义支持的话,那么你的```cmake```调用可能会复杂一点.下面基于你已经从上面的第三步中下载了llvm.org中的LLvm+clang的二进制版本.你可以把文件解压到```~/ycm_temp/llvm_root_dir```(包含```bin, libinclude```等等文件夹)对Windows用户来说需要使用[7-zip](https://www.7-zip.org/download.html)来进行解压.

  **小心**这仅限于下载的llvm二进制文件包,而不是内置的llvm!使用自定义的文件包来安装时请参阅以下的文档内容```EXTERNAL_LIBCLANG_PATH```

  在使用下载编译的llvm二进制文件包下,在```ycm-build```目录中使用以下命令:
  ```cmake -G "<generator>" -DPATH_TO_LLVM_ROOT=~/ycm_temp/llvm_root_dir . ~/.vim/bundle/YouCompleteMe/third_party/ycmd/cpp```
  上面的```<generator>```上面一样被替代.
  现在已经生成了可编译文件,使用下面的命令来进行编译
  ```cmake --build . --target ycm_core --config Release```
  ```config Release```仅限于Windows用户.在unix os中会被忽略.
  对于那些想要使用系统版本的libclang的用户来说,需要传递以下参数
  ```-DUSE_SYSTEM_LIBCLANG=ON```给cmake来代替``-DPATH_TO_LLVM_ROOT=...``
 **小心** **再次强烈建议**不要使用系统内置的libclang来代替上游的二进制包.不然可能会出现莫名的bug.

  当然如果你非要使用内置的libclang库的话,你可以使用```DEXTERNAL_LIBCLANG_PATH=/path/to/libclang.so```标志(对mac用户来说库的结尾名为.dylib)然后这个标志就会代替其他的标志.**如果你是从上游编译的llvm的话,应该使用的标志位会被代替**.

  如果你已经编译了c系语言支持的话,用```cmake```命令也会在```YouCompleteMe/third_party/ycmd```目录中替代```libclang.[so|dylib|dll]```

- 5.自定义你需要补全的语言:
  - C#:安装[Mono on non-Windows platforms](http://www.mono-project.com/docs/getting-started/install/)切换到```YouCompleteMe/third_party/ycmd/third_party/OmniSharpServer```运行下面的命令:
  ```msbuild /property:Configuration=Release /property:Platform="Any CPU" /property:TargetFrameworkVersion=v4.5```
  对于Windows用户来说,请确认[编译使用的```msbuild```在你的PATH中](https://stackoverflow.com/questions/6319274/how-do-i-run-msbuild-from-the-command-line-using-windows-sdk-7-1)

  - Go: 在你的路径中安装[Go](https://golang.org/doc/install)切换到```YouCompleteMe/third_party/ycmd/third_party/gocode```然后运行```go build```.

  - TypeScript support: 和快速引导里一样,安装非常的简单,在安装过[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node)后运行```npm install -g typescript```

  - JavaScript: 安装[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node)然后切换到```YouCompleteMe/third_party/ycmd/third_party/tern_runtime```并运行```npm install --production```

  - Rust: 安装[Rust](https://www.rust-lang.org/en-US/)切换到```YouCompleteMe/third_party/ycmd/third_party/racerd```运行```cargo build --release```

  - Java 安装[JDK8(version 8 required)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)然后下载```[binary release of eclipse.jdt.ls ](http://download.eclipse.org/jdtls/milestones/)```并将其解压到```YouCompleteMe/third_party/ycmd/third_party/eclipse.jdt.ls/target/repository```.小心!此方法不推荐一般用户使用,只推荐那些YCM高级用户和YCM开发人员.一般用户请使用```install.py```来开启java支持.

恭喜!你已经完成了安装!!不要忘了如果你需要c系语言的语义支持的话,你需要在安装过程中提供标志给YCM.当然.在指导中已经包含了这些内容了.
YCM为其选项提供了合适的默认值,但是您可以查看使用与配置的内容,并且打开几个默认为关闭的选项.

#### 特性概要快速浏览

##### 普遍特性

- 超快速已识别标签和语法关键字补全
- 智能补全排序及过滤
- 文件和路径补全
- 支持 vim OmniFunc 补全
- Ultisnips 片段补全

##### C系语言(C,C++,Objective C,Object C++)

- 语义自动补全
- 实时语法检错
- Include/declaration/definition跳转(```GoTo```,等等)
- identifiers的语义类型信息(```GetType```)
- 自动修复当某些语法错误(```FixIt```)
- 浏览identitiers的文档信息(```GetDoc```)

##### C#
- 语义自动补全
- 实时语法检错
- 定义/声明跳转(```GoTO```,等等.)
- indetifiers的语义类型信息(```GetType```)
- 自动修复某些语法错误(```FixIt```)
- 管理OmniSharp实例服务
- 浏览identitiers的文档信息(```GetDoc```)

##### Python
- 智能补全
- 定义/声明及帮助文档跳转(```GoTO, GoToReferences```)
- identifiers文档信息浏览(```GetDoc```)
- 通过重启[JediHTTP](https://github.com/vheon/JediHTTP)服务,切换不同的Python解释器

##### Go
- 语义自动补全
- 定义跳转(```GoTO```)
- 管理```gocode```服务实例

##### TypeScript
- 语义自动补全
- 实时语法检错
- 标记重命名(```RefactorRename<new name>```)
- 定义跳转,查找帮助文档(```GoTODefinition, GoToReferences```)
- identifiers 语义类型信息(```GetType```)
- 浏览 identifiers文档信息(```GetDoc```)

##### JavaScript
- 智能补全
- 变量重命名(```RefactorRename<new name>```)
- 定义跳转,浏览参考文档(```GoTODefinition, GoToReferences```)
- 修改 identifiers信息(```GetType```)
- 浏览identifiers文档信息(```GetDoc```)
- 管理```Tern```服务实例

##### Rust
- 语义自动补全
- 定义跳转(```GoTo, GoToDefinition```和```GoToDeclaration```都是identical)
- ```racer```实例管理
- 浏览identifiers文档信息(```GetDoC```)

##### Java
**小心**Java目前只是实验性支持,请向我们提供[反馈](https://github.com/Valloric/YouCompleteMe#contact),帮助这个项目的发展谢谢!

- 基于自动导入插入的的语义补全(Semantic auto-completion with automatic import insertion)
- 定义跳转(```GoTO, GoToDefinition```和'GoTODeclaration'都是identical)
- 帮助文档查询('GoToReferences')
- 实时语法检错
- 标记重命令(```RefactorRename<new name>```)
- 浏览identifiers文档内容(```GetDoc```)
- 修改identifiers信息(```GetType```)
- 自动修复包括代码生成(code generation)在内的错误(```FixIt```)
- 代码格式(```Format```)
- 选择java项目
- 管理```jdt.ls```服务实例

# 用户指导
#### 一般用法
如果补全候选内容太过宽泛,请继续输入字符,YCM会根据你输入的字符修改补全候选内容.

补全过滤是对大小写敏感的是这样的,如果你输入的全是小写字符,则补全内容不会区分大小写,一旦你输入任意一个大写字符,那么补全候选框的内容将会启用大小写敏感.例如"foo"匹配"Foo"和"foo"而"Foo"则只匹配"Foo"和"
FOO"但是却不会匹配"foo"

Gvim使用```TAB```选择补全框中的第一个补全内容,继续按```Shift-TAB```键则会在补全候选框中进行循环选择.**注意**如果你使用的是console Vim(即终端vim)那么```Shift-Tab```可能无法切换,因为console无法将其传递给Vim.你可以重新映射按键;参阅下面的[设置](https://github.com/Valloric/YouCompleteMe#options)部分.

了解一部分YCM内部工作原理,可以防止一些错误的发生.YCM有几个不同的补全引擎:一个基于你当前文件中的所有identifiers和你浏览文件中的identifiers以及标签并的并在你输入时,自动收集的补全引擎(identifiers被放在per-filetype 组中).

同样YCM也有几个语义补全引擎.有一个基于libclang-based的c系语义补全引擎.一个基于Jedi-based的Python语义补全引擎.另外还有一个基于omnifuc,使用Vim的omnicomplete系统数据的补全引擎.当该YCM中不存在语言的补全引导时,就会调用该引擎.

就如你所想的那样,YCM当然也还有其他补全引擎,比如UltiSnips程序及文件路径补全引擎.

在所有的补全模式下,YCM会自动去选择最优的补全引擎进行补全.偶尔,他会同时将几个不同补全引擎中的内容合并并一起输出到你的补全结果当中.

#### Client-Server 框架
YCM与一个CS框架,YCM中的vim所呈现的部分只是一个客户端,他与ycmd HTTP +JSON 服务器进行通信，该服务会跟随你开启或关闭vim进行开启或关闭.

**好了基础部分介绍完毕**下面进入配合阶段
相信你如果坚持阅读到了此处,一定会对YCM有一个整体的大致的印象的!

**注意**由于笔者目前主要使用Python进行编程,故以下配置除通用部分外,已Python为准

```set completeopt=longest,menu```   "让Vim的补全菜单行为与一般IDE一致(参考VimTip1228)

```autocmd InsertLeave * if pumvisible() == 0|pclose|endif ```  "离开插入模式后自动关闭预览窗口

```inoremap <expr> <CR>       pumvisible() ? "\<C-y>" : "\<CR>"``` "映射按键,没有这个会导致其他插件的tab不能用

```let g:ycm_key_list_select_completion=['<c-n>', '<Down>']```

```let g:ycm_key_list_previous_completion=['<c-p>', '<Up>']```

```let g:ycm_confirm_extra_conf=```                      "关闭加载.ycm_extra_conf.py提示

```let g:ycm_collect_identifiers_from_tags_files = 1```   " 开启 YCM基于标签引

```let g:ycm_min_num_of_chars_for_completion=2```         " 从第2个键入字符就开始罗列匹配项

```let g:ycm_use_ultisnips_completer = 1```               " Default 1, just ensure

```let g:ycm_cache_omnifunc=0```                          " 禁止缓存匹配项,每次都重新生成匹配项

```let g:ycm_seed_identifiers_with_syntax=1```            " 语法关键字补全

```let g:ycm_complete_in_comments = 1```                  " 在注

ps:其他语言的配置请参考官方文档,或者等其他人来提交配置,不才就不来献丑了.

# 说一句题外话,抛砖引玉,Vim-chian刚刚起步,希望大家能多少拿出一部分自己宝贵的时间来进行下总结,既可以提升自己又可以帮助后来人何乐而不为呢?

#### 配置选项
默认设置,一般情况下足够正常使用了.若有定制需求的话,可已参照下面列出的选项进行设置.

**```g:ycm_min_num_of_chars_for_completion``` 选项**

设置YCM从第几个字符开始罗列补全选项默认为2,该选项不作用于语义补全.

```let g:ycm_min_num_of_chars_for_completion = 2```

**注意**: 每次更改设置之后,都需要重启下vim才可以正常加载已更改的设置内容.


```g:ycm_min_num_identifier_candidate_chars``` 选项

这个选项控制触发identifiers补全的字符数.默认为0即不限制字符数.
**注意**: 这个选项之影响identifiers不影响基于语义的变量自动补全

```let g:ycm_min_num_identifier_candidate_chars = 0```


**```g:ycm_max_num_candidates``` 选项**

这个选项控制在候选补全框内显示的补全条目的最大数量.仅限于基于语义的自动补全.请参阅[g:ycm_max_identifier_candidates](https://github.com/Valloric/YouCompleteMe#the-gycm_max_num_identifier_candidates-option)选项
0值比较特殊意味着无限制

**注意**: 不建议将值设置为0或者大于100的值,这样会减缓补全速度.

默认值为```50```

```let g:ycm_max_num_candidates = 50```

```g:ycm_max_num_identifier_candidates``` 选项

该选项控制基于identifiers-based引擎的最大候选补全项

```0``` 比较特殊意味着无限制

**注意**: 不建议将值设置为0或大于100的数, 这样会减缓补全速度.

默认值为 ```10```

```let g:ycm_max_num_identifier_candidates = 10```

**```g:ycm_filetype_whitelist``` 选项**

这个选项控制YCM可以在哪些VIM文件类型( ```:h filetype``` )中开启. 其值应为字典形式(比如Python,cpp等)同时像哈希设置一样,值并不重要,(字典像哈希设置一样,即只有键重要)

```*``` 键是一个特殊的能匹配所有文件类型的键.默认情况下,白名单内只含有此键.

YCM同样可以设置黑名单选项```g:ycm_filetype_blacklist```,

 此选择限制YCM开启的文件.YCM会在黑白名单的同时作用下进行工作.(黑名单的"allows"是一个没有键值的文件类型)

举个例子: 假设你需要用YCM处理 ```cpp``` 类文件,这个文件类型应该以字典的形式正确的放入白名单中.(cpp键即为白名单).当然你也可以直接在白名单中使用  ```*```  键,来在任意文件类型中启用YCM.

一旦文件类型在忽略列表(黑名单)中出现,那么针对该类型的所有文件,YCM都不会启用.

你可以使用  ```:set ft?```  来获取当前使用的文件的文件类型
默认值为: ```{'*' : 1}```

```let g:ycm_filetype_whitelist = { '*': 1  }```

**```g:ycm_filetype_blacklist``` 选项**

此选项控制YCM应当在那些vim文件类型(```:h filetype```)中关闭. 这个选项的值应该为字典形式.键的内容为文件类型(比如Pyton,CPP等).其值并不重要.(就像哈希一样,键才是重要的)请参阅 ```g:ycm_filetype_whitelist``` 选项来理解其工作方式.

默认值为```[see next line]```

```
let g:ycm_filetype_blacklist = {
      \ 'tagbar' : 1,
      \ 'qf' : 1,
      \ 'notes' : 1,
      \ 'markdown' : 1,
      \ 'unite' : 1,
      \ 'text' : 1,
      \ 'vimwiki' : 1,
      \ 'pandoc' : 1,
      \ 'infolog' : 1,
      \ 'mail' : 1
      \}}
```

**```g:ycm_filetype_specific_completion_to_disable``` 选项**

该选项控制YCM语义补全引擎在哪些文件类型中关闭.值应为字典形式,键为文件类型(例Python,cpp),值不重要重要的是键.他列出了所有YCM语义补全引擎忽略的文件类型.但是!基于identifiers-based的补全引擎在这些文件类型中同样会启用.

**注意**: 即使未关闭特定类型的文件补全,但是语义引擎不支持该类型文件的话,同样不会触发补全.可以使用 ```:set ft?``` 来获取当前文件的类型.

默认值为: ```[see next line]```

```
let g:ycm_filetype_specific_completion_to_disable = {
      \ 'gitcommit': 1
      \}
```

**```g:ycm_show_diagnostics_ui``` 选项**

设置过该选项后,则会打开YCM的诊断显示特性.

诊断UI的特性部分(比如侧边符号,文本高亮, 诊断显示, 自动位置列表填充)均可以单独打开或关闭.详参下面内容.

请注意: YCM的诊断UI目前仅支持C系语言.

此选项设置后将会移除所有有关 ```c, cpp, objc, objcpp``` 文件类型的语言检错设置.因为这些会与YCM的诊断UI冲突

如果你正在使用C系语言的identifiers补全,但是无法使用clang-based语义补全,通是希望使用GCC语法检错的话,那么请取消该选择.

默认值为: ```1```

```let g:ycm_show_diagnostics_ui = 1```

**```g:ycm_error_symbol``` 选项**

YCM会使用该选项指定的值来在vim的侧边显示错误信息.

该选项为语法兼容层的一部分.若未设置该选项,那么YCM则会在使用默认值之前尝试调用 ```g:syntastic_error_symbol```

默认为: ```>>```

```let g:ycm_error_symbol = '>>'```

```g:ycm_warning_symbol``` 选项

YCM会使用该值指定的值来在vim的侧边显示警告信息.

该选项为语法兼容层的一部分, 若未设置该选项,那么YCM会在使用默认值之前尝试调用 ```g:syntastic_warning_symbol```

默认为: ```>>```

```let g:ycm_warning_symbol = '>>'```

**```g:ycm_enable_diagnostic_signs``` 选项**

当该选项设置后,YCM会把诊断图标放置在vim的侧栏当中.关闭该选项同样会关闭 ```YcmErrorLine``` 和 ```YcmWarningLine``` 高亮.

该选项为语法兼容层的一部分,若未设置该选项,则在使用默认值之前,YCM会尝试去调用 ```g:syntastic_enable_signs```

默认为: 1

```
let g:ycm_enable_diagnostic_signs = 1
```

**```g:ycm_echo_current_diagnostic``` 选项**

当该选择设置后,你把光标放置到有错误处,则YCM会显示该行的错误信息.如果当前检错提供了可修复功能那么YCM会尝试去修复该错误.

该选项为语法兼容层的一部分,若未设置该选项,则在使用默认值之前,YCM会尝试去调用 ```g:syntastic_echo_current_error```

默认为: ```1```

```
let g:ycm_echo_current_diagnostic = 1
```

**```g:ycm_filter_diagnostics``` 选项**

该选项控制YCM的检错显示信息.值为字典形式,键为用逗号分割的vim文件类型字符串,值为过过滤器.

过滤器是字典的键值对,其中键是筛选类型,值为筛选器的参数列表.在列表只有一项内容是,你可以省略括号直接提供参数.若任意一个过滤器与检错器相同的话,那么YCM会删除该过滤器,并且不会显示该过滤器内容

支持以下筛选器类型:

- "regex" 接受字符串形式的正则表达式.当检错器在诊断文本中找到匹配该正则表达式的内容时,该过滤器生效.

- "level"接受字符串形式的级别类型."warninig" 或 "error".当检错器的诊断内容包含指定的等级内容的话,该过滤器生效.

**注意**: 正则表达式使用不是VIM的语法,而是PYTHON的

默认值为: ```{}```

```
let g:ycm_filter_diagnostics = {
  \ "java": {
  \      "regex": [ ".*taco.*", ...  ],
  \      "level": "error",
  \      ...
  \    }
  \ }
```

**```g:ycm_always_populate_location_list``` 选项 **

该选项设置后,YCM会在每次获取到诊断数据时,将其填充到位置列表中.默认下为了避免影响到您放置在位置列表中的其他内容,该选项为关闭状态.

请参阅: ```:help location-list```

这个选项是语法兼容层的一部分,若该选项为设置则在使用该选项的默认值之前YCM会对 ```g:syntastic_always_populate_loc_list``` 进行调用

默认为: ```0```

```
let g:ycm_always_populate_location_list = 0
```

**```g:ycm_open_loclist_on_ycm_diags``` 选项**

该选项设置后,```YcmDiags``` 会在强制编译且用诊断数据填充位置列表后,打开位置列表.

详参: ```:help location-list```

默认为: ```1```

```
let g:ycm_open_loclist_on_ycm_diags = 1
```

**```g:ycm_complete_in_comments``` 选项**

该选项值设置为 ```1``` 时,即使实在编写注释内容,YCM也会显示补全框

默认为: ```0```

```
let g:ycm_complete_in_comments = 0
```

**```g:ycm_complete_in_strings``` 选项**

该选择值设置为 ```1```时,YCM会在键入字符串时提供补全建议

**注意**: 默认下该选项值为 ```1```,以便补全文件名.例如在C语言中,键入
```# inclde``` 会触发文件名的补全.这会很有用的.

默认值: ```1```

```
let g:ycm_complete_in_strings = 1
```

**```g:ycm_collect_identifiers_from_comments_and_strings``` 选项**

该选项值为 ```1``` 时,YCM的identifiers补全引擎,将会在字符串和注释中收集补全内容.为 ```0``` 时则会取消.

默认为: ```0```

```
let g:ycm_collect_identifiers_from_comments_and_strings = 0
```

**```g:ycm_collect_identifiers_from_tags_files ``` 选项 **

该选择值为 ```1``` 时,YCM的identifiers补全引擎会从文件标签中收集identifier. 文件标签是从vim 的 ```tagfiles()``` 函数中进行检索的.详参 ```:h tags```

若YCM检测到文件标签已被修改,那么他会重修进行检索.

**注意** 目前仅支持 Exuberance Ctags 格式不支持一般的Ctags格式. Ctag许要通过 ```--fields=+l``` 进行调用.(是小写的L) 因为YCM要标记输出的语言. ```language:<lang>```

若你的标签文件未被YCM读取,请参阅 ```项目页面的FAQ```

默认下该选项为关闭状态.因为如果标签位于网络上的话会造成vim启动速度偏慢.

默认为: ```0```

```
let g:ycm_collect_identifiers_from_tags_files = 0
```

**```g:ycm_seed_identifiers_with_syntax``` 选项**

该选择值为1是, YCM的identifier 补全引擎会为你当前编写的编程语言的关键字,在其identifier库中添加种子.

由于语法关键字是从 ```vim syntax file``` 中提取的,因此可能未完全收集关键字.具体取决于语法文件的编写方式.一般情况下,最少也能提取95%以上的语法关键字.

默认为: ```0```

```
let g:ycm_seed_identifiers_with_syntax = 0

```

**```g:ycm_extra_conf_vim_data option``` 选项**

如果你正在使用基于语义的c系语言自动补全,该选择可能对你有很大的帮助.这是一种从vim向 你的.ycm_extra+conf.py 的 ```FlagForFile``` 函数发送数据的方法.

这个选项支持vim脚本语法中的字符串列表形式, 该字符串会对每个对ycmd服务的请求进行评估, 然后将其作为 client_data 关机子参数传递给 FlagForFile函数.

例如: 将该选项设置为 ```['v: version']```,则 FlagForFile 函数的调用方式如下:

```
# The '704' value is of course contingent on Vim 7.4; in 7.3 it would be '703'
FlagsForFile(filename, client_data = {'v:version': 704})
```

综上 ```client_data``` 参数是一个字典,他将vim的表达式字符串映射到请求时的值上.

正确定义你的 FlagForFile 函数的形式如下:

```def ForFile(filename, **kwargs):```

然后你就可以使用 ```client_data``` 的 ```kwargs['client_data']``` 来获取数据了

默认为: ```[]```

``` let g:ycm_extra_conf_vim_data = [] ```

**```g:ycm_server_python_interpreter``` 选项**

默认下YCM会在你的系统上自动查找合适的Python解释器,你可以为该选项指定值来覆盖默认行为.

**注意**: 该解释器仅限于[ycmd server](https://github.com/Valloric/ycmd) 在vim中使用的YCM总是使用vim内置的Python解释器.

默认值为: ```''```

```
let g:ycm_server_python_interpreter = ''
```

**```g:ycm_keep_logfiles``` 选项**

该选项值为 ```1``` 时, YCM 和 [ycmd completion sever](https://github.com/Valloric/ycmd)会在服务关闭后保留日志文件.(默认下关闭服务后会删除日志)

查看日志内容请调用 ```:YcmDebugInfo```

默认为: ```0```

```
let g:ycm_keep_logfiles = 0
```

**```g:ycm_log_level```** 选项
YCM 和 ycmd completion server 使用等级来区分日志的种类.下面有效值排序为从最详细到最不详细:
- ```debug```
- ```info```
- ```warning```
- ```error```
- ```critical```

**注意**: ```debug```内容冗长

默认为: ```info```

```
let g:ycm_log_level = 'info'
```

**```g:ycm_auto_start_csharp_server``` 选项**

该选项值为 ```1``` 时,当打开 C# 文件时, ```OmniSharp``` 服务会自动开启.

默认为: ```1```

```
let g:ycm_auto_start_csharp_server = 1
```

**```g:ycm_auto_stop_csharp_server``` 选项**

该选项值为 ```1``` 时 OmniSharp 服务会在vim关闭后自动关闭

默认为: ```1```

```
let g:ycm_auto_stop_csharp_server = 1
```

**```g:ycm_csharp_server_port``` 选项**

当 ```g:ycm_auto_start_csharp_server``` 值为 ```1``` 时,才可以指定OmniSharp服务监听的端口. 为 ```0``` 则默认使用系统提供的监听端口.

默认为: ```0```

```
let g:ycm_csharp_server_port = 0
```

**```g:ycm_csharp_insert_namespace_expr``` 选项**

默认情况下,当YCM 插入一个命名空间时,他会在最近的 using statement 下插入 using statement.
或许你希望将 using statement 语句插入某个位置并保留顺序.那么你可以修改该选项来覆盖默认行为:

该选项设置后,YCm会使用全局变量 ```g:ycm_namespace_to_insert``` 设置为插入的命名空间进行命名,而不是 using statement 本身.

默认: ```''```

```
let g:ycm_csharp_insert_namespace_expr = ''
```

**```g:ycm_add_preview_to_completeopt``` 选项**

该选项值为 ```1``` 是YCM会将预览字符串添加到vim的自动补全窗口中.详参
(```:h completeopt```).若你的自动补全设置已经设置过,则该选项不会覆盖i的设置,同时不会生效.(即该补全行为不会复写vim自身的补全设置,且优先级低于vim自身的补全设置).你可以使用 ```:set completeopt?``` 来查看当前的补全设置.(千万别忘了最后的?)

当进行自动补全预览时,YCM会使用文件顶部的预览窗口来存储有关当前候选内容的详细信息(仅在候选项来自于语义补全引擎才该行为才有效).例如,如果当前补全的是函数名,那么他会在补全窗口中显示完整的函数原型及调用.

默认为: ```0```

```
let g:ycm_add_preview_to_completeopt = 0
```

**```g:ycm_autoclose_preview_window_after_completion``` 选项**

该选项值为 ```1``` 时YCM会在用户选择好自动补全内容后关闭补全窗口.若用户输入没触发补全的话,那么该选项无效.详参 ```g:ycm_add_preview_to_completeopt``` 选项.

默认为: ```0```

```
let g:ycm_autoclose_preview_window_after_completion = 0
```

**```g:ycm_autoclose_preview_window_after_insertion``` 选项**

该选择值为 ```1``` 时,YCM会在退出插入模式后自动关闭补全框.若设置了 ```g:ycm_autocrose_preview_window``` 后未触发补全, 则该选项无效.详参 ```g:ycm_add_preview_to_completeopt```

默认为: ```0```

```
let g:ycm_autoclose_preview_window_after_insertion = 0
```

**```g:ycm_max_diagnostics_to_display``` 选项**

该选项控制在检测完文件中的错误和警告信息后，向用户呈现的最大诊断数量．且目前仅限于使用ｃ系语义自动补全引擎的情况．

默认为　```30```

```
let g:ycm_max_diagnostics_to_display = 30
```

**```g:ycm_key_list_select_completion``` 选项**

该选项控制首选补全项的按键映射．调用他们中的任意一个均可在补全候选框内进行跳转和循环．

有些用户喜欢把 ```<Enter>``` 键加入列表．
默认为： ```['<TAB>', '<Down>']```

```
let g:ycm_key_list_select_completion = ['<TAB>', '<Down>']
```

**```g:ycm_key_list_previous_completion``` 选项**

这个设置控制选择补全内容的按键映射．他们中的任意一个都已可以在补全框内向前跳转循环．

**请注意**: 默认的 ```<S-TAB>``` 是指Shift-TAB,该映射可能只能在Gvim中工作,终端vim请修改为其他按键.

默认为: ```['<S-TAB>', '<Up>']```

```
let g:ycm_key_list_previous_completion = ['<S-TAB>', '<Up>']
```

**```g:ycm_key_list_stop_completion``` 选项**

该选择控制用于关闭自动补全功能的按键映射.当你需要浏览代码或者需要插入
制表符或者你想要从[UltiSnips](https://github.com/SirVer/ultisnips/blob/master/doc/UltiSnips.txt)中展开部分片段的话,该选项非常有用.

默认为: ```['<C-y>']```

```
let g:ycm_key_list_stop_completion = ['<C-y>']
```

**```g:ycm_key_invoke_completion``` 选项**

这个选项是控制语义补全的按键的映射.默认下,输入字符后自动触发语义补全在插入模式下 ```.``` , ```->``` (若已编译了语义完成支持),这个按键映射可用于任何位置触发语义补全.在搜索顶级函数库和类的时候,这个选项非常有用.

当用户输入 ```<C-Space>``` 时,终端 vim 会把 ```<Nul>``` 传递给vim.因此当使用终端vim时,YCM将会确保此按键映射启用.当然在使用Gvim时YCM会确保 ```<C-Space>``` 启用. 这意味着无论是在Gvim 还是终端vim中,但你按下 ```<C-Space>``` 后YCM都会正确的运行.

将该选项的值设置为空字符的话,则会确保没有任何按键映射被创建.

默认为: ```<C-Space>```

```
let g:ycm_key_invoke_completion = '<C-Space>'
```

**```g:ycm_key_detailed_diagnostics``` 选项**

该选项用于控制是否在当用户光标位于有诊断内容的行上时,显示诊断信息.他基于 ```:YcmShowDetailedDiagnostic``` 进行调用.

将该选项的值设置为空字符的话,则会确保没有任何按键映射被创建.

默认为: ```<leader>d```

```
let g:ycm_key_detailed_diagnostics = '<leader>d'
```

**```g:ycm_global_ycm_extra_conf``` 选项**

一般情况下YCM会查找一个用于编译 ```.ycm_extra_conf.py``` 的标志(相关信息请参阅项目主页的 User Guid for more details on how this works)这个选项指定的内容会在找不到```.ycm_extra_conf.py```文件的情况下启用.

你可以将这样的全局文件放置于系统的任何位置.

默认为: ```''```

```
let g:ycm_global_ycm_extra_conf = ''
```

**```g:ycm_confirm_extra_conf``` 选项**

该选项值为 ```1``` 时,YCM会询问一次 ```.ycm_extra_conf.py```文件,如果他可以安全加载的话.这是为了防止执行你未写入```.ycm_extra_conf.py```的恶意代码.

可以选择性的让YCM询问/不询问关于装载 ```.ycm_extra_conf.py```文件.详参 ```g:ycm_extra_conf_globlist``` 选项.

默认为: ```1```

```
let g:ycm_confirm_extra_conf = 1
```

**```g:ycm_extra_conf_globlist``` 选项**

该选项的值是一个列表.其中可能包换多个全局模式.如果模式全以 ```!``` 开头,那么与该模式匹配的 ```.ycm_extra_conf.py``` 文件会被放入黑名单中.即不会加载这些文件,且不会显示确认对话框.若模式不是以 ```!``` 开始的那么所有与该模式匹配的文件都会被列入白名单.
**注意**: 当认证被禁用时,使用 ```g:ycm_confirm_extra_conf``` 该选项会导致列表前面的内容优先于后面的内容.

规则:
- ```*``` 全部匹配
- ```?``` 匹配任意单个字符
- ```[seq]``` 匹配任何相同的字符
- ```[!seq]``` 匹配任意不相同的字符

例如:

```
let g:ycm_extra_conf_globlist = ['~/dev/*','!~/*']
```

##### 剩下的内容笔者觉得大多数都不需要,有需求的同学也自己能看得懂文档,所以就不啰嗦了.
