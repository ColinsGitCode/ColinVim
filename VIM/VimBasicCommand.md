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

## 多文件编辑
- **:bn or :bp** :
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
- **:saveas path** : 另存为
- **:x or :wq** : 保存并退出
- **ZZ** : 保存并退出
- **:qa** : 关闭所有文件

## 外界交互
- **:shell** : 暂时进入shell, 当输入exit的时候退出
