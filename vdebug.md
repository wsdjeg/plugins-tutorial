  # vdebug
   [项目主页](https://github.com/vim-vdebug/vdebug)

  ## 简介

   Vdebug 是一个新颖的,快速且强大的 Vim debugger客户端. 他支持多种语言,
  目前为止已经测试过: ```PHP, Python, Ruby, Perl, Tcl 和 NodeJS```. 其
  接口支持任何使用 **DBGP** 协议的debugger, 比如: PHP的Xdebug.在 vim 的
  Vdebug 帮助文档中有关于上述所有语言的 debugeer 每个方面的设置指导. PS:
  下面我会以 Python 为例列出常用的选项设置.

  ## 安装
   **依赖**:

   - vim 的 Python3 支持, tags 和 signs 支持.(在 Debian 和 Ubuntu 中的 vim-nox 包中包含了以上需求.)


   - 支持 **DBGP** debugger 的语言.比如: ```PHP, Python, Ruby, Perl, Tcl``` 等.

  不用担心,安装过程和其他的 vim 插件是一样的.你可以用下面的方式来安装(或其他方式):


   - 手动安装: 使用以下命令: ```git clone https://github.com/vim-vdebug/vdebug $HOME/.vim```
     然后执行 ```:helptags ~/.vim/doc``` 来生成必要的帮助文档.

   - Pathogen: 执行: ```git clone https://github.com/vim-vdebug/vdebug $HOME/.vim/bundle```
     并在 ```:call pathogen#helptags()``` 后面添加插件信息.

   - 任意插件管理: 根据你的插件管理器使用方法,添加插件信息任何安装.下面以 Vundle 为例:
   在配置文件中加入 ```Plugin 'vim-vdebug/vdebug'``` 然后执行 ```:PluginInstall```.

  ### Python2

   如果你在使用只支持Python2的电脑的话,你可以下载 [1.5版本](https://github.com/vim-vdebug/vdebug/releases/tag/v1.5.2)

  ## 用法

   所有内容均已包含在 vim 的帮助文档中.其包含了从安装到调试,接口解释,选项,远程
   调试等等所有你所需要的内容.
   执行 ```:help Vdebug``` 打开帮助文档

  ### 快速使用指南

   设置任意一个基于 **DBGP** 协议的 debugger.比如 **Xdebug**(详参: ```VdebugSetUp``` )
   按 ```<F5>```开启 Vdebug 让其进入等待传入的状态. 在打开 Debug 引擎后运行你需
   要 Debug 的脚本. 然后 vim 会出现一个新的显示 Debug 接口信息的标签.

   进入 Debug 模式后,下面的这些按键映射会自动启用:

   - ```<F5>``` 开始/运行 (到下一个断点/脚本末尾)
   - ```<F2>``` 步进(将整个子函数视为一句跳过子函数,但是会执行整个子函数)
   - ```<F3>``` 步入(即遇到子函数进入子函数一句句执行)
   - ```<F4>``` 步出(即结合步入模式,在进入子函数中执行过语句后,手动选择进行步出,将会将子函数余下部分视为一句,执行完成后会返回上层函数)
   - ```<F6>``` 停止 debug(结束脚本)
   - ```<F7>``` 从debugger中分离脚本.
   - ```<F9>``` 运行到当前光标位置
   - ```<F10>``` 触发断点
   - ```<F11>``` 显示上下文变量(例如: after"eval")
   - ```<F12>``` 显示当前光标所在变量的详细信息
   - ```:Breakpoint <type> <args>``` 设置任意类型的断点(详参: ```:help VdebugBreakpoints```)
   - ```:VdebugEval <code>``` 显示代码评估结果
   - ```<Leader>e``` 评估在可视模式下高亮的代码段并显示结果

   按下 ```<F6>``` 停止 debug,并关闭 debugger 接口.

   如果你无法连接到 debugger ,那么你应该花点时间来查阅 ```:help Vdebug``` 来配置
   环境.

  ## debugging

   如果你遇到了问题,并想要查阅后台发生的错误,那么使用日志不失为一个好方法.在开
   始调试之前先执行:

   ```
   :VdebugOpt debug_file ~/vdebug.log
   :VdebugOpt debug_file_level 2
   ```

   然后开始调试吧. 你可以随时查阅日志.他提供了调试引擎与 Vdebug 之间的通信信息.

   如果你需要建立一个新的 issues 的话,那么请你把日志上传到 Gist中.因为日志会很大.


  ## 环境设置
   **注意**: 以下内容均为Linux平台.由于作者未提供其他平台的方法,笔者也未就其他
   平台进行测试.所以请其他平台的小伙伴注意点咯.　
  ###　PHP

   PHP　最流行的 **DBGP** 调试器是 **Xdebug**.
   可以通过包管理器比如 yum 来进行安装.当然也可以手动安装.最后也可以通过 pecl来
   进行安装执行
   ```pecl install xdebug```
   完成安装后,他可能会告诉你,需要包含一个运行库(在类 unix 中后缀为 .so, 在 Windows 中后缀为 .dll)
   复制下库文件路径.我们需要把其作为 zend 的扩展.这件事其实可以直接在 php 的 INI
   文件中来完成,但是我选择(注:此处为作者)在 /etc/php5/conf.d 中新建一个文件.
   因为这个目录内的所有 php 配置都可以自动加载.
   把以下内容放入 INI 文件中:

   ```
   zend_extension=/path/to/xdebug.so
   xdebug.remote_enable=on
   xdebug.remote_handler=dbgp
   xdebug.remote_host=localhost
   xdebug.remote_port=9000
   ```

   如果使用的是 Apache 的话,重启下 php 就能正常加载库文件了.可以通过命令行接口
   来进行查看 输入 ```php -v``` 你会看到类似下面这样的信息:

   ```
   with Xdebug v2.2.0, Copyright (c) 2002-2012, by Derick Rethans
   ```

   现在已经可以正常的使用了.但是我(作者)喜欢让命令行调试美观,快捷所以我写了个
   脚本来自动开启调试服务器脚本名字随意,只要自己能记住就行.推荐为 "php-xdebug"
   内容如下:

   ```
   #!/bin/bash
   export XDEBUG_CONFIG="idekey=xdebug"
   /usr/bin/php "$@"
   <
   ```

   然后运行 ```chmod + x``` 改变脚本权限.最好把这个脚本放到 $PATH 中.然后在
   调试时,就可以使用该脚本来替代 php 了.例如: 将 ```php myscript.php``` 替换为
   ```php-xdebug myscript.php``` 来开启调试对话.


  ### Python

   python 有一个独立的命令行调试工具.但是如果你要使用 Vdebug 来进行调试的话,你
   还需要下载一个 **pydbgp** 工具. 该工具作者是 ActiveState.

   可以在 ```https://code.activestate.com/komodo/remotedebugging``` 下载全平台
   的该工具.然后进行解压.

   这个包里面有一个名为 pydbgp 的二进制文件.在我们运行时可以将其放入脚本当中.
   注意这会允许远程调试. 如果你正在使用版本8 或者更新的版本,你需要移动 pythonlib
   中的 dbgp 目录 到 包含 pydbgp 可执行文件的目录中.(推荐: 复制过去).否则的话
   你会遇到 ```No module named dgpg.client``` 的错误.

   调试脚本名为 ```myscript.py``` , 安装下面的方法来运行:

   ```
   python -S path/to/pydbgp -d localhost:9000 myscript.py
   ```

   将 pydbgp 二进制文件加入 path 中.如果未开启 Vdebug 就运行的话,那么会遇到
   ```it cann't connect host``` 的错误.

   **注意**: 当你试着运行 "eval" 时你可能会遇到问题.如果你遇到关于 not providing
   a length 的错误的话,那么你需要 Python 远程调试源码中的 client.py 补丁.(ps:推荐
   看原始文档.这段笔者翻译不好)
   你可以从 https://gist.github.com/3348076 下载该补丁.(**注意** 需要魔法上网)

   使用类 unix 的话,可以通过命令行来安装补丁. 例如:

   ```
   patch dbgp/client.py < client-7.1.0.patch
   ```

   如果以上还未解决的话,请去项目主页提 issues.

   鉴于未接触到使用 ruby 等语言的人,笔者推荐该语言的使用者应该都具有丰富的编程
   经验,可以自己参照文档搞定.那笔者就不啰嗦了.

  ## 参考配置

   默认设置如下:

   ```
   let g:vdebug_options= {
       \    "port" : 9000,             " 监听端口
       \    "server" : '',             " 监听地址
       \    "timeout" : 20,            " 超时时间
       \    "on_close" : 'detach',     " 结束动作
       \    "break_on_open" : 1,       " 决定调试在脚本第一行处结束,或者运行到第一个断点.
       \    "ide_key" : '',
       \    "path_maps" : {},
       \    "debug_window_level" : 0,  " 0 为只显示错误, 1 为信息, 2为调试
       \    "debug_file_level" : 0,    " 值同上
       \    "debug_file" : "",         " 设置调试日志存放位置.此处填入文件路径.
       \    "watch_window_style" : 'expanded',
       \    "marker_default" : '⬦',
       \    "marker_closed_tree" : '▸',
       \    "marker_open_tree" : '▾'
       \}
    ```

   默认按键设置:

   ```
   let g:vdebug_keymap = {
       \    "run" : "<F5>",
       \    "run_to_cursor" : "<F9>",
       \    "step_over" : "<F2>",
       \    "step_into" : "<F3>",
       \    "step_out" : "<F4>",
       \    "close" : "<F6>",
       \    "detach" : "<F7>",
       \    "set_breakpoint" : "<F10>",
       \    "get_context" : "<F11>",
       \    "eval_under_cursor" : "<F12>",
       \    "eval_visual" : "<Leader>e",
       \}
  ```

  文件路径映射:

  文件路径不是问题.你可以使用 "remote_path" 和 "local_path"来使他们彼此兼容.

  假设我们正在调试远程机器上的文件,其路径为 "/home/user/scripts/myscript.php"
  在我的机器上同样的文件路径为"/home/jon/php/myscript.php"　那么我会按照下面的
  方式来设置：

  ```
 let g:vdebug_options.path_maps = {"/home/user/scripts": "/home/jon/php"}
  ```

  当调试器发送文件路径时,交换会自动完成.所以所有的 "/home/user/scripts" 中的
  文件都会被替换为 "/home/jon/php"　中的文件.
  从反方向发送的话，交换也会反过来。(简言之：反之亦然)

  可以在 "path_maps"　字典中添加多组文件路径。
