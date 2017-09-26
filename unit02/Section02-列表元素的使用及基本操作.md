# 2. Python中的列表、元组和循环

## 2.1 列表元素的使用及基本操作

### 2.1.1 列表简介

序列是Python中最基本的数据结构，序列中的每个元素都分配一个数字代表其位置，也可以叫做索引，元素的索引是从0开始。

Python有六个序列的内置类型，但最常见的就是列表和元组。

序列都可以进行的操作包括索引、切片、加、乘、检查成员操作。

列表是最常用的Python数据类型，它是由一些列按特定顺序排列的元素组成。在Python中可以使用[]来表示列表，其中的元素可以使用英文的逗号,分隔。列表中可以放任意类型的元素。

### 2.1.2 创建列表

创建列表很简单，就是使用[]中放置任意的元素即可。

```python

# 创建空列表

list1 = []

# 创建包含数值的列表

list2 = [10,20,30,40,50]

# 创建包含字母的列表

list3 = ['a','b','c','d','e']

# 创建混合列表

list4 = ['domi',23,True,58888.99]

"""
列表里面的元素，可以是不同类型的对象，可谓是“有容乃大”，不仅如此，它的元素个数还可以无限大，就是说里面所能容纳的元素数量无限，当然这是在硬件设备理想的情况下。
"""

# 嵌套列表

list5 = [['a','b'],['c','d']]

```

### 2.1.3 打印列表

可以直接使用print()函数来打印列表

```python

print(list1) # []

print(list2) # [10,20,30,40,50]

print(list3) # ['a','b','c','d','e']

print(list4) # ['domi',23,True,58888.99]

print(list5) # [['a','b'],['c','d']]

```

### 2.1.4 检测是否是列表

如果想检测变量是否是列表，可以通过两种方式：

- type(name):返回对象的类型
- isinstance(name,type):断一个对象是否是一个已知的类型，类似 type()


**_推荐使用isinstance()检测变量类型_**


```python

# 打印变量类型
type(list1) # <class 'list'>

# 检测变量是否是某个类型
isinstance(list1,list) # True

a=12

type(a) # <class 'int'>

isinstance(a,int) # True

isinstance(a,list) # False

name='domi'

type(name) # <class 'str'>

isinstance(name,str) # True

isinstance(name,list) # False

# 也可以检测是否是某些类型中的一种，如果是返回True，否则返回False

salary=12345.678

type(salary) # <class 'float'>

isinstance(salary,(int,float,str)) # True

isinstance(salary,(int,str,list)) # False


```

>isinstance() 与 type() 区别：
>
>- type() 不会认为子类是一种父类类型，不考虑继承关系。
>
>- isinstance() 会认为子类是一种父类类型，考虑继承关系。
>
>(PS~可以先不考虑什么是继承，等学到面向对象的时候就会讲了)


### 2.1.5 列表的长度

可以通过len(list)函数得到列表的长度

```python

len(list1) # 0

len(list2) # 5

len(list3) # 5

```

### 2.1.6 访问列表中的元素

由于列表是有序集合，可以根据下标或者索引找到对应的元素进行访问。索引是从0开始。

```python

# 创建列表

users = ['tom','lily','rose','domi','king']

# 打印列表的第一个元素

print(users[0]) # tom

# 取出domi，对应的索引是3

print(users[3]) # domi

# 取出列表最后一个元素

print(users[4])

# 如果不知道列表长度的情况下，还可以使用-1快速取出最后一个元素，此时-1代表位置，从列表的最后开始向左边数

print(users[-1]) # king

# 也可以使用len(users)-1得到列表的最后一个元素

print(users[len(users)-1]) # king

# 访问嵌套列表

usersInfo = [
['domi',23,'女','北京'],
['king',24,'男','上海'],
['queen',25,'女','广州']
]

print(usersInfo) # [['domi', 23, '女', '北京'], ['king', 24, '男', '北京'], ['queen', 25, '女', '上海']]

# 取出domi

print(usersInfo[0][0]) # domi

# 取出queen

print(usersInfo[2][0]) # queen
```

### 2.1.7 修改列表元素

