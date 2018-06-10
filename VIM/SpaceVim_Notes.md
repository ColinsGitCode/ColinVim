# SpaceVim Notes
## 1. Basic Operations
- Notices:
  - 窗口 **Windows :  w**
  - 文件 **Files : f**
  - 缓冲区 **Buffer : b**
  - 标签页 **Tab : t**
  - 搜索 **search : s**
  - 工程 **project : p**
  - 帮助 **help : h**
- Documents:
  - `:h SpaceVim` : 打开SpaceVim的帮助文档

### 1.1 Space
- `Space` **几乎解决了许多快捷键命令的记忆难题**
  - **1秒之后下面会出现一个提示窗口，内部有各种操作选项**
  - 出现提示窗口之后
    - 按`Control-h`之后，可以进行上下翻页，撤销命令的操作
      - `u` : 撤销前一按键
      - `n` : 导航系统的下一页
      - `p` : 导航系统的上一页
  - **按`Esc`键之后就会退出**
### 1.2 Input
- Tips:
  - 输入`vim`打开之后，`e` 打开空文件（新文件） `q` 退出vim
  - `:w filename` 保存这个新的文件
### 1.3 Open Files
- Tips:
  - 输入`vim`之后，输入`:e path/filename` 既可以打开相应的文件
### 1.4 Files Manager
- Tips:
  - `Space f t` : 关闭右侧的文件浏览器，再次输入`Space f t`可以再次打开
  - `F3` 也可以操作文件浏览器
  - `h`和`l`都可以打开和关闭文件夹，`l`用来打开文件
  - `j`和`k`用来上下移动
### 1.5 Buffers
- A opening file as a **Buffer**
- Tips:
  - `Space b b` 列表显示所有打开的文件(buffers)
  - 可以输入文件名进行查询，回车就可以打开指定的文件
  - `Ctrl-p`和`Ctrl-n`来进行上下选择文件
  - 按`Space`可以选中相应的文件，按回车就可以打开这个文件
### 1.6 Windows Manager
- Tips:
  - `Space W /` 可以左右分割窗口
  - `Space w -` 可以上下分割串口
  - 分割窗口之后，光标会在文件管理器，选择要打开的文件，则会在新窗口打开新文件, 此时会有窗口选择，直接输入要选择的窗口的字母即可。
  - **窗口切换**
     - `Space num` 切换至编号指定的窗口
     - `Space w Tab` 顺序切换窗口
### 1.7 Tab Manager
- 打开的文件多了，可以使用`Tab`
- `Space w F` 可以新建一个tab页面
- `Space t t` 可以显示Tab列表
- `j` `k` 可以上下选择Tab
- `Space w o` 可以按顺序切换tab

## 2 Simple Configurations
- SpaceVim的配置文件在：`~/.SpaceVim.d/init.vim`
- 所有自定义的内容都可以放在这个文件中，可以文件夹可以通过git进行管理
- [author's Configurations](https://github.com/everettjf/.SpaceVim.d/blob/master/init.vim)
### 2.1 空格键延迟
- 默认为1s, 可以设置   `set timeoutlen=200`
### 2.2 主题切换
- [可以使用的主题](https://github.com/rafi/awesome-vim-colorschemes)
- `let g:spacevim_colorscheme = 'onedark'`
### 2.3 语言支持
- 有些语言用不到，可以注释掉，保证vim操作的流畅度
### 2.4 字体设置
- 有些字符无法显示，需要配置特定的字体
- [可以使用的字体](https://github.com/ryanoasis/nerd-fonts)
- 安装：
`brew install caskroom/fonts`
`brew cask install font-hack-nerd-font`
- MacVim中的配置：
`let g:spacevim_guifont='Knack\ Nerd\ Font:h12'`
- **Terminal.app**需要单独设置**
- **iTerm2.app**

## 3 Projects Manager
- 工程定义
  - SpaceVim会从当前文件自动向上查找`.git`目录或者`.projections.json`作为根目录
- 输入`Space p`可以看到支持的功能，也可以算是命令教程
### 3.1 模糊查找 fuzzy search
- `Space p /` 启动模糊查找，输入特定字符可以在整个工程中进行查找
   - 得到的结果可以按`j` `k`进行上下选择
   - 按`q`可以退出
### 3.2 Git
- `Space g s` 查看状态
- `Space g A` 添加所有文件
- `Space g S` 添加当前文件
- `Space g c` 设置commit message, 最后`:wq`表示完成并**commit**
- `Space g p` 开始push

## 4 初步进阶
### 4.1 命令行
- `Space !` 打开命令行，但是只能执行一条命令
### 4.2 Terminal
- `:terminal` 打开一个窗口，可以执行terminal
- 在terminal中输入exit之后可以`:q`退出
### 4.3 Python开发环境

## 5 更新
- `:SPUpdate` : 更新SpaceVim以及包含的插件
- `:SPUpdate PluginName` : 更新指定的插件
- `:SPUpdate SpaceVim` : 更新SpaceVim本身

##  其他操作
- 注释 ： `Space c l` 注释或者取消注释选中的行， `Space c` 会出现很多的提示
- 录制宏 ： 和vim的默认配置不一样，已经修改了，在normal模式下，`\ q r`
- TagBar : 安装ctags之后，打开cpp文件，`F2`可以打开TagBar,查看已经定义的函数
- 设置语言支持的类型 ：
- grep当前文件(缓冲区)
   - `Space s s` 可以打开当前打开的文件（缓冲区），执行grep搜索
   - 输入要搜索的字符之后，可以按`esc`，然后就可以按`j``k`来进行上下选择操作了，在想定位的一行进行回车，就可以直接到达指定行
   - 可以按`q`退出

## 卸载
- 只需要在命令行输入如下命令：
``` curl -sLf https://spacevim.org/install.sh | bash -s -- --uninstall ```
