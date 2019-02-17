---
title: Python3入门 | 枚举类、模块、包、类
date: 2019-02-17 21:07:02
tags:
- Python3
- 枚举
categories:
- Python3
---


**作者的话**

通常我们需要表示一些日常事物，但是表达形式又不想太复杂，比如，我们QQ使用的红钻、绿钻、黄钻和黑钻，然后想通过1，2，3，4分别代替，但是在代码中使用1，2，3，4，对于代码的可阅读性会非常差，从而就有了枚举类，如果还是不能很好的理解，那么我们在后面学习枚举类的时候就能够更好地理解。对于包和模块要区分好，学会写类和使用类。
<!-- more -->
## 枚举类的基本表达

```
from enum import Enum

class VIP(Enum):
    YELLOW = 1
    GREEN = 2
    BLACK = 3
    RED = 4
    
print(VIP.YELLOW)

# 结果是输出 VIP.YELLOW
```

由此可以很清晰的看出，枚举实际上是一个类，而我们自定义的枚举类就是继承了Enum这个类

## 包和模块

两者都可能表现形式都是文件夹，会存在细微的差别，多个模块会组成包。

模块还可以就是指单个py文件，我们如果对于一个简单的功能，只需要一个文件就可以完成，那么这个功能就用一个py构成叫做一个模块，如果这个功能很复杂，一个py文件并不能完整的实现，而需要多个文件结合，这时候这些py文件存在的文件夹就成了一个模块.

文件夹和包 区别在于 在包下会有__sinit__.py文件

包下面是可以存在子包的，子包下也可以有它的子包

### 导入包

```
import 模块名
```
例:
存在一个模块
```
# file : spam.py  
a = 37                    # 一个变量  
def foo:                  # 一个函数  
    print "I'm foo"  
class bar:                # 一个类  
    def grok(self):  
        print "I'm bar.grok"  
b = bar()  
```
测试模块

```
# ceshi.py
import spam           # 导入并运行模块 spam  
print spam.a          # 访问模块 spam 的属性  
spam.foo()  
c = spam.bar()  
```

1. 总结下来就是，import 导入某个模块，通过模块名.* 在选择使用的对象

2. 如果包路径很深怎么办，那么我们使用as关键字进行简化

存在一个模块
```
# file : spam.py   位于 a/b下面
a = 37                    # 一个变量  
def foo:                  # 一个函数  
    print "I'm foo"  
class bar:                # 一个类  
    def grok(self):  
        print "I'm bar.grok"  
b = bar()  
```
测试模块

```
# ceshi.py 位于 a下面
import b.spam  as bspam         # 导入并运行模块 spam  
print bspam.a          # 访问模块 spam 的属性  
bspam.foo()  
c = bspam.bar()  
```

另外一种导入方式

```
from ... import ...
```
比如上面的导入可以改写为
```
# ceshi.py 位于 a下面
from b import spam      # 导入并运行模块 spam  
print spam.a          # 访问模块 spam 的属性  
spam.foo()  
c = spam.bar()  
```
这种方式也可以导入模块中某个具体对象
```
# ceshi.py 位于 a下面
from b.spam import a      # 导入并运行模块 spam  
print a          # 访问模块 spam 的属性   
```

***tips***: 包和模块的导入时不会重复的，要避免循环导入

今天就到这里吧，简单简单的非常口语化，写作能力确实有限，慢慢进步吧。


![关注我](https://upload-images.jianshu.io/upload_images/11278476-9a81399a80fd9bcf.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)