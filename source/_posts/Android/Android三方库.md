---
title: Android三方库
date: 2019-10-18 13:03:15
tags:
categories: Android
---

# Android Studio 2.3

## Android Butterknife(黄油刀)

ButterKnife是一个专注于Android系统的View注入框架，减少findViewById来找View对象，使用ButterKnife对性能基本没有损失，因为ButterKnife用到的注解并不是在运行时反射的，而是在编译的时候生成新的class

ButterKnife项目地址：https://github.com/JakeWharton/butterknife

* ButterKnife的优势

> 1、强大的View绑定和Click事件处理功能，简化代码，提升开发效率
>
> 2、方便的处理Adapter里的ViewHolder绑定问题
>
> 3、运行时不会影响APP效率，使用配置方便
>
> 4、代码清晰，可读性强

* ButterKnife的基本配置

在android Studio项目中配置使用ButterKnife

1、 在Project的 build.gradle 中添加如下代码：

```Java
buildscript {
    repositories {
        jcenter()
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:2.3.3'
        classpath 'com.jakewharton:butterknife-gradle-plugin:8.8.1'  // 添加这一行
    }
}
```

2、 在App的 build.gradle 中添加如下代码：

```Java
apply plugin: 'com.jakewharton.butterknife'
```

dependencies中添加：

```Java
compile 'com.jakewharton:butterknife:8.8.1'
annotationProcessor 'com.jakewharton:butterknife-compiler:8.8.1'
```

* ButterKnife的使用

> 1、在Activity 类中绑定 ：ButterKnife.bind(this);必须在setContentView();之后绑定；且父类bind绑定后，子类不需要再bind。
>
> 2、在非Activity 类（eg：Fragment、ViewHold）中绑定： ButterKnife.bind(this，view);这里的this不能替换成getActivity（）。
>
> 3、在Activity中不需要做解绑操作，在Fragment 中必须在onDestroyView()中做解绑操作。
>
> 4、使用ButterKnife修饰的方法和控件，不能用private or static 修饰，否则会报错。错误: @BindView fields must not be private or static. (com.zyj.wifi.ButterknifeActivity.button1)
>
> 5、setContentView()不能通过注解实现。（其他的有些注解框架可以）
>
> 6、使用Activity为根视图绑定任意对象时，如果你使用类似MVC的设计模式你可以在Activity 调用ButterKnife.bind(this, activity)，来绑定Controller。
>
> 7、使用ButterKnife.bind(this，view)绑定一个view的子节点字段。如果你在子View的布局里或者自定义view的构造方法里 使用了inflate,你可以立刻调用此方法。或者，从XML inflate来的自定义view类型可以在onFinishInflate回调方法中使用它。

待续。。。。。。

## Logger(日志打印)

Logger项目地址：https://github.com/orhanobut/logger

配置：

```Java
compile 'com.orhanobut:logger:2.0.0'
```

初始化

```Java
Logger.addLogAdapter(new AndroidLogAdapter());

// 日志适配器通过检查此功能来检查是否应打印日志。如果要禁用/隐藏日志以进行输出，请重写isLoggable方法。 true将打印日志消息，false将其忽略
Logger.addLogAdapter(new AndroidLogAdapter() {
  @Override public boolean isLoggable(int priority, String tag) {
    return BuildConfig.DEBUG;
  }
});

```

使用

```Java
Logger.d("hello");
```
