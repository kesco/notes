# Xposed FrameWork初探

Xposed是一个很出名的Android系统注入框架。依赖于Xposed框架，开发者可以不在修改系统层面的源码的情况下，进行各种Hook。

## Gradle上引入Xposed JAR包

现在，Google已经终止Eclipse的支持了，以后官方只支持Android Studio来开发Android。而Android Studio构建Android应用是依赖于Gradle的。所以我们如果用Android Stuido开发自己的一个Xposed Module的话，则必须通过Gradle来引入Xposed框架。

目前，Xposed的SDK还是以JAR为主，没有相应的Maven，所以

```groovy
dependencies {
	/* 这里JAR包应该以Provided的形式引入 */
    provided fileTree(dir: 'libs', include: ['*.jar'])   
}
```

