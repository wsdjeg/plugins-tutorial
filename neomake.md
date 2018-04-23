![Neomake](https://cloud.githubusercontent.com/assets/111942/22717189/9e3e1760-ed67-11e6-94c5-e8955869d6d0.png)

# Neomake

> 异步编译及语法检查

<!-- vim-markdown-toc GFM -->

- [简介](#简介)
- [依赖](#依赖)
  - [neovim](#neovim)
  - [Vim](#vim)
- [安装](#安装)
- [配置](#配置)
- [命令](#命令)

<!-- vim-markdown-toc -->

## 简介

Neomake 是一个用于异步执行命令的 Vim/Neovim 插件。

你可以使用它替代 Vim 内置命令 `:make`，因为该插件可以检测你的 `'makeprg'` 设置。
但该插件核心功能是根据当前文件类型或者项目类型进行语法检查。它的最初目的是替代 `Syntastic`，并提供异步支持。

## 依赖

### neovim

neomake 支持所有的 neovim release 版本。

### Vim

Neomake 支持最低的 Vim 版本是 v7.4.503, 当然如果你不需要使用 `g:neomake_logfile`，
Neomake 在老版本 Vim 中也许也能正常工作。

Vim 异步支持最低版本为： v8.0.0027

## 安装

可以选择任意插件管理器，比如 dein.vim

```vim
call dein#add('neomake/neomake')
```

## 配置

如果你仅仅需要一个简单的方法来异步运行 `:make`, 你只需要正常设置 `'makeprg'` 和 `'errorformat'`，
然后执行 `:Neomake!` 即可。

如果你想自动配置neomake，可以通过 `neomake#configure#automake()` 这个方法在 vimrc 中进行配置:

**分以下四种情况**

- 保存文件时直接进行语法检查，没有延迟

```vim
call neomake#configure#automake('w')
```

- 保存文件时直接语法检查，切换至 `Normal` 模式下滞后 750ms 进行语法检查。

```vim
call neomake#configure#automake('nw', 750)
```

neomake 还支持为指定文件类型配置专门的检查工具，比如，为 c 文件指定 lint 工具作为maker：

```vim
let g:neomake_c_lint_maker = {
    \ 'exe': 'lint',
    \ 'args': ['%:p', '--option', 'x'],
    \ 'errorformat': '%f:%l:%c: %m',
    \ }
```

## 命令

除了自动运行意外，neomake 还提供了一些命令，以方便手动运行一些命令。

- `:Neomake [makers]` 指定语法检查工具，并对当前文件进行语法检查，缺省时根据当前文件类型自动选择检查工具。
- `:Neomake! [makers]` 指定工具进行全工程语法检查，或者编译，比如编译 Java 工程 `:Neomake! mvn`
- `:NeomakeSh {command}` 异步执行命令，以 quickfix 展示输出结果
- `:NeomakeSh! {command}` 异步执行命令，忽略结果输出
- `:NeomakeInfo` 展示neomake配置信息，用于 debug neomake 配置
