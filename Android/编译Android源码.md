# 编译Android源码

## 系统要求

如果是在Mac OSX 10.12上，编译Android 6.0和7.0是最方便的了，低版本因为JDK和Xcode的限制，要修改编译文件，比较麻烦。

### 文件系统

OS X默认的文件系统是不区分大小写的，所以要编译AOSP，要自己设置一个区分大小写的分区，或者像我一样直接把整个系统的分区都改成区分大小写的。

### 其他依赖

对于10.12以上的系统，需要安装三个依赖就可以了：

```shell
brew install gnupg sdl 
brew install curl --with-openssl
```

AOSP编译过程中，需要SSL传输，所以需要用brew安装支持SSL的curl，在编译过程中：

```shell
export PATH=$(brew --prefix curl)/bin:$PATH
```

## 编译

```shell
source build/envsetup.sh
lunch # 选择要build的target
make -j4
```

## 浏览源码

生成Android Studio的项目文件：

```shell
mmm development/tools/idegen/
development/tools/idegen/idegen.sh
```