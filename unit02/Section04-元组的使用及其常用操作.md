# 2. Python中的列表、元组和循环

## 2.4 元组的使用及其常用操作

### 2.4.1 元组简介

元组也是Python中的一种数据类型，它和列表很相似，但是元组的元素是不能被修改的。元组中的元素也可以是任意类型。

创建元组也特别简单，可以使用几种方式：

- 直接使用逗号分隔元素
- 圆括号括起来，括号中的值用逗号隔开
- 使用tuple()函数创建元组

首先先看第一种方式创建元组，直接使用逗号分隔元素：

```python

# 创建元组

# 元素可以是任意类型

tuple1 = 'a', 'b', 'c', 'd'

print(tuple1) # ('a', 'b', 'c','d')

tuple2 = 1, 2, 3, 4

print(tuple1) # (1, 2, 3, 4)

tuple3 = 'domi', 23, True, 56789.123

print(tuple3) # ('domi', 23, True, 56789.123)

tuple4 = ['a', 'b', 'c'],['d', 'e', 'f']

print(tuple4) # (['a', 'b', 'c'], ['d', 'e', 'f'])

# 如果元组中只有一个元素，需要在元素后面放置逗号

tuple5 = 'python',

print(tuple5) # ('python',)

# 打印变量类型

print(type(tuple5)) # <class 'tuple'>

# 检测变量类型

print(isinstance(tuple5,tuple)) # True

```

---

接着在使用圆括号的形式来创建元组：

```python

# （）的形式创建元组

tuple1 = () #空元祖

print(tuple1) # ()

# 返回元组中元素的个数

print(len(tuple1)) # 0

# 同样如果元组只有一个元素，需要放置逗号

tuple2 = ('a')

print(tuple2) # a 字符串的a

tuple2 = ('a',)

print(tuple2) # ('a',)

tuple3 = (1,1.3,'a',True)

print(tuple3) # (1, 1.3, 'a', True)

tuple4 = ('a','b',12,34.56,False,['x','y','z'])

print(tuple4) # ('a', 'b', 12, 34.56, False, ['x', 'y', 'z'])

# 同样元组支持嵌套

tuple5 = ((1,2,3),('a','b','c'))

print(tuple5) # ((1, 2, 3), ('a', 'b', 'c'))

```

---

接着最后一种方式是使用tuple()函数创建元组：

```python

# 使用tuple()函数创建元组

# tuple()函数中传入字符串序列

tuple1 = tuple('abcdef')

print(tuple1) # ('a', 'b', 'c', 'd', 'e', 'f')

tuple2 = tuple('1234')

print(tuple2) # ('1','2','3','4')

tuple2 = tuple(1234) # 报错

"""
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'int' object is not iterable
"""

# 传入列表

tuple3 = tuple(['a', 'b', 'c', 'd'])

print(tuple3) # ('a', 'b', 'c', 'd')

# 也可以将元组转换成列表

list1 = list(tuple3)

print(list1) # ['a', 'b', 'c', 'd']

```

### 2.4.2 元组的使用

元组的使用和列表基本一致，但是不同的就是元组中的元素不能够被修改：

```python

tuple1 = ('a', 'b', 'c')

print(tuple1[0]) # a

# 修改

tuple1[0] = 'x' # 报错

"""
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'tuple' object does not support item assignment
"""

# 删除

del tuple1[0] # 报错

# 添加

tuple1.append('d') # 没有此方法

```

其它和列表相关的操作我就不一一来试验了，交给大家来测试，对照着列表的方式来试验，看看哪些可以，哪些不可以。

**但记住所有在列表中可以修改列表的方法，在元组中都不可以**

### 2.4.3 多元赋值

有了列表包括元组，可以实现多元赋值的操作，形式如：x,y,z = (1, 2, 3)或者x,y,z = ['a', 'b', 'c'],可以实现多个变量快速赋值。如果左右两边数目不等，会报错。

```python

x,y,z = (1, 2, 3)

print(x) # 1

print(y) # 2

print(z) # 3

x,y,z = ['a', 'b', 'c']

print(x) # a

print(y) # b

print(z) # c

# 左右两边不等，报错

x, y = (1, 2, 3) # 报错

"""
值比变量多
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: too many values to unpack (expected 2)
"""

x, y, z = (1, 2) # 报错

"""
值比变量少
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: not enough values to unpack (expected 3, got 2)
"""

```

