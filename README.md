# 2基于跳表结构的KV存储引擎设计

非关系型数据库redis，以及levedb，rockdb其核心存储引擎的数据结构就是跳表。

本项目就是基于跳表实现的轻量级键值型存储引擎，使用C++实现。插入数据、删除数据、查询数据、数据展示、数据落盘、文件加载数据，以及数据库大小显示。

在随机写读情况下，该项目每秒可处理啊请求数（QPS）: 24.39w，每秒可处理读请求数（QPS）: 18.41w

# 什么是跳表

> 这里不做介绍，详见:
>
> - [漫画：什么是 “跳表” ？ - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/200815425)
> - [拜托，面试别再问我跳表了！ - 彤哥读源码 - 博客园 (cnblogs.com)](https://www.cnblogs.com/tong-yuan/p/skiplist.html)

# 项目中文件

- main.cpp 包含skiplist.h使用跳表进行数据操作
- skiplist.h 跳表核心实现
- bin 生成可执行文件目录
- makefile 编译脚本
- store 数据落盘的文件存放在这个文件夹
- stress_test_start.sh 压力测试脚本

# 对外接口

- insert_element(int,string) // 插入记录
- srase_element(int) // 删除记录
- search_element(int) // 查询记录
- displayList(int) // 显示结构
- dumpFile(string) // 导出数据
- loadFile(string) // 加载数据
- size() // 获取数据规模

# 存储引擎数据表现

## 插入操作

跳表树高：20

采用随机插入数据测试：

| 插入数据规模（万条） | 耗时（秒） |
| -------------------- | ---------- |
| 10                   | 2.64536    |
| 30                   | 8.56653    |
| 50                   | 17.0683    |

每秒可处理写请求数（QPS）: 24.39w

## 取数据操作

| 取数据规模（万条） | 耗时（秒） |
| ------------------ | ---------- |
| 10                 | 4.57455    |
| 30                 | 16.98      |
| 50                 | 30.8792    |

每秒可处理读请求数（QPS）: 18.41w

# 项目运行方式

```
make            // complie demo main.cpp
./bin/main      // run 
```

如果想自己写程序使用这个kv存储引擎，只需要在你的CPP文件中include skiplist.h 就可以了。

可以运行如下脚本测试kv存储引擎的性能（当然你可以根据自己的需求进行修改）

```
sh stress_test_start.sh 
```

相关参考：

[【数据结构】跳表SkipList代码解析(C++) - 半生瓜のblog (banshengua.top)](https://banshengua.top/[数据结构]跳表skiplist代码解析c/)