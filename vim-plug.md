# junegunn/vim-plug 多线程，轻量，可靠的vim插件管理程序

* 安装方法：[下载 plug.vim](https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim) 到"autoload"目录。

* 配置：在你的 `~/.vimrc` (or `~/.config/nvim/init.vim` for Neovim)中添加vim-plug 区段:

1. 区段开始于 `call plug#begin()`
2. 在 `Plug` 命令后列出需要管理的插件地址
3. 区段结束于`call plug#end()` 

* 配置示例：
```
call plug#begin('~/.vim/plugged')

" 使用简化地址; 获取 https://github.com/junegunn/vim-easy-align
Plug 'junegunn/vim-easy-align'

" 允许任何有效的地址
Plug 'https://github.com/junegunn/vim-github-dashboard.git'

" 多个插件可以写在一行，用|分隔
Plug 'SirVer/ultisnips' | Plug 'honza/vim-snippets'

" 按需加载
Plug 'scrooloose/nerdtree', { 'on':  'NERDTreeToggle' }
Plug 'tpope/vim-fireplace', { 'for': 'clojure' }

" 使用非Master分支
Plug 'rdnetto/YCM-Generator', { 'branch': 'stable' }

" 使用标记的版本；允许通配符（需要git 1.9.2或以上）
Plug 'fatih/vim-go', { 'tag': '*' }

" 插件选项
Plug 'nsf/gocode', { 'tag': 'v.20150303', 'rtp': 'vim' }

" Plugin outside ~/.vim/plugged with post-update hook
Plug 'junegunn/fzf', { 'dir': '~/.fzf', 'do': './install --all' }

" 自定义插件 (手动安装及更新)
Plug '~/my-prototype-plugin'

" 初始化插件管理器
call plug#end()
```
* 配置完成后初次使用 重新载入 .vimrc 然后键入命令 `:PlugInstall` 安装插件.

* 命令列表

| 命令                                 | 描述                                                               |
| ----------------------------------- | ------------------------------------------------------------------ |
| `PlugInstall [name ...] [#threads]` | 安装插件                                                            |
| `PlugUpdate [name ...] [#threads]`  | 安装或升级插件                                                       |
| `PlugClean[!]`                      | 移除没用的目录                                                       |
| `PlugUpgrade`                       | 升级 vim-plug 插件管理器                                             |
| `PlugStatus`                        | 检查插件状态                                                         |
| `PlugDiff`                          | 对比插件版本的差异                                                    |
| `PlugSnapshot[!] [output path]`     | 生成用于恢复当前插件快照的脚本                                          |
