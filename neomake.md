![Neomake](https://cloud.githubusercontent.com/assets/111942/22717189/9e3e1760-ed67-11e6-94c5-e8955869d6d0.png)

# Neomake 配置指南

- 原文链接: [Neomake 配置指南](https://github.com/vim-china/plugins-tutorial/blob/master/neomake.md)

<!-- vim-markdown-toc GFM -->

- [简介](#简介)
- [依赖](#依赖)
  - [neovim](#neovim)
  - [Vim](#vim)
- [安装](#安装)
- [配置](#配置)
- [调试](#调试)

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

如果你想自动配置neomake，可以通过 `neomake#configure#automake` 这个方法在 vimrc 中进行配置:

**分以下四种情况**

- 保存文件时直接进行语法检查，没有延迟

```vim
call neomake#configure#automake('w')
```

- 保存文件时直接语法检查，切换至 `Normal` 模式下滞后 750ms 进行语法检查。

```vim
call neomake#configure#automake('nw', 750)
```


## 调试
