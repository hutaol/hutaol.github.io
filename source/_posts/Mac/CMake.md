---
title: CMake
date: 2022-12-09 11:54:07
tags:
---

> CMake是一个跨平台的安装（编译）工具，支持静态库与动态库的建构，生成可执行文件
> CMake通过CMakeLists.txt配置项目的构建系统，配合使用cmake命令行工具生成构建系统并执行编译、测试，相比于手动编写构建系统（如Makefile）要高效许多

<!-- more -->

### 简单的例子`hello`

1.创建项目

```s
mkdir hello
touch HelloWorld.cpp
touch CMakeLists.txt
```

2.编写`CMakeLists.txt`

```s
project(hello) # 项目名称
add_executable(hello HelloWorld.cpp) # 可执行文件的文件名 指定源文件
```

3.用cmake生成构建系统，Makefile文件

```s
cmake .
```

4.make编译可执行程序`hello`

```s
make
```

### `CMake`命令

`cmake --help`查看`cmake`命令支持的详细参数

常用参数

参数 | 含义
--- | :---
-S | 指定源文件根目录，必须包含一个`CMakeList.txt`文件
-B | 指定构建目录，构建生成的文件的生成路径
-D | 指定变量，-D后面的空格可以省略

比如，指明使用当前目录作为源文件目录，其中包含CMakeLists.txt文件；使用build目录作为构建目录；设定变量CMAKE_BUILD_TYPE的值为Debug，变量AUTHOR的值为Henry

> cmake -S . -B build -DCMAKE_BUILD_TYPE=Debug -DAUTHOR=Henry

1.生成构建系统

```c
cmake -B build
```

2.执行构建

```c
cmake --build build
```

### CMakeLists.txt

参考：<https://gitee.com/RealCoolEngineer/cmake-template>
