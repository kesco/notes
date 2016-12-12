# 使用Buck构建Android工程

## 安装

### Mac OS X

直接通过`HomeBrew`安装比较方便：

```shell
brew update
brew tap facebook/fb
brew install buck
```

安装好后，如果需要监听文件改动，可以再安装`watchman`。另外也需要设置`ANDROID_HOME`和`ANDROID_NDK`。

## Startup

简单的创建一个初始项目:

```shell
touch .buckconfig && buck quickstart
```

创建Intellij Idea的IDE配置文件：

```shell
buck project --ide IntelliJ
```

不过测试了下，Buck产生的配置文件还是有点小问题，Android Studio打开项目后会出现资源没有找到的问题，所以Buck对IDE的支持还是不咋地。

## 变通方案-OKBuck

