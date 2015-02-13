title: Vim常用命令分享PPT
author:
  name: 邢秀东
  email: xingxiudong@gmail.com
  url: http://xingxiudong.com
output: vim-common-command-ppt.html
controls: true
encoding: utf-8
theme: jdan/cleaver-retro
---

# Vim常用命令分享
## Vim常用命令入门及深入
--

### 内容提纲
* 引言
* 入门篇
* 进阶篇
* 高级篇
* 附：命令模式下常用命令
---

### 引言
* 读者群体
* 为什么要使用vim？
* 提前准备
---

### 读者群体
* 经常与linux打交道的人
* 程序猿、攻城狮、技术狂
* 对vim感兴趣的人
---

### 为什么要使用vim？
* 操作简洁、高效
* 跨平台
* 编程式编辑
* 优秀的工具和文档 vimtutor
---

### 提前准备
* 学习曲线陡峭
* 身心是痛苦的
* 需要时间
* 不断练习和磨练
---


# 入门篇
* 工作模式
* 基本命令
---

### 工作模式
1. Normal模式     Esc
2. 插入模式         i
3. 命令模式         :
4. 可视化模式     v，V，Ctrl-v
---

### 基本命令
* 移动光标
             ^
             k              Hint:  h 键在左边，左移.
       < h       l >               l 键在右边，右移.
             j                     j 键看上去像一个向下的箭头，下移.
             v
--
* 编辑
        i
* 撤销和重做
        u, Ctrl-R
* 保存和退出
        :w, :q, :x
--


# 进阶篇
* 快速移动光标
* 快速编辑
* 复制和粘贴
* 查找和替换
--

### 快速移动光标
以下操作在Normal模式下执行，按Esc进入。
* 行内移动光标
        ^, $, 0
        w, W
		b, B
		e, E
        f, F
		2f{X}, {n}F{X}
* 行间移动光标
        {n}G, G
        gg                	→ =1G
--
* 按匹配括号移动光标（“(” “)”，“[” “]”，“{” “}”等等）
        %
* 屏内移动光标
        H, M, L
* 按句移动光标
        (, )
* 按代码块“{” “}”移动光标（要求“{”或“}”独占一行）
        [[, ]]
--
* 移动光标至上次停留的位置
		''                 	→ 两个单引号
* 移动光标至上次上一次的修改行
		'.
* 移动光标至上次上一次的修改点
		`.
--

### 快速编辑
* 进入编辑模式
        I, i
        a, A
        x, X
        d, D(=d$)
        c, C(=c$)
        r, R
* 快速删除
        dd, dw, de, d{n}w, df{char}, dt{char}, {n}dd, dgg, d{n}gg, dG, ...
        cc, cw, ce, c{n}w, cf{char}, ct{char}, {n}cc, cgg, c{n}gg, cG, ...
--
* 重复操作
        .
        {n}.
* 大写和小写
        gU	 				→ 变大写命令
        gu	 				→ 变小写命令
* 更快
        <start position><command><end position>
          	 				→ command可以是d, y, gU, gu...
        0y$
--

### 复制和粘贴

* 复制
        yy, yw, ye, y{n}w, yf{char}, yt{char}, {n}yy, ygg, y{n}gg, yG, ...
        Y(=yy)
* 粘贴
        p, P
--

### 查找

* 向后查找
        /
* 向前查找
        ?
* 查找下一个
        n, N
--

### 替换
		:s/{old}/{new}	 	→ 替换当前行第一个{old}为{new}
		:s/{old}/{new}/g   	→ 替换当前行所有的{old}为{new}
		:s/{old}/{new}/c   	→ 替换当前行所有的{old}为{new}, 每次提醒

		:%s/{old}/{new}    	→ 替换所有行的{old}为{new}
		:{start-row-num},{end-row-num}s/{old}/{new}
						   	→ 替换{start-row-num}行至{end-row-num}行的{old}为{new}
		:{n},$s/{old}/{new}	→ 替换替换第{n}行开始到最后一行中每一行所有的{old}为{new}
		
		:s#{old}#{new}     	→ / 不会作为分隔符
--

# 高级篇
* 翻页
* 移动屏幕
* 书签
* 宏
* visual模式
* 列编辑
* 分屏
* 其他
--

### 翻页

* 向上翻页
		Ctrl + f  	     	→ (page forword)向下整页翻页
* 向下翻页
		Ctrl + b  	     	→ (page backward)向上整页翻页
* 向上翻半页
		Ctrl + u  	     	→ (page up)向上翻半页
* 向下翻半页
		Ctrl + d  	     	→ (page down)向下翻半页
--

### 移动屏幕

* 移动屏幕，使光标所在行位于屏幕中间
		zz
* 移动屏幕，使光标所在行位于屏幕顶部
		zt
* 移动屏幕，使光标所在行位于屏幕底部
		zb
--

### 书签

* 设定书签
        m{a-z}            	→ 小写字母应用域为单个文件，大写字母可应用域为全局
* 跳转到书签
        `{a-z} 或 '{a-z}
* 查看书签
		:marks
--

### 宏

* 录制宏
        开始录制：q{a-z}
        完成录制：q
* 播放宏
        @{a-z}
        @@
--
宏的演示示例：

		qaYp<Ctrl-a>q
		@a
		@@
		100@@
--

### visual模式
    v, V
    Ctrl + v

列编辑
    （Ctrl + v）  +  I 
--

### 分屏
    :split
    vsplit
    Ctrl + w, Ctrl + w + (←↓↑→)  切换分屏
--

### 其他

* 寄存器
        "{a-Z}, {A-Z}
* 获取系统剪贴板
        "+ 或 "*
--

# 附：命令模式下常用命令
--

* 跳转到指定行
		:{int-number}      	→ 跳转到行号为{int-number}的行
* 设置显示行号
		:set number        	→ 显示行号
		:set nonumber      	→ 隐藏行号
		:set number!       	→ 显示/隐藏行号
* 设置语法高亮
		:syntax on         	→ 开启语法高亮
		:syntax off        	→ 关闭语法高亮
--

* 设置显示不可见字符
		:set list          	→ 显示不可见字符, 把制表符显示为^I, 用$标示行尾
		:set nolist        	→ 隐藏不可见字符
* 搜索设置
		:set ignorecase    	→ 设定查找时忽略大小写
		:set noignorecase  	→ 取消查找时忽略大小写的设定
		:set hlsearch      	→ 设置高亮搜索的匹配结果
		:set nohlsearch    	→ 取消搜索高亮设置
--

* 设置文件格式
		:set fileformat    	→ 显示当前文件格式
		:set fileformat={format}
				           	→ 设置当前文件格式
* 设置文件编码
		:set encoding      	→ 显示当前文件编码
		:set encoding={encoding}
				           	→ 设置当前文件格式

> 这些set命令一般都有简写形式，如 set number! 可简写为 set nu!
--

### 结束语

* 本文使用的vim版本是：version 7.2.411
* 上面讲到的只是常用的命令，还有更多更高级的功能没有提到。
* 经常学习新的命令，多操作。
* 经常和Linux打交道的人学习使用vim能提高工作效率。
* 再也不怕裸系统了。
--


### 参考资料
* [《简明 Vim 练级攻略》](http://www.cnblogs.com/wrmfw/archive/2011/09/08/2170465.html)
* [Graphical vi-vim Cheat Sheet and Tutorial](http://www.viemu.com/a_vi_vim_graphical_cheat_sheet_tutorial.html)
--

# END
## THANK YOU！
--