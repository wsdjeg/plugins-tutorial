# termdebug

## 简介

termdebug 是从 Vim 8.1 开始内置的调试插件，仅支持 GDB。

本教程仅在 Linux 下（Ubuntu 16.04）测试通过。

## 安装

将 Vim 升级至 8.1 或以上版本。

GDB 需升级至 7.12 或以上版本。

## 启动

默认情况下需手动加载 termdebug 插件：

```
:packadd termdebug
```

假设我们有一个简单的 helloworld.cpp 文件：

```cpp
#include <iostream>

using namespace std;

int main() {
    cout << "hello world" << endl;
    int in;
    cin >> in;
    cout << "you input " << in << endl;
    return 0;
}
```

我们将其编译为二进制文件 `helloworld`：

```
g++ -g helloworld.cpp -o helloworld
```

现在，我们在 Vim 中启动 termdebug 来调试这个程序：

```
:Termdebug helloworld
```

这时 termdebug 会为我们开三个窗口。
其中， GDB 窗口提供 GDB 原生操作；程序窗口供被调试程序使用，提供 IO 功能；源码窗口提供源码交互。
在 GUI 版本的 Vim （如 gvim）中，源码窗口还提供交互按钮：

![](https://user-images.githubusercontent.com/8697363/40467705-75d69b9e-5f5d-11e8-8f34-8f2345b9c735.png)

我们可以通过 `<Ctrl-W>` 按键切换不同窗口。

## 调试程序

我们既可以在 GDB 窗口中调试，也可以在源码窗口中调试。
GDB 调试常用指令：

```
- file bin   加载名为 bin 的二进制文件 
- CTRL-C     中断程序
- run/r      运行
- next/n     执行当前行，停在下一行 （step over）
- step/s     执行当前行，进入下一层函数 （step in）
- finish     执行直至离开当前函数
- where      显示栈
- continue/c 继续执行
- break/b N  在第 N 行加断点
- break/b f  在函数 f 处加断点
- delete     删除所有断点
```

更多 GDB 使用方法请参考官方文档： https://sourceware.org/gdb/current/onlinedocs/gdb/

在源码窗口中的调试指令：

```
 :Run [args]        运行程序，可带参数 [args]，或沿用上一次运行的参数
 :Arguments {args}  设置下一次运行所用参数

 :Break     在当前行加断点
 :Clear     清除当前行的断点

 :Step      = gdb "step" 
 :Over      = gdb "next"
 :Finish    = gdb "finish"
 :Continue  = gdb "continue"
 :Stop      中断程序
```

如果觉得手动输入调试指令太麻烦，可以在个人的 `.vimrc` 文件中自定义 keymap 来执行这些命令，如用 `<F9>` 来添加断点等。

现在我们来演示一下调试上面的已经加载好的 `helloworld` 程序：

1. 先移动至 GDB 窗口，输入 `b main` 以在 main 函数入口处添加断点；
2. 在 GDB 窗口输入 `r`，程序开始运行，并停在 main 函数入口；
3. 在 GDB 窗口输入 `n`，程序停在 `cout << "hello world" << endl;` 这一行；
4. 移动至源码窗口，输入 `:Continue`，程序继续运行，并在 `cin >> in` 处等待用户输入；
5. 移动至程序窗口（IO窗口），输入数字 3 并回车，可以看到程序输出 `you input 3`，并运行直至结束；
6. 移动至 GDB 窗口，输入 `q`，退出调试。

## 获取帮助文档

在 Vim 窗口中输入 `:h terminal-debug` 阅读详细的帮助文档。

