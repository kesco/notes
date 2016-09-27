# C语言宏定义入门 

## 宏基本用法

宏仅仅是在C预处理阶段的一种文本替换工具，编译完之后对二进制代码不可见。基本用法如下：

1. 标识符别名

```c
#define BUFFER_SIZE 1024
```

预处理阶段， `foo = (char *) malloc (BUFFER_SIZE);` 会被替换成 `foo = (char *) malloc (1024);`
宏体换行需要在行末加反斜杠\。

```c
#define NUMBERS 1, \
                2, \
                3
```

预处理阶段 `int x[] = { NUMBERS };` 会被扩展成 `int x[] = { 1, 2, 3 };`

2. 宏函数
 
宏名之后带括号的宏被认为是宏函数。用法和普通函数一样，只不过在预处理阶段，宏函数会被展开。优点是没有普通函数保存寄存器和参数传递的开销，展开后的代码有利于CPU cache的利用和指令预测，速度快。缺点是可执行代码体积大。

```c
#define min(X, Y)  ((X) < (Y) ? (X) : (Y))
```

`y = min(1, 2);` 会被扩展成 `y = ((1) < (2) ? (1) : (2));`

## 宏特殊用法

1. 字符串化(Stringification)

在宏体中，如果宏参数前加个 `#` ，那么在宏体扩展的时候，宏参数会被扩展成字符串的形式。如：

```c
#define WARN_IF(EXP) \
     do { if (EXP) \
             fprintf (stderr, "Warning: " #EXP "\n"); } \
     while (0)
```

`WARN_IF (x == 0);` 会被扩展成：

```c
do { if (x == 0)
    fprintf (stderr, "Warning: " "x == 0" "\n"); }
while (0);
```

这种用法可以用在assert中，如果断言失败，可以将失败的语句输出到反馈信息中。

2. 连接(Concatenation)

在宏体中，如果宏体所在标示符中有##，那么在宏体扩展的时候，宏参数会被直接替换到标示符中。如：

```c
#define COMMAND(NAME)  { #NAME, NAME ## _command }

struct command
{
    char *name;
    void (*function) (void);
};
```

在宏扩展的时候：

```
struct command commands[] =
{
    COMMAND (quit),
    COMMAND (help),
    ...
};
```

会被扩展成：

```c
struct command commands[] =
{
    { "quit", quit_command },
    { "help", help_command },
    ...
};
```

这样就节省了大量时间，提高效率。
