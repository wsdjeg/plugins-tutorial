# 声明
- 以下内容适用于**Ubuntu**,**Fedora**,**Mac OS X**,**Windows**,**arch**
- **注意**笔者只在**ubuntu**以及**arch**行进行测试,并未在其余平台进行测试
- 安装过程大多来源于项目的README,望有能力阅读英文文档的同学直接去项目主页参阅README进行安装
- 以下内容截止于**2018年4月20日**均为正常,笔者不保证后续会持续进行进行更新,如有变动请参阅项目主页

#项目主页
[YCM](https://github.com/Valloric/YouCompleteMe)

# 简介
YCM是一个非常有名的vim自动补全插件之一,他的特点是基于语义进行补全,同时反应速度非常之快.
缺点也很明显,就是安装困难.

## 安装
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

- Go: 安装[Go](https://golang.org/doc/install)然后执行```./install.py --cs-completer```

- TypeScript: 安装[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node) 然后执行```npm install -g typescript```安装 TypeScript SDK

- JavaScript: 安装[Node.js and npm](https://docs.npmjs.com/getting-started/installing-node) 然后执行```./install.py --js-completer```

- Rust: 安装[Rust](https://www.rust-lang.org/en-US/)然后执行```./install.py --rust-completer```

- Java: 安装[JDK8 (version 8 required)](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)然后执行```./install.py --java-completer```

是不是觉得很麻烦?别着急有个简单的方法开启全部的语义支持那就是```--all```标志!在此之前,你要先确认下```xbuild```,```go```,```tsserver```,```node```,```node```,```npm```,```rustc```,```cargo```这行工具已经安装.然后执行
```
cd ~/.vim/bundle/YouCompleteMe
./install.py --all
```
