![](1.png)

# 介绍

有两个模式。转移模式适用于想将某一目录重新分类的情况——将其作为新目录，和已分类的旧目录作比较，会忽略隐藏目录和文件，并有以下五项结果：

- 列出旧目录中重复分类的文件(名字或内容相同)

- 旧目录中没有的新文件会归入 `旧目录/new`，重名的文件会以 xxx_1, xxx_2的形式重命名

- 删除`new`中已分类的文件

- 替换更新文件

- 重命名旧目录中和新目录名字不同内容相同的文件

复制模式会对比新旧目录，程序运行后新旧目录会保持一致。

# 功能

- 集成文本框，重定向标准io流
- 嵌入 cmd
- 文本框搜索，并对搜索内容高亮
- 多进程与多线程
- 关闭脚本进程
- 清空文本框内容
- 记忆功能，包括目录路径、窗口尺寸和位置、主题
- 鼠标悬停在路径上时可在右键菜单中选择在 VS Code 打开文件（需将 code 命令加入环境变量）
- 选择部分文本框内容或在鼠标悬停时复制
- 交互限制，限制输入内容、限制重复运行脚本

# 下载

见 [Release](https://github.com/Areuhw/compare-entries/tags)

# 使用

打开新旧目录，点击“转移/复制”切换模式，然后选择比较条目，结果会输出在文本框中，主要以“将被...”的形式分开，比如“将被复制的文件”。如果条目数目大于300耗时会比较长，所以不会直接显示，需要cmd命令确认。

如果选择输出结果到文件的话会导出markdown文件，在VSCode中可以在设置里搜索markdown.preview.open，将打开链接设置为In editor，然后预览导出文件，将其锁定。

目录旁边有一个下拉菜单会显示最近打开的10个路径。程序运行会在所在目录生成`data.json`，里面保存了上次退出程序时的窗口尺寸等数据。

## 鼠标

左键：取消文本框内容选择、取消搜索高亮、聚焦于文本框或搜索框

右键：在文本框中弹出菜单

悬停：在文本框中高亮段落

## 键盘

Y/n：选择是否执行文件操作

O/p：选择将比较结果输出到文件/打印到文本框

BackSpace：删除输入的cmd命令

Help/?：显示命令帮助

回车：在文本框中输入命令后确认、在搜索框中输入内容后进行搜索

r：取消/开启悬停高亮

control + f：聚焦于搜索框

# 协议

此项目使用 [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/legalcode.zh-hans) 协议。第三方材料协议见 [THIRD_PARTIES](/THIRD_PARTIES.md).
