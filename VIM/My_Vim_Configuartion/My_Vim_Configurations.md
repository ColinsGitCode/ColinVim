# My Vim Configurations
## 1. Basic Information for Vim Configurations
### 1.1 基础配置
- vim的所有配置都是在 ```~/.vimrc``` 文件中的，**默认没有，需要自己创建**

## 2 Install and Configure step by step
### 2.1 Vbundle （Plugins Manager)
- 一个自动化仓库，专门用于管理各类插件
- **安装** ：
    1. github上直接下载
    ```
      git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim
    ```

    2. 添加相关配置语句到 ```~/.vimrc ``` 文件中
    ```
       " *********************************************
       " Vbundle插件管理                
       " *********************************************
       set nocompatible              " required
       filetype off                  " required

       " set the runtime path to include Vundle and initialize
       set rtp+=~/.vim/bundle/Vundle.vim
       call vundle#begin()        

       " alternatively, pass a path where Vundle should install plugins
       "call vundle#begin('~/some/path/here')

       " let Vundle manage Vundle, required
       Plugin 'gmarik/Vundle.vim'
       " Add all your plugins here (note older versions of Vundle used Bundle instead of Plugin)
       " All of your Plugins must be added before the following line                 
       call vundle#end()            " required
       filetype plugin indent on    " required
    ```
    3. 更新插件：启动vim 之后输入如下命令
    ```
       :PluginInstall
    ```

### 2.2 主题安装
- 有一些 ```runtimepath``` 问题
   - 解决方法 ：
      - 包主题的 .vim 文件放入 ``` ~/.vim/colors ``` 之下

### 2.3 分割布局
- vim 分屏命令
   -  上下分屏 ： ``` :split ```
   - 左右分屏 ： ``` :vsplit ```
- 切屏操作：
   - ``` ctrl-h ``` : 向左切屏
   - ``` ctrl-l ``` : 向右切屏
   - ``` ctrl-k ``` : 向上切屏
   - ``` ctrl-j ``` : 向下切屏
- 配置文件相关配置
   - ```
       " *********************************************
       " 分割布局相关
       " *********************************************
       set splitbelow
       set splitright
       "快捷键，ctrl+l切换到左边布局，ctrl+h切换到右边布局
       "ctrl+k切换到上面布局，ctrl+j切换到下面布局
       nnoremap <C-J> <C-W><C-J>
       nnoremap <C-K> <C-W><C-K>
       nnoremap <C-L> <C-W><C-L>
       nnoremap <C-H> <C-W><C-H>
     ```

### 2.4 代码折叠
- 配置文件相关配置
   - ```
        " 开启代码折叠功能
        " 根据当前代码行的缩进来进行代码折叠
        set foldmethod=indent
        set foldlevel=99
        " 将za快捷键映射到space空格键上
        nnoremap <space> za
     ```

### 2.5 目录树
- 选用 NERDTree 插件，用vbundle来安装
- 添加方法
   1. 在 ``` ~/.vimrc ``` 中加入如下配置项：
      - ```
           Plugin 'scrooloose/nerdtree'
        ```
   2. 添加NERDTree插件相关配置
      - ```
           " *********************************************
           " NERD插件属性
           " *********************************************
           au vimenter * NERDTree   // 开启vim的时候默认开启NERDTree
           map <F2> :NERDTreeToggle<CR>  // 设置F2为开启NERDTree的快捷键
        ```
    3. 执行 ``` :PluginInstall ``` 然后重启 vim

### 2.6 TagBar
- Tagbar可以将正在编辑的文件生成一个大纲，包含类、方法、变量等，可以选中快速跳转到目标位置，编辑大文件的时候特别有用。
- Tagbar的安装需要Ctags的支持，我们首先需要安装用brew来安装Ctags，运行如下命令：
   - ``` brew install ctags ```
- 安装步骤：
   1. 在 ``` ~/.vimrc ``` 中加入如下配置项：
      - ```
          Plugin 'majutsushi/tagbar'
          " 设置开启关闭快捷键
          map <F3> : TagbarToggle<CR>
          " 启动时自动focus
          let g:tagbar_auto_faocus =1
          " 启动指定文件时自动开启tagbar
          autocmd BufReadPost *.py,*.cpp,*.c,*.h,*.hpp,*.cc,*.cxx call tagbar#autoopen()
        ```

