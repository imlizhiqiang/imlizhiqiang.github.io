---
title: python中namedtyple与dataclass的使用
tags: python
---

#

<!-- more -->

命名元组可以方便地声明一个极简的对象，默认该对象是不可变的。

在声明时可以显式指定属性名赋值，可读性很好。

dataclass官方给出的设计目的是“mutable namedtuples with defaults”，即可变的且带有默认值的命名元组，使用起来与class类似，可以继承。

但是我认为不可变恰恰是命名元组的优势（函数式的风格），不带有默认值也无关紧要。在需要一个极简的对象结构时，仍然推荐使用命名元组。

命名元组唯一需要注意的地方是，它不会检查不同元组之间同名属性的数据类型是否一致，比如如下代码：

```python
User=namedtuple('User',['id','name','age'])

user1=User(id=1,name='zhangsan',age=22)
user2=User(id='123',name=222,age='333')
```

这段代码是完全正确的。