# Effective C++

摘录网上的片段和自己的一些心得。

## `struct` VS. `class`

除了名字不同之外， `class` 和 `struct` 唯一的差别是：默认可见性。这体现在定义和继承时。 `struct` 在定义一个成员，或者继承时，如果不指明，则默认为 `public` ，而 `class` 则默认为 `private` 。

但这些都不是重点，重点在于定义接口和继承时，冗余 `public` 修饰符总让人不舒服。简单设计四原则告诉告诉我们，所有冗余的代码都应该被剔除。

但很多人会认为 `struct` 是 *C* 遗留问题，应该避免使用。但这不是问题，我们不应该否认在写 *C++* 程序时，依然在使用着很多 *C* 语言遗留的特性。关键在于，我们使用的是 *C* 语言中能给设计带来好处的特性，何乐而不为呢？

正例：

```c++
// hamcrest/SelfDescribing.h
#ifndef OIWER_NMVCHJKSD_TYT_48457_GSDFUIE
#define OIWER_NMVCHJKSD_TYT_48457_GSDFUIE

struct Description;

struct SelfDescribing
{
    virtual void describeTo(Description& description) const = 0;
    virtual ~SelfDescribing() {}
};

#endif
```

反例：

```c++
// hamcrest/SelfDescribing.h
#ifndef OIWER_NMVCHJKSD_TYT_48457_GSDFUIE
#define OIWER_NMVCHJKSD_TYT_48457_GSDFUIE

class Description;

class SelfDescribing
{
public:
    virtual void describeTo(Description& description) const = 0;
    virtual ~SelfDescribing() {}
};

#endif
```

更重要的是，我们确信“抽象”和“信息隐藏”对于软件的重要性，这促使我将 `public` 接口总置于类的最前面成为我们的首选， `class` 的特性正好与我们的期望背道而驰(`class` 的特性正好适合于将数据结构捧为神物的程序员，它们常常将数据结构置于类声明的最前面。)

不管你信仰那一个流派，切忌不能混合使用 `class` 和 `struct` 。在大量使用前导声明的情况下，一旦一个使用 `struct` 的类改为 `class` ，所有的前置声明都需要修改。

## POD(Plain Old Data Structure)

POD是C++里定义的一个兼容C Struct的内存数据结构。

## std::string用法

## Windows的Dll宏

`__declspec(dllexport)`是标志着这个方法或类要从DLL提供给用户调用。
`__declspec(dllimport)`是标志申明要从DLL引用方法或者类，有助于编译器优化。

## C++11新特性

### 新的using用法

现在`using`可以替代`typedef`的功能：

```c++
using string = std::string;
```