同样的想要修改列表中的元素，首先需要找到元素对应的索引，接着在重新赋值即可。

```python

list6 = ['a','b','c','d']

# 将元素a更新为a1

list6[0] = 'a1'

print(list6) # ['a1','b','c','d']

# 将元素d更新为d1

list6[-1] = 'd1'

print(list6) # ['a1','b','c','d1']

```

### 2.1.8 添加列表元素

- 在列表末尾添加元素
- 在列表中插入元素

第一种可以通过append()方法向列表末尾添加元素：

```python

list7 = ['a','b','c']

# 向列表末尾添加元素d

list7.append('d')

print(list7) # ['a','b','c','d']

# 向列表末尾添加另外一个列表

list7.append([1,2,3,4])

print(list7) # ['a','b','c','d',[1,2,3,4]]

# 定义空列表

list8 = []

# 通过append()向列表中添加元素

list8.append('a')

list8.append('b')

list8.append('c')

print(list8) # ['a','b','c']

```

---

第二种可以通过list.insert()在列表指定位置插入元素,找到对应索引插入相应元素即可。

list.insert(i,x),第一个参数是准备插入到其前面的那个元素的索引

```python

list9 = ['a','b','c']

# 在列表0的位置前面插入x

list9.insert(0,'x')

print(list9) # ['x','a','b','c']

list10 = ['a','b','c']

# 在列表-1的位置之前插入x

list10.insert(-1,'x')

print(list10) # ['a','b','x','c']

list11 = ['a','b','c']

# 在列表最后插入x

list11.insert(len(list11),'x') # 等价于list11.append('x')

print(list11) # ['a','b','c','x']

```

### 2.1.9 删除列表元素

- del语句删除列表元素
- 使用pop()方法删除末尾元素
- 使用pop()方法根据索引删除元素
- 使用remove()方法根据值删除元素
- 使用clear()方法删除所有元素

del语句是根据元素的索引来删除元素，它没有返回值,也可以通过del语句删除某个变量

```python

list12 = ['a','b','c','d']

# 删除a,元素对应的索引是0

del list12[0]

print(list12) # ['b','c','d']

# 删除最后一个元素

del list12[-1]

print(list12) # ['b','c']

# 删除list12这个变量

del list12

# 此后再引用命名list12会引发错误（直到另一个值赋给它为止）

print(list12)

'''
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'list12' is not defined
'''

```

---

有时候我们需要拿到删除元素的值，就可以通过pop()方法来实现。直接使用list.pop()方法可以删除列表末尾的值

```python

list13 = ['a','b','c','d']

# 弹出末尾元素

list13.pop() # 'd'

print(list13) # ['a','b','c']

# 将弹出的元素赋值给变量，为了下面接着使用

str = list13.pop()

print(str) # 'c'

print(list13) # ['a','b']

```

---

同样的我们还可以使用pop()方法弹出列表中任意位置的元素，根据对应的索引即可。

```python

list14 = ['a','b','c','d','e']

# 弹出索引为0的元素

list14.pop(0) # 'a'

print(list14) # ['b','c','d','e']

# 弹出d元素，对应的索引为2

str = list14.pop(2)

print(str) # 'd'

print(list14) # ['b','c','e']

```

---

有时候我们不知道元素在列表中的位置，也可以通过remove()方法根据值来删除这个元素

```python

list15 = ['a','b','c','d']

# 删除元素c

list15.remove('c')

print(list15) # ['a','b','d']

# 删除不存在的元素会报错

list15.remove('z')

'''
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: list.remove(x): x not in list
'''

# remove()只删除列表中存在的第一个值，如果需要删除多个值,需要使用到后续的循环来实现

list16 = ['a','b','c','a','a','a']

list16.remove('a')

print(list16) # ['b', 'c', 'a', 'a', 'a']

```

---

如果想删除列表中所有元素，可以对列表重新赋值为[],也可以使用clear()方法来删除

```python

# 将列表重新赋值为[]

list17 = ['a','b','c']

list17 = []

print(list17)

# 使用list.clear()方法清空列表

list18 = ['a','b','c']

list18.clear()

print(list18)

```
