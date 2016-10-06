# React Native学习笔记

最近在折腾RN，做下相关的学习笔记。

## Flex布局

RN的布局参考了`CSS`中的`flexbox`流式布局，大部分属性和`CSS`的相同，只是在某些特性上不一致。

### 默认单位

React设置宽高的时候是不需要自带单位的，根据RN的官方文档说明，默认的布局单位是`dp`，没错，就是`Android`里的`dp`。

### Flex方向

Flex布局在UI的显示平面上划分两个坐标轴，主坐标轴(**primary axis**)和次坐标轴。至于哪个坐标轴是主坐标轴哪个是次坐标轴，则由`flexDirection`属性决定。`flexDirection`默认属性为`column`(列)，其余属性值还有`row`（行)。Flex布局是依照主坐标轴排布元素的。

### justifyContent

`justifyContent`表示元素在主坐标轴方向上的对齐方式。可选值有: `flex-start`, `flex-end`, `center`, `space-between`, `space-around`。

![justifyContent](http://7xksdk.com1.z0.glb.clouddn.com/justifyContent.jpg)

### alignItems

`alignItems`表示调整伸缩项目在侧轴上的定位方式，可选值: `flex-start`, `flex-end`, `center`, `stretch`，默认值为`stretch`。

![alignItems](http://7xksdk.com1.z0.glb.clouddn.com/alignItems.jpg)

### alignSelf

`alignSelf`加在布局元素上会覆盖容器的alignItems属性，取值和用法alignItems一样。可选值: `auto`, `flex-start`, `flex-end`, `center`, `stretch`。

### flexWrap
 
`flexWrap`子元素超出父容器时是否换行，可选值: `wrap`, `nowrap`。

![flexWrap](http://7xksdk.com1.z0.glb.clouddn.com/flexWrap.jpg)
