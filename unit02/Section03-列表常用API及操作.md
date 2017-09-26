# 2. Python中的列表、元组和循环

## 2.2 列表常用API及操作

### 2.2.1 取出列表中的最大最小值

如果想快速取出列表中的最大值和最小值，可以通过max()和min()函数：

- max(list):返回列表元素最大值
- min(list):返回列表元素最小值

```python

list1 = [47,23,11,55,90,-12]

# 返回列表最大值，赋值给maxValue

maxValue = max(list1)

# print('列表最大值为:%d' % maxValue) # 列表最大值为90

print('列表最大值为:{}'.format(maxValue))

# 返回列表最小值，赋值给minValue

minValue = min(list1)

#print('列表最小值为:%d' % minValue) # 列表最小值为-12

print('列表最小值为:{}'.format(minValue))

# 针对于字母也可以

list2 = ['a','b','c','d']

# 返回列表中的最大值

print(max(list1)) # 'd'

# 返回列表最小值

print(min(list1)) # 'a'

```

针对于字母做比较的原理是通过ASCII码([ASCII 百度百科](https://baike.baidu.com/item/ASCII/309296?fr=aladdin&fromid=19660475&fromtitle=ascii%E7%A0%81%E8%A1%A8))进行比较的。了解其原理之后，我们可以直观的看出a的ASCII位97，b的ASCII位98，所以a<b。我们可以通过ord(character)得到字符的ASCII码值，也可以通过chr(ascii)返回指定ASCII值对应的字符。

```python

char='a'

# ord(character) 返回指定字符的ASCII码值

asciiValue=ord(char)

# print('字符%s的ASCII码值为:%d' % (char,asciiValue))

print('字符{}的ASCII码值为:{}'.format(char,asciiValue))

# chr(ascii) 根据ASCII值返回指定字符

char=chr(asciiValue)

# print('ASCII码值为%s对应的字符为:%s' % (asciiValue,char))

print('ASCII码值为{}对应的字符为:{}'.format(asciiValue,char))


```

### 2.2.2 列表常用操作符

Python列表支持组合和重复这样的操作符，和字符串型类似。

- 组合：使用+，将多个列表拼接到一起
- 重复：使用*, 重复列表中的值

```python

# 列表组合

newList = [1,2,3] + [4,5,6]

print(newList) # [1,2,3,4,5,6]

newList = ['a','b','c'] + ['d','e','f']

print(newList) # ['a','b','c','d','e','f']

newList = [1,2,3] + [1,2,3]

print(newList) # [1,2,3,1,2,3]

newList = ['a','b'] + ['c','d'] + ['e','f']

print(newList) # ['a','b','c','d','e','f']

# 列表重复

list1 = ['a','b','c']

newList = list1 * 3

print(newList) # ['a', 'b', 'c', 'a', 'b', 'c', 'a', 'b', 'c']

```

### 2.2.3 检测列表中的值

如果想在列表中搜索某个值或者在列表中搜索某个值第一次出现的索引，我们可以使用in操作符和index()方法来实现，这在检索值是否存在时特别有效。

- in:检测某个值是否在列表中,存在返回True，否则返回False
- list.index(x):返回列表中x第一次出现的索引；如果没有出现返回false

```python

users = ['domi','king','queen']

# 检测domi是否在列表中

print('king' in users) # True

# 检测的时候区分大小写

print('KING' in users) # False

# 找出queen对应的索引

print(users.index('queen')) # 2

print(users.index('QUEEN')) # 不存在则报错

'''
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: 'QUEEN' is not in list
'''

```

### 2.2.4 列表的切片操作

列表支持切片操作，和字符的操作一样。

```python

list1 = ['a','b','c','d','e','f','g','h']

# 取出前3个元素,list1[0:3],从索引0开始，直到索引3为止，但不包含索引3

print(list1[0:3]) # ['a','b','c']

# 可以省略起始索引0，效果也一样

print(list1[:3]) # ['a','b','c']

# 如果省略第二个数字，代表从起始位置一直截取到末尾

print(list1[5:]) # ['f','g','h']

# 也支持负数，代表位置，同样的取出最后三个

print(list1[-3:]) # ['f','g','h']

# 也可以设置截取步长,设置步长为2

print(list1[0:9:2]) # ['a', 'c', 'e', 'g']

# 也是每两个截取一次

print(list1[::2]) # ['a', 'c', 'e', 'g']

# 如果什么都不写，代表复制了一个列表,得到新的副本

print(list1[:]) # ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']

# 也可以模拟追加元素

list1 = ['a','b','c']

list1[len(list1):] = 'd'

print(list1) # ['a', 'b', 'c', 'd']

```

通过[:]复制出来的列表为新列表，对新列表操作不影响原列表的值。

```python

# 创建列表a

a = [1,2,3]

# 将列表a赋值给b

b = a

# 创建列表c并且赋值为[]

c = []

# 将a赋值给c

c = a

# 通过[:]复制列表a,将产生的新列表赋值给d

d = a[:]

# 打印这四个列表

print(a,b,c,d) # [1,2,3] [1,2,3] [1,2,3] [1,2,3]

# 可以通过id(object)得到对象的内存地址，打印可以比较出来前三个对象的内存地址一样，而新复制出来的列表和原对象内存地址不一样

print(id(a),id(b),id(c),id(d)) # 4331732936 4331732936 4331732936 4331732296

# 修改b[0]='x'，此时a,b,c对象的第一个值都会改为x,而d不会改变

b[0] = 'x'

print(a,b,c,d) # ['x',2,3] ['x',2,3] ['x',2,3] [1,2,3]

c[1] = 'y'

print(a,b,c,d) # ['x', 'y', 3] ['x', 'y', 3] ['x', 'y', 3] [1, 2, 3]

# 将d[2]='z',此时a,b,c对象不会改变

d[2] = 'z'

print(a,b,c,d) # ['x', 'y', 3] ['x', 'y', 3] ['x', 'y', 3] [1, 2, 'z']

# 当想得到一个新列表的时候并且改变列表值不影响原列表，可以使用[:]来复制

```

除了使用[:]复制列表，还可以使用列表中的list.copy()方法来实现复制，它们两个效果一样。

```python

a = [1,2,3]

# 通过[:]复制列表a,赋值给b

b = a[:]

# 通过a.copy()复制列表a,赋值给c

c = a.copy()

print(a,b,c) # [1, 2, 3] [1, 2, 3] [1, 2, 3]

print(id(a),id(b),id(c)) # 4331731400 4331724104 4331731016


```

### 2.2.5 列表其它常用方法

再来一起看下列表中其它常用的方法：

- list.count(x):返回x在列表中出现的次数
- list.extend(L):将一个给定列表中的所有元素都添加到另外一个列表中，相当于a[len(a):] = L
- list.reverse():列表元素倒置
- list.sort():列表排序

```python

users = ['domi','king','queen','rose','domi','domi']

# 统计domi出现的次数

# print('domi出现的次数为%s次' % users.count('domi')) # domi出现的次数为3次

print('domi出现的次数为{}次'.format(users.count('domi'))) # domi出现的次数为3次


list1 = ['a','b','c']

list2 = ['d','e','f']

# 将list2列表中的所有元素添加到list1中,一种方式可以使用+将两个列表连接起来在重新赋值给list1

list1 = list1 + list2

print(list1) # ['a','b','c','d','e','f']

# 另外一种方式就可以使用list1.extend(list2)的方式将list2中的值添加到list1中

list1 = ['a','b','c']

list2 = ['d','e','f']

list1.extend(list2)

print(list1) # ['a','b','c','d','e','f']

# 列表元素倒置

list1 = ['a','b','c']

# 会改变列表本身

list1.reverse()

print(list1) # ['c','b','a']

# 如果不想改变元素本身可以使用[::-1]的形式将元素倒置

list1 = ['a','b','c']

print(list1[::-1]) # ['c','b','a']

print(list1) # ['a','b','c']

# 列表排序

list1 = [12,34,56,234,-15]

# 对list1中的元素从小到大排序(升序),会改变列表本身

list1.sort()

print(list1) # [-15, 12, 34, 56, 234]

list1 = ['z','x','a','d','c','m']

list1.sort() # ['a', 'c', 'd', 'm', 'x', 'z']

# 也可以通过指定reverse=True,从大到小排序(倒序)

list1 = [12,34,56,234,-15]

list1.sort(reverse=True)

print(list1) # [234, 56, 34, 12, -15]

# 如果想临时排序不影响列表本身，可以使用sorted()函数，它返回的是一个新的list，而不是在原有列表基础上进行操作

list1 = [23,15,-59,89,234,857]

# 将排序结果赋值给newList

newList = sorted(list1)

print(list1) # [23,15,-59,89,234,857]

print(newList) # [-59, 15, 23, 89, 234, 857]

# 后续还可以自定义函数进行排序


```
