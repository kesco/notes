# Effective C

## do {} while(0)

C语言没有像 `C++` 和 `Java` 那样的异常捕捉机制，一般来说都是利用返回值判断是否发生异常或者用goto做异常处理跳转，不过这两种方法都有缺点，比如代码冗余和容易出错等等。所以，这里有个利用 `do {} while(0)` 的小技巧，直接看代码吧。

```c
bool Execute()
{
  // 分配资源
  int *p = (int *) malloc(sizeof(int));
  bool bOk(true);
  do
  {
    // 执行并进行错误处理
    bOk = func1();
    if(!bOk) break;

    bOk = func2();
    if(!bOk) break;

    bOk = func3();
    if(!bOk) break;
    // ..........
  } while(0);
    // 释放资源
    free(p);
    p = NULL;
    return bOk;
}
```

这样，就不需要重复使用 `goto` 了。

## 指针和数组的区别