有了这种多元赋值的形式，交互两个变量的值包括交互列表中两个元素的位置就特别容易了：

```python

a = 3

b = 5

# 交互a和b的值

a, b = b, a

print(a, b) # 5,3

balls = ['⚽️', '🏀', '🏸', '🏓']

# 交换足球和乒乓球的位置

balls[0], balls[3] = balls[3], balls[0]

print(balls)

```

这就体现了Python的简洁之道，一行代码就可以搞定。如果是其它语言，需要拿一个临时变量来存放，接着再交换。

---

### 2.4.4 元组应用场景

其实我们看过了元组，应该发现它其实和字符串包括列表有些相似，也可以说它是字符串和列表的杂交体。因为其不能被修改的特性像字符串，而形式上又和列表很像，可以保存任意元素，只不过是不能被修改，这点和字符串又不同。

那元组具体有什么应用场景呢？

根据元组的特点，大体总结了下其实际应用场景：

- 元组比列表操作速度快。如果说你想定义一些不被改变的值或者常量，建议使用元组。
- 如果想对不想被更改的数据进行"写保护"，这样可以保证代码更安全。使用元组而不是列表就相当于加上了assert语句(断言，后面我们会学习)，说明这些数据是常量，不应该被修改。如果必须想修改的时候会先将元组转换成列表在操作。
- 元组可以在字典(后续会将这种类型)中作为key，而列表不可以。因为字典中的key必须是不变的

### 2.4.5 序列总结

其实你发现我们将字符串、列表、元组放到一起来讲是有目的的，因为它们都属于序列，而且还有一些共同的特点，这样方便大家来记忆。

接着我们在一起回顾下这些序列的共同特点，包括其中一些常见的方法：

- 都可以通过索引得到每一个元素
- 默认索引值都是从0开始，代表第一个元素
- 都可以通过切片的方式得到一个范围内的元素的集合
- 有很多共同的操作符(像连接、重复、成员关系操作符)

接着再来看下这些序列常用的一些方法：

1.list([iterable])

list()用于把一个可迭代的对象转换为列表，这列的迭代我们先简单了解下，后续还会学到迭代相关的知识。

>迭代：

>迭代就是重复反馈过程的活动，目的通常是为了接近并到达所需的目标或结果。每一次对过程的重复被称为一次迭代，而每一次迭代得到的结果会被用来作为下一次迭代的初始值。

```python

# 创建一个空列表

list1 = list()

# 将字符串中的每一个字符迭代存放到列表中

list2 = list('python')

print(list2) # ['p', 'y', 't', 'h', 'o', 'n']

# 将元组中每个元素迭代放到列表中

list3 = list(('a', 'b', 'c'))

print(list3) # ['a', 'b', 'c']

```

2.tuple([iterable])

tuple()和list()一样，用于把一个可迭代的对象转换为元组

```python

# 创建空元组

tuple1 = tuple()

# 将字符串中的每个字符迭代放到元组中

tuple2 = tuple('python')

print(tuple2) # ('p', 'y', 't', 'h', 'o', 'n')

# 将列表中的每一个元素迭代的放入元组中

tuple3 = tuple(['a','b','c'])

print(tuple3) # ('a', 'b', 'c')

```

3.str(obj)

str()可以把其它对象转换成字符串：

```python

# 将其它类型转换成字符串

str(1) # '1'

str(23.4) # '23.4'

str(True) # 'True'

str(False) # 'False'

str(None) # 'None'

str(['a', 'b', 'c']) # "['a', 'b', 'c']"

str(('a', 'b', 'c')) # "('a', 'b', 'c')"

# 和它一起记住的还有int()和float()函数

int(23.4) # 23

int(23.9) # 23

int(True) # 1

int (False) # 0

int(None) # 报错

int('3abc') # 报错

float(3) # 3.0

float(True) # 1.0

float(False) # 0.0

```

4.len(obj)

len()用于返回对象的长度：

```python

str1 = 'abc'

print(len(str1)) # 3

list1 = ['a', 'b', 'c']

print(len(list1)) # 3

tuple1 = ('a', 'b', 'c')

print(len(tuple1)) # 3

```

5.max(...)|min(...)

max()和min()是返回序列中的最大值和最小值：

