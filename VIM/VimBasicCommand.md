# Vim Basic Opearations
## 插入命令
- **I** : 在当前行的行首插入
- **cl** : Change the char at the cursor
- **cw** : Change the word at the cursor
- **cc** : Change the current line

## 光标定位移动命令
- **H** : 光标定位到屏幕上最上面一行
- **M** : 光标定位到屏幕中间一行
- **L** : 光标定位到屏幕最下面一行
- **zEnter** : The current line will be the frist line on the screen
- **z-** : The current line will be the last line on the screen
- **n或者nG** : 光标定位到文件第n行
- **set nu 或者 set number** : 设置行号
- **set nonu** : 取消行号显示
- **(** : 向前移动一个句子
- **)** : 向后移动一个句子
- **{** ：向前移动一个段落
- **}** ：向后移动一个段落
- **fchar** : 向后移动到本行第一个字符char所在的位置
- **Fchar** : 向前移动到本行第一个字符char所在的位置
- **Ctl-d** : 屏幕向下移动半页
- **Ctl-u** : 屏幕向上移动半页
- **Ctl-f** : 屏幕向下移动一页
- **Ctl-b** : 屏幕向上移动一页
- **Ctl-o** : 光标移动到上次编辑的位置

## 删除命令
- **x** : 删除光标后面的字符
- **X** : 删除光标之前的字符
- **dl** : Delete the char at the cursor
- **dt char** : 删除从光标处到字符char的一段字符
- **nx** : 删除光标之后的n个字符
- **D** : 删除光标位置到行尾的所有内容
- **dw** : 删除光标处所在的单词
- **dG** : 删除光标位置开始到文件末尾的所有内容
- **n1,n2d** : 删除n1行到n2行之间的内容，包括n1,和n2行

## Copy & Paste
- **yy or Y** : Copy current line, also could used as **nyy or nY**
- **yl** : Copy the char at the cursor 
- **yw** : Copy the word at the cursor

## Visual Operations
- **v** : 字符选择，选中的地方会反白
- **V** : 行选择，选中的地方会反白
   - **y** : 复制选中的地方
   - **d** : 删除选中的地方
   - **J** : 将选中的行变为一行
   - **< or >** : 左右缩进
   - **=** ：自动缩进（很好用）

## 分屏操作
- **Ctrl-H,J,K,L** : 上下左右进行分屏切换

## 多文件编辑
- **:bn or :bp (,bn or ,bp)** :
  同时打开多个文件，使用这两个命令来切换下一个或者上一个文件,或者使用（**:n or
  :N)
- **:rew** : 回到第一个文件
- **n#** : 调到前一个文件
- **:ls:: : 列出正在编辑的所有文件
- **:bd** : 关闭当前文件
- **:bd!** : 强制关闭当前文件

## 打开，保存，退出
- **:e path** : 打开一个文件
- **:w** : 存储
- **:wa or :wall** : 存储所有的文件
- **:saveas path** : 另存为
- **:x or :wq** : 保存并退出
- **ZZ** : 保存并退出
- **:qa** : 关闭所有文件

## 外界交互
- **:shell** : 暂时进入shell, 当输入exit的时候退出


## Shortcuts for MyVim
- **,ee** : 快速打开 ```~/.vimrc```
- **,sc** : 快速打开vim 快捷键和配置说明
- **za or space** : 折叠代码







## Vbundle Plugin Managers
- 插件配置格式
   - ```Plugin 'user/plugin'```
    - 从Github上进行安装

   - ```Plugin 'plugin_name```
    - 从http://vim-scripts.org/vim/scripts.html上进行安装

   - ```Plugin 'git://git.another_repo.com/plugin'```
    - 从另一个git软件库进行安装

   - ```Plugin 'file://home/user/path/to/plugin'```
    - 从本地文件夹进行安装
   
   - ```Plugin 'rstacruz/sparkup',{'rtp':'another_vim_path'}```
    - 指定其他的参数，比如插件运行的路径，如果是自己在编写插件，或者想从不是```~/.vim```的另一个文件夹来安装它

   - ```Plugin 'User/plugin',{'name':'newPlugin'}
    - 存在同名插件的情况下，可以更名插件，这样就不会冲突了

- 常用插件管理命令
   - ```:PluginInstall``` : 安装所有的插件
   - ```:PluginInstall <plugin-name>``` : 安装指定的插件
   - ```:PluginClean``` : 清理闲置的插件
   - ```:PluginSearch <text-list>``` : 插件搜索H

## NERDTree 操作
### 快捷键
- **F2** : 打开或关闭文件目录

### Global Commands
- **:NERDTree <dirs_paths/bookmark>** : 打开一个新的Tree，根节点自己制定目录或书签，默认为当前目录
- **:NERDTreeCWD** : 当前目录为根目录，并打开一个新的Tree.

### Bookmarks
- **:Bookmark <name>** : 为当前文件或目录设置标签名，没有指定名称则为本来的文件名或者目录名
- **:BookmarkToRoot <name>**  : 使用该标签作为新的根目录并打开一个Tree
- **:OpenBookmark <name>** : 打开一个标签（必须指定为文件）
- **:ClearBookmarks <name>** : 删除标签，没有指定，则删除该节点上的所有标签
- **:ClearAllBookmarks** : 删除所有的标签
#### 注意处理无效书签，它和有效书签之间会被一行空格隔开

### ShortCuts
- **O** : 递归打开选中节点下的所有子节点
- **go** : 打开选中的文件，但是光标仍在NERDTree中
- **t** : 在**新的标签页**中打开选中的节点和书签
- **T** : 类似于t, 但是光标仍在当前的标签页
- **i** : 上下分割打开选中的文件
- **gi** : 类似于i, 但是光标在当前标签页
- **s** : 左右分屏，打开选中的文件
- **gs** : 类似于s, 但是光标在当前标签页
- **x** : 关闭选中节点的父节点
- **X** : 递归关闭选中节点下的所有子节点 ？？
- **e** : 编辑当前的目录

- **D** : 删除当前的书签 ??
- **P** : 跳到根节点
- **p** : 跳到当前节点的父节点
- **K** : 跳到同级的第一个节点
- **J** : 跳到同级的最后一个节

- **C** : 将当前节点的父节点左右根节点
- **u** : 将当前节点的父节点设为根节点
- **U** : 类似于u, 但是旧的根节点保持打开状态

- **r** : 递归刷新当前目录
- **R** : 递归刷新当前根节点

- **m** : 显示NERDTree 菜单
- **cd** : 将当前工作目录（CWD)设为选中目录
- **CD** : 将当前工作目录（CWD)设为树的根目录

- **I** : 切换是否显示隐藏文件
- **f** : 切换是否显示文件过滤器
- **F** : 切换是否显示文件
- **B** : 切换是否显示书签表
 
#### Plugin Features


## Tagbar 操作
- **F3** : 打开或关闭

## YCM (YouCompleteMe) 操作
- **Tab, Ctrl-p, Ctrl-n** : 上下选择提示的选项

## ctrlp 操作
- **Ctrl-p** ：Normal模式下进行搜索 

# The END
## Thank you for reading!
