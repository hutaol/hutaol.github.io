---
title: OC-Keywords
date: 2018-11-09 12:53:32
tags: OC
categories: Objective-C
---

> 关键字 `nullable` `nonnull` 【未完】

<!-- more -->

## 关键字

## `nullable`和`nonnull`

iOS9新出的关键字：用来修饰属性 方法的参数和返回值

### 在属性中使用`nullable`和`nonnull`

`nullable`: 表示修饰的属性或参数可以为空

`nonnull`:非空，表示修饰的属性或参数不能为空

**注意：`nonnull`，`nullable`只能修饰对象，不能修饰基本数据类型**

3种写法：

```OC
@property (nonatomic, strong, nullable) NSString * name;
@property (nonatomic, strong) NSString *_Nullable name;
@property (nonatomic, strong) NSString *__nullable name;
//
@property (nonatomic, strong, nonnull) NSString * price;
@property (nonatomic, strong) NSString *_Nullable name;
@property (nonatomic, strong) NSString *__nullable name;
```

### 在方法中使用`nullable`和`nonnull`

```OC
- (nullable NSString *)buyBook:(nullable NSString *)book;
- (NSString *__nullable)buyBook:( NSString *__nullable)book;
- (NSString *_Nullable)buyBook:( NSString *_Nullable)book;
```

### `Nonnull`区域设置(Audited Regions)

宏定义

```OC
NS_ASSUME_NONNULL_BEGIN
@property (nonatomic, strong) NSString * name;
...
NS_ASSUME_NONNULL_END
```

之间定义的所有属性和方法参数和返回值默认加上`nonnull`修饰

为了**安全**起见，苹果还制定了几条**规则**：

> 1.typedef定义的类型的nullability特性通常依赖于上下文，即使是在Audited Regions中，也不能假定它为nonnull。  
> 2.复杂的指针类型(如id)必须显示去指定是nonnull还是nullable。例如，指定一个指向nullable对象的nonnull指针，可以使用`__nullable id * __nonnull`。  
> 3.我们经常使用的`NSError` 通常是被假定为一个指向nullable NSError对象的nullable指针。

### null_resettable

**`null_resettable`: get方法:不能返回为空，set方法可以为空**

```OC
 @property (nonatomic, strong, null_resettable) NSNumber * number;
```

当属性策略中使用了`null_resettable`修饰，就必须保证该属性的get方法返回不为空，否则编译器会如上图那样报警告⚠️。可以在set方法或get方法中做非空处理，以下是在get方法中做处理：

```OC
- (NSNumber *)number {
    if (_number == nil) {
        _number = @11;
    }
    return _number;
}
```

### null_unspecified

**`null_unspecified`:不确定是否为空,使用方式有三种：**

```OC
// 方法一
@property(nonatomic,strong) NSNumber *_Null_unspecified height;
// 方法二
@property(nonatomic,strong) NSNumber *__null_unspecified height;
// 方法三
@property(nonatomic,strong,null_unspecified) NSNumber * height;
```