```python

# 给定多个参数，可以返回其最大值

max(23, 42, 52) # 52

min(23, 42, 52) # 23

max('a', 'b', 'c', 'z') # 'z'

min('a', 'b', 'c', 'z') # 'a'

max([12, 424, 53]) # 424

min([12, 424, 53]) # 12

max(('a', 'b', 'c')) # 'c'

min(('a', 'b', 'c')) # 'a'

max([1, 2, 'a', 'b']) # 报错

"""
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unorderable types: str() > int()
"""

```

6.sum(iterable[, start=0])

sum()是用于返回序列iterable的总和：

```python

list1 = [1, 2, 3, 4, 5]

sum(list1) # 15

tuple1 = (1, 2, 3, 4, 5)

sum(tuple1)

# 可以设置第二个参数，求和的起始点，默认为0

# 设置起始点为10，代表从10开始累加

sum(list1, 10) # 25

sum(tuple1, 20) # 35

# 只能对于数值求和

sum(['1', '2', '3']) # 报错

"""
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'int' and 'str'
"""

# 只能求一维列表和元组的元素和

list2 = [1, 2, 3, [1, 2]]

sum(list2) # 报错

"""
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: unsupported operand type(s) for +: 'int' and 'list'
"""

```

7.sorted(iterable, key=None, reverse=False)

sorted()用于返回一个排序的列表，之前我们还学过列表中的sort()方法，它也能实现排序的效果，但是它是对原列表进行排序，会改变原来的列表。而sorted()函数是返回一个新的列表。

```python

str1 = 'czxba'

sorted(str1) # ['a', 'b', 'c', 'x', 'z']

print(str1) # czxba

list1 = ['p', 'y', 't', 'h', 'o', 'n']

sorted(list1) # ['h', 'n', 'o', 'p', 't', 'y']

print(list1) # ['p', 'y', 't', 'h', 'o', 'n']

tuple1 = ('p', 'y', 't', 'h', 'o', 'n')

sorted(tuple1) # ['h', 'n', 'o', 'p', 't', 'y']

print(tuple1) # ('p', 'y', 't', 'h', 'o', 'n')

```

8.reversed(sequence)

reversed()用于返回逆向迭代序列的值。同样的道理，实现效果和列表的reverse()一致。区别是列表的内建方法是原地翻转，而reversed()是返回一个翻转之后的迭代器对象。注意返回的不是一个列表，是一个迭代器对象(后续会学到，先简单看一下)：

```python

str1 = 'abc'

reversed(str1) # <reversed object at 0x102f8d3c8> 迭代器对象

# 使用for循环遍历,先简单看下

for v in reversed(str1):
    print(v)

"""
c
b
a
"""

list1 = ['a', 'b', 'c']

reversed(list1) # <list_reverseiterator object at 0x102ce28d0>

tuple1 = ('a', 'b', 'c')

reversed(tuple1) # <reversed object at 0x102f8d3c8>

```

9.enumerate(iterable)

enumerate()生成由二元组(就是元素数量为二的元组)构成的一个迭代对象，每个二元组是由可迭代参数的索引号及其对应的元素组成的。

```python

str1 = 'python'

for v in enumerate(str1):
    print(v)

"""
(索引, '元素的值')这样的形式
(0, 'p')
(1, 'y')
(2, 't')
(3, 'h')
(4, 'o')
(5, 'n')
"""

list1 = ['a', 'b', 'c']

for v in enumerate(list1):
    print(v)

"""
(0, 'a')
(1, 'b')
(2, 'c')
"""

tuple1 = ('a', 'b', 'c')

for v in enumerate(tuple1):
    print(v)

"""
(0, 'a')
(1, 'b')
(2, 'c')
"""

```

10.zip(iter1 [,iter2 [...])

zip()用于返回由各个可迭代参数共同组成的元组：

```python

list1 = ['a', 'b', 'c']

list2 = ['x', 'y', 'z']

for v in zip(list1, list2):
    print(v)

"""
(第一个列表的值,第二个列表的值) 一一对应的形式
('a', 'x')
('b', 'y')
('c', 'z')
"""

str1 = 'abc'

str2 = 'xyz'

for v in zip(str1, str2):
    print(v)

"""
('a', 'x')
('b', 'y')
('c', 'z')
"""

tuple1 = 23, 18, 27
tuple2 = '北京', '上海', '深圳'
tuple3 = 'domi', 'rose', 'lily'

for v in zip(tuple1, tuple2, tuple3):
    print(v)

"""
(23, '北京', 'domi')
(18, '上海', 'rose')
(27, '深圳', 'lily')
"""

```
