  # vdebug
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


  ## 参考配置

   # TODO
