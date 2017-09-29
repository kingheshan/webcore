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

tuple1 = 'a','b','c','d'

print(tuple1) # ('a', 'b', 'c','d')

tuple2 = 1,2,3,4

print(tuple1) # (1,2,3,4)

tuple3 = 'domi',23,True,56789.123

print(tuple3) # ('domi', 23, True, 56789.123)

tuple4 = ['a','b','c'],['d','e','f']

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

tuple3 = tuple(['a','b','c','d'])

print(tuple3) # ('a', 'b', 'c', 'd')

# 也可以将元组转换成列表

list1 = list(tuple3)

print(list1) # ['a','b','c','d']

```

### 2.4.2 元组的使用

元组的使用和列表基本一致，但是不同的就是元组中的元素不能够被修改：

```python

tuple1 = ('a','b','c')

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


---

### 2.4.3 元组应用场景

其实我们看过了元组，应该发现它其实和字符串包括列表有些相似，也可以说它是字符串和列表的杂交体。因为其不能被修改的特性像字符串，而形式上又和列表很像，可以保存任意元素，只不过是不能被修改，这点和字符串又不同。

那元组具体有什么应用场景呢？

根据元组的特点，大体总结了下其实际应用场景：

- 元组比列表操作速度快。如果说你想定义一些不被改变的值或者常量，建议使用元组。
- 如果想对不想被更改的数据进行"写保护"，这样可以保证代码更安全。使用元组而不是列表就相当于加上了assert语句(断言，后面我们会学习)，说明这些数据是常量，不应该被修改。如果必须想修改的时候会先将元组转换成列表在操作。
- 元组可以在字典(后续会将这种类型)中作为key，而列表不可以。因为字典中的key必须是不变的