### 2.7 自动补全 （ YouCompleteMe )
- 在vim下，最好用的自动补全插件非YouCompleteMe莫属，这款插件支持C、C++、obj-C、C#和python语言的自动补全，有了它，补全各类代码都不用愁了。
- 安装过程：
    1. 安装YCM需要cmake的支持，而且vim的版本需要在7.4以上。首先，我们来安装cmake。
       - ``` brew install cmake ```
    2. 在 ``` ~/.vimrc ``` 中加入如下配置项：
       - ```
           Plugin 'Valloric/YouCompleteMe'
           " *********************************************
           " YCM插件相关
           " *********************************************
           let g:ycm_autoclose_preview_window_after_completion=1
           " 跳转到定义处
           map <leader>g  :YcmCompleter GoToDefinitionElseDeclaration<CR>
           " 默认tab、s-tab和自动补全冲突
           let g:ycm_key_list_select_completion = ['<TAB>', '<c-n>', '<Down>']
           let g:ycm_key_list_previous_completion = ['<S-TAB>', '<c-p>', '<Up>']
           let g:ycm_auto_trigger = 1
         ```
      3. 编译YCM
          - ```
               /* 进入ycm目录 */
               ~ cd .vim/bundle/YouCompleteMe/
               /* 执行编译 */
               ./install.sh --clang-completer
            ```

### 2.8 airline 状态栏插件
- 这个状态栏是由vim-airline插件提供，默认情况下，airline使用ASCII字符来作为状态栏的分隔符， 所以安装完后，会出现一些乱码的情况。可以根据情况自行修改
- 安装方法
    1. 在 ``` ~/.vimrc ``` 中加入如下配置项：
         - ```
             Plugin 'vim-airline/vim-airline'
             Plugin 'vim-airline/vim-airline-themes'

             " *********************************************
             " vim-airline
             " *********************************************
             " 开启powerline字体
             let g:airline_powerline_fonts = 1
             " 使用powerline包装过的字体
             set guifont=Source\ Code\ Pro\ for\ Powerline:h14
           ```




## 快捷键集合
### 基本操作
- Leader Key
   - ``` , ```
- 切屏操作：
   - ``` ctrl-h ``` : 向左切屏
   - ``` ctrl-l ``` : 向右切屏
   - ``` ctrl-k ``` : 向上切屏
   - ``` ctrl-j ``` : 向下切屏
- 代码折叠 （根当前行的缩进来进行代码折叠）
   - ``` space ``` 或者 ```z+a``` 来进行代码的折叠和展开
- 快速编辑 ``` ~/.vimrc ```
   - 快速打开编辑 ``` , - ee ```

### 插件操作
- 更新插件
   - ``` :PluginInstall ``` : 更新所有的插件

### VIM : 命令
- vim 分屏命令
   -  上下分屏 ： ``` :split ```
   - 左右分屏 ： ``` :vsplit ```
- Vim runtimepath 查看
   - ``` set runtimepath ? ```

### NERDTree 基本操作
- ```
    ?: 快速帮助文档
    o: 打开一个目录或者打开文件，创建的是buffer，也可以用来打开书签
    go: 打开一个文件，但是光标仍然留在NERDTree，创建的是buffer
    t: 打开一个文件，创建的是Tab，对书签同样生效
    T: 打开一个文件，但是光标仍然留在NERDTree，创建的是Tab，对书签同样生效
    i: 水平分割创建文件的窗口，创建的是buffer
    gi: 水平分割创建文件的窗口，但是光标仍然留在NERDTree
    s: 垂直分割创建文件的窗口，创建的是buffer
    gs: 和gi，go类似
    x: 收起当前打开的目录
    X: 收起所有打开的目录
    e: 以文件管理的方式打开选中的目录
    D: 删除书签
    P: 大写，跳转到当前根路径
    p: 小写，跳转到光标所在的上一级路径
    K: 跳转到第一个子路径
    J: 跳转到最后一个子路径
    <C-j>和<C-k>: 在同级目录和文件间移动，忽略子目录和子文件
    C: 将根路径设置为光标所在的目录
    u: 设置上级目录为根路径
    U: 设置上级目录为跟路径，但是维持原来目录打开的状态
    r: 刷新光标所在的目录
    R: 刷新当前根路径
    I: 显示或者不显示隐藏文件
    f: 打开和关闭文件过滤器
    q: 关闭NERDTree
    A: 全屏显示NERDTree，或者关闭全屏
  ```







## 补充知识
### Vim的环境变量
- Vim 插件一般安装在5个地方，存放插件的路径都列在 ``` runtimepath ``` 选项中，可以用 **set命令** 查看:
   - ``` :set runtimepath ? ```
   ./configure --with-features=huge \
               --enable-multibyte \
               --enable-rubyinterp \

               --enable-python3interp \
               --with-python3-config-dir=/usr/lib64/python3.5/config \
               --enable-perlinterp \
               --enable-luainterp \
               --enable-gui=gtk2 --enable-cscope --prefix=/usr


               ./configure --with-features=huge -enable-python3interp --with-python3-config-dir=/home/Colin/anaconda3/lib/python3.6/config-3.6m-x86_64-linux-gnu --

               ./configure --with-features=huge --enable-python3interp --enable-rubyinterp --enable-luainterp --enable-perlinterp --with-python3-config-dir=/home/Colin/anaconda3/lib/python3.6/config-3.6m-x86_64-linux-gnu --enable-multibyte --enable-cscope --prefix=/usr/local/vim8/
