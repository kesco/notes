# Android列表控件使用心得

## ListView

### 滚动略过Padding

我们都知道ListView可以设置Padding，但是在默认情况下，ListView滚动时Padding的地方还是为空的，所以想滚动的时候略过Padding的话，可以在ListVIew的XML Tag上设置：

```xml
<ListView
    android:clipToPadding="false" />
```
## 共有特性

### 列表项的最低高度

如果你在每个列表项内设置`layout_height`的话，会发现根本不起作用。变通的方法是设置`minHeight`即可。

