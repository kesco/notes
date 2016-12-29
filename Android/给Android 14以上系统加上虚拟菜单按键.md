# 给Android 14以上系统加上虚拟菜单按键

`Options Menu`在Android 2.3以后就被Deprecated了，如果TargetSDKVersion设置了11以上，就没法在虚拟按键区显示菜单键了。

看了下Android源码，发现系统显示虚拟菜单键的逻辑在`PhoneWindow.generateLayout`方法上的：

```java
final Context context = getContext();
final int targetSdk = context.getApplicationInfo().targetSdkVersion;
final boolean targetPreHoneycomb = targetSdk < android.os.Build.VERSION_CODES.HONEYCOMB;
final boolean targetPreIcs = targetSdk < android.os.Build.VERSION_CODES.ICE_CREAM_SANDWICH;
final boolean targetPreL = targetSdk < android.os.Build.VERSION_CODES.LOLLIPOP;
final boolean targetHcNeedsOptions = context.getResources().getBoolean(
                R.bool.target_honeycomb_needs_options_menu);
final boolean noActionBar = !hasFeature(FEATURE_ACTION_BAR) || hasFeature(FEATURE_NO_TITLE);

if (targetPreHoneycomb || (targetPreIcs && targetHcNeedsOptions && noActionBar)) {
    setNeedsMenuKey(WindowManager.LayoutParams.NEEDS_MENU_SET_TRUE);
} else {
    setNeedsMenuKey(WindowManager.LayoutParams.NEEDS_MENU_SET_FALSE);
}
```

从源码上可以看出`setNeedsMenuKey`是打开虚拟按键的API，但是这个API不是public的，所以我们只有通过反射来调用它了。