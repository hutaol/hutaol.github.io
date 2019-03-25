---
title: OC-Property
date: 2018-12-19 13:19:32
tags:
categories: Objective-C
---

## 属性 @property

@property = 实例变量 + get方法 + set方法

Example
```
@property (nonatomic, copy) NSString *name;
```
属性name生成的setter方法
```
- (void)setName:(NSString *)name;

// rewrite setter
- (void)setName:(NSString *)name {
    _name = name;
}
```
属性name生成的getter方法
```
- (NSString *)name;

// rewrite getter
- (NSString *)name {
    return _name;
}
```

#### 自动合成
> 定义一个@property，在*编译*期间，编译器会*自动*生成*实例变量*、*getter方法*、*setter方法*，这些方法、变量是通过*自动合成*（`autosynthesize`）的方式生成并添加到类中。
实际上，一个类经过编译后，会生成变量列表`ivar_list`和方法列表`method_list`，每添加一个属性，在变量列表`ivar_list`会添加对应的*变量*，方法列表`method_list`会添加对应的*setter*方法和*getter*方法。

对应的代码：
```
@synthesize name = _name;
```
编译器自动生成，无需手动添加

#### 动态合成

```
@dynamic sex;
```
这样代码告诉编译器，sex属性的变量名、getter方法、setter方法由开发者自己来添加，编译器无需处理。

**特别注明：**
> `getter方法中不能用self.,会造成死循环`

```
- (NSString *)name {
    return self.name;  // 错误的写法，会造成死循环
}
```
`self.name`实际上就是执行了属性name的getter方法，getter方法中又调用了`self.name`，会一直递归调用，直到程序崩溃

```
self.name = @"aaa";
```
这样的方式，setter方法会被调用。

### @property修饰符

修饰符有四种：

> 1. 原子性：`nonatomic`、`atomic`：不能绝对保证线程安全，会耗费一些性能，默认`nonatomic`
> 2. 读写权限：`readwrite`、`readonly` 默认`readwrite`
> 3. 内存管理：`assign`、`strong`、`weak`、`copy`、`unsafe_unretained`
> 4. set、get方法名
> 5. 可为空 nullable、nonnull

#### nonatomic非原子性 atomic原子性

不写默认是`atomic`原子性

*区别*：系统自动生成的getter/setter方法不一样。

`atomic`的属性，系统生成的getter/setter会保证get、set操作的完整性，不受其他线程的影响。比如，线程 A 的 getter 方法运行到一半，线程 B 调用了 setter：那么线程 A 的 getter 还是能得到一个完好无损的对象。

`nonatomic`的属性，没有这个保证，`nonatomic`的速度要比`atomic`快

`atomic`并不能保证线程安全。如果线程 A 调了 getter，与此同时线程 B 、线程 C 都调了 setter——那最后线程 A get 到的值，3种都有可能：可能是 B、C set 之前原始的值，也可能是 B set 的值，也可能是 C set 的值。同时，最终这个属性的值，可能是 B set 的值，也有可能是 C set 的值。

*保证数据完整性——这个多线程编程的最大挑战之一*

#### assign

`assion`用于非指针变量。基础数据类型（例如NSInteger）和C数据类型（int、float、double、char等），以及id类型。

用于对基本数据类型进行复制操作，不更改引用计数。也可以用来修饰对象，但是，被`assign`修饰的对象在释放后，指针的地址还是存在的，也就是说指针并没有被置为nil，成为野指针。如果后续在分配到堆上的某块内存时，正好分到这块内存，程序就会crash。之说以可以修饰基本数据类型，因为基本数据类型一般分配到栈上，栈的内存会由系统自动处理，不会造成野指针。

#### weak

`weak`修饰Object类型，ARC下修饰delegate属性

在ARC环境下，所有指向这个对象的weak指针都将被置为nil。
修饰Object类型，修饰的对象在释放后，指针地址会被置为nil，是一种弱


