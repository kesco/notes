# Xposed FrameWork初探

Xposed是一个很出名的Android系统注入框架。依赖于Xposed框架，开发者可以不在修改系统层面的源码的情况下，进行各种Hook。

## 虚拟机安装Xposed

一般来说Xposed都是安装在真机上的，不过我一般平时做开发的时候都喜欢用Genymotion虚拟机，比较快。但是Genymotion的虚拟机是基于X86 AOSP编译的，而且对于Flash的Zip文件支持还是不足的。Genymotion对于Zip文件，拖拽到Genymotion虚拟机的窗口上，只是机械地把Zip文件复制到`/system`的子目录。而对于Flash Zip文件来说，复制之后还需要执行其中的`update-binary`或者`updater-script`。

### [GenyFlash](0)

刚好Xposed的作者针对Genymotion出了一个脚本用于安装Flash Zip包，[GenyFlash](0)。只要git clone下来，执行`install.sh`或者`install.bat`即可。

#### 实现原理

当Genymotion在接收到拖拽文件的时候，会执行`/system/bin`下的两个脚本文件：

- `check-archive.sh`，检查拖拽进来的文件是否是Flash Zip。
- `flash-archive.sh`, 执行文件然后复制文件到制定的目录。

[GenyFlash](0)通过复写这两个文件，使得Genymotion能正确执行Flash Zip。



## Gradle上引入Xposed JAR包

现在，Google已经终止Eclipse的支持了，以后官方只支持Android Studio来开发Android。而Android Studio构建Android应用是依赖于Gradle的。所以我们如果用Android Stuido开发自己的一个Xposed Module的话，则必须通过Gradle来引入Xposed框架。

目前，Xposed的SDK还是以JAR为主，没有相应的Maven，所以

```groovy
dependencies {
	/* 这里JAR包应该以Provided的形式引入 */
    provided fileTree(dir: 'libs', include: ['*.jar'])   
}
```

[0]: https://github.com/rovo89/GenyFlash
