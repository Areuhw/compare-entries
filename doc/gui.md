使用的是custom tkinter。

大致思路是先创建窗口和组件(比如给butthon中添加对应的执行函数)，然后绑定鼠标键盘事件。

可以参考 [官方文档](https://customtkinter.tomschimansky.com/documentation/)。

# 布局

整体采用gird布局方式，不过组件一多可能会互相影响布局，可以尝试使用frame。

[tutorial](https://customtkinter.tomschimansky.com/tutorial/beginner)

[tkinter的grid布局方法及参数图示讲解](https://zhuanlan.zhihu.com/p/435375856?utm_id=0)

# 窗口整体缩放

[Python Tkinter - resize widgets evenly in a window](https://stackoverflow.com/a/24654428)

# 设置和调整窗口位置

[geometry设置位置](https://github.com/TomSchimansky/CustomTkinter/issues/1707)

当你的系统使用非100%缩放时，窗口可能不会在中心位置出现：

[The geometry method behaves incorrectly on 4K monitor](https://github.com/TomSchimansky/CustomTkinter/issues/1075)

解决方法是获取一个缩放数值，手动对窗口属性进行调整，注意有些属性需要取整数：

[scale factor](https://github.com/TomSchimansky/CustomTkinter/issues/1707#issuecomment-1626367034)

[CTk geometry method](https://github.com/TomSchimansky/CustomTkinter/issues/131)

# 打开目录

有一个initialdir参数可以设置默认打开路径。

[Tkinter文件打开](https://deepinout.com/tkinter/tkinter-questions/617_tkinter_opening_file_tkinter.html#)

# button绑定函数时传参

一般情况下只要给butthon绑定函数即可：

```python
button = ctk.CTkButton(
    window,
    command=function
)
```

当需要传参时，可以采用下面的方法：

`command=lambda: function(arg)`

有多个参数可以这样：

`command=lambda x=1, y=2, z=3: function(x, y, z)`

[Python——如何向 Tkinter 按钮命令中传递参数](https://zhuanlan.zhihu.com/p/475384940?utm_id=0)

# 鼠标右键菜单添加命令

[tkinter事件绑定—— 在文本框点击右键弹出“剪切、复制、粘贴 ”菜单选项](https://blog.csdn.net/xue_11/article/details/117574921)

copy函数用的是这个：

[How to make menubar cut/copy/paste with Python/Tkinter](https://stackoverflow.com/questions/8449053/how-to-make-menubar-cut-copy-paste-with-python-tkinter/8450268#8450268)

# 事件绑定

[Python笔记之Tkinter(Key键盘事件)](https://blog.csdn.net/xoofly/article/details/89736152)

[Event types](https://tkdocs.com/shipman/event-types.html)

[tkinter检测窗口关闭](https://deepinout.com/tkinter/tkinter-questions/352_hk_1711665183.html)

# json文件处理

[python 修改json数据中的某个值](https://blog.51cto.com/u_16175432/8077889)

[Python（21）json.dumps()使用indent参数 格式化输出json数据格式](https://blog.csdn.net/weixin_42221654/article/details/128343854)

# 历史路径

采用ComboBox，需要在App类中创建两个self列表变量，分别记录新旧目录打开的路径，然后分类讨论, number是设定的最大记录数量:

```python
if path not in list:
    if len(list) < number:
        list.insert(0, path)
    elif len(list) == number:
        list.insert(0, path)
        list.pop() 
elif path in list:
    index = list.index(path)
    list.pop(index)
    list.insert(0, path)
```

参考了某搜索引擎上AI给出的答案，关键词好像是"python fixed length list"之类的。

# 模式切换

在写某个功能时最好将其封装成一个函数，这样在更改模块时会省事不少。

[CTkSegmentedButton](https://customtkinter.tomschimansky.com/documentation/widgets/segmentedbutton)

# 键盘输入

[Tkinter 如何使用Tkinter库在Python中检测键盘输入](https://deepinout.com/tkinter/tkinter-questions/315_tkinter_detect_key_input_in_python.html)

# 清除文本框

[CTkTextbox](https://customtkinter.tomschimansky.com/documentation/widgets/textbox)

# 关闭脚本

如果条目正在打印，实际上共享队列中已经有很多数据了，所以关闭后文本框还会输出，需要同时清空队列。

[multiprocessing.Process.terminate](https://docs.python.org/3/library/multiprocessing.html#multiprocessing.Process.terminate)

# 主题切换

需要注意源代码是light, dark，需要在App类中进行转换。

[CTk主题](https://github.com/TomSchimansky/CustomTkinter/blob/master/examples/complex_example.py#L151)

# 搜索文本框

需要有一个中间变量存储上一次搜索的内容，然后分类讨论搜索内容是否变化、上一次搜索是否有结果。

[Tkinter 文本搜索方法](https://deepinout.com/tkinter/tkinter-questions/616_tkinter_explain_tkinter_text_search_method.html)

# 搜索高亮

在上一小节中搜索会得到一个相关结果的第一个字符索引，加上搜索字符长度，添加tag即可。

比如搜索“aaabbb”，会返回一个索引“2.1”, 搜索字符长度是

`str(len('aaabbb')`

添加tag

`tag_add("tag_name", '2.1', '2.1+字符长度c')`

[Highlighting a clicked line in an unfocused Tkinter text widget](https://stackoverflow.com/a/8425933)

[Explain Tkinter text search method](https://stackoverflow.com/a/19466754)

[Scroll to text in Tkinter](https://stackoverflow.com/a/24067799)

# 鼠标悬停高亮

得到鼠标悬停行的索引，然后添加tag. 也可以和右键菜单结合，直接悬停右键进行复制。

[Tkinter text that executes functions on click, highlights when cursor hovers](https://stackoverflow.com/a/72408803)

[Text widget indices](https://tkdocs.com/shipman/text-index.html)

# BackSpace删除输入

和悬念高亮很相似，得到最后一行最后一个字符的索引：

```python
end = text_box.index('end-1c lineend')
```

比如3.2，rsplit取后面的数字，只在其 >= 6时删除文本就可以始终显示cmd的输入提示前缀。

# 用VS Code打开文件

上一小节鼠标悬停会得到对应行的索引，使用text box中的get方法得到路径，用code命令打开即可，注意有空格的话需要加双引号。

# 交互限制

输入限制使用ctk widget中的configure方法：

`configure(state='normal')`
`configure(state='disabled')`

脚本重复运行限制需要一个变量记录运行状态，然后if语句分情况。
