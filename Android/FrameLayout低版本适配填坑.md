# FrameLayout低版本适配填坑

在Android 2.X系列里，`FrameLayout`有个Bug，就是`FrameLayout`默认是没有设置`layout_gravity`的，导致`margin`不起效果，所以做低版本适配的时候要在XML上加上`Android:layout_gravity=""`或者直接在代码加上(以左上排列)：

```java
MarginLayoutParams marginParams = new MarginLayoutParams(this.getLayoutParams());
marginParams.height = this.getMeasuredHeight();
marginParams.width = this.getMeasuredWidth();
marginParams.setMargins(l,t,r,b);
LayoutParams layoutParams = new LayoutParams(marginParams);
layoutParams.gravity = Gravity.TOP|Gravity.LEFT;
this.setLayoutParams(layoutParams);
```