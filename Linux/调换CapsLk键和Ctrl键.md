# 调换CapsLk键和Ctrl键

Capslk键一般都是用来做键盘大小写切换的，作为一个平时我们用的不多，但是又占据键盘上一个黄金位置的功能键来说，这是很不妥的，尤其是对于Vim和Emacs这些用户，所以一般来说很多人都把Capslk和Ctrl键替换掉。因为我Linux、Win和Mac OSX都用过，所以每个系统我都知道替换的方法，下面就让我们总结一下怎么替换。

## Windows系列

最近在使用Windows 10，虽然网上有很多软件都可以替换键位，但是最好的方法，还是自己修改注册表。

1. 打开Win下的注册表应用。
2. 跳转注册表条目到：`HKEY_LOCAL_MACHINE -> System -> CurrentControlSet -> Control -> KeyBoard Layout`，注意是Keyboard Layout，而不是KeyBoard Layouts。
3. 新建一个二进制值，`Scancode Map`，值为：

```
0000  00 00 00 00 00 00 00 00       
0008  03 00 00 00 1d 00 3a 00
0010  3a 00 1d 00 00 00 00 00
0018
``` 
4. 保存注册表，重启即可。

