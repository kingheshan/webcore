# 3. Python中的条件语句

所谓条件语句，顾名思义，就是根据某个条件的真假，执行不同的内容。


## 3.1 if语句的使用

Python条件语句是通过一条或多条语句的执行结果（True或者False）来决定执行的代码块。

if的就可以翻译成如果，它所发起的就是一个条件语句。也就是我们条件语句的关键词。

和我们生活中经常遇到的问题很相似，经常我们会看到，如果年龄不满足18岁则不能进入。这其实就是条件语句。

if的形式也有很多种，我们一一来看。

### 3.1.1 单独的if语句

if语句的形式有很多种，先来看最简单的形式，形式如：

```python

"""
if expression:
    语句块
"""

```
Python碰到if语句，首先检测expression是否为True，如果为True会执行下面的语句块。这里我们需要特别注意下：在expression之后要有冒号，这个是不能省略的。还有就是在语句块之前要有四个空格的缩进，这就是Python的特点，必须要通过缩进方式来表示语句块的开始和结束。当然如果你的tab设置为4个空格，用tab键也可以。

```python
# 如果表达式为真，则可以执行语句块

if True:
    print('Hello Python')
    print('人生苦短，我用Python')
print('continue~')

# 如果表达式为假，则执行不到语句块，程序继续向下执行

if False:
    print('条件为假，执行不到相应的代码块')
print('continue~')

# 如果年龄大于等于18则可以进入

age = 23

if age>=18:
    print('可以进入')
print('continue~')

```

表达式要么为真，要么为假，我们找出表达式为假的情况，其它的都会为真：

布尔情况为假的有：

- False
- None
- 数值中的0,0.0,0j(虚数)
- 空序列(包括空字符串、空列表、空元组)
- 空字典(字典后续会介绍，先来使用下)
- 空集合(集合后续会介绍，先来使用下)

```python

# 第一种方式可以使用bool()函数来检测是否为True或者False

# 以下情况都为布尔类型的假

print(bool(False)) # False

print(bool(None)) # False

print(bool(0)) # False

print(bool(0.0)) # False

print(bool(0j)) # False

print(bool('')) # False

print(bool("")) # False

print(bool([]) # False

print(bool(())) # False

print(bool({})) # False 空的字典

print(bool(set())) # False 空的集合

```

其它都会转换成布尔类型的True：

```python

print(bool(123)) # True

print(bool(23.4)) # True

print(bool('False')) # True

print(bool(' ')) # True 空格也是字符

print(bool([0])) # True

print(bool((12))) # True

```

接着可以将其放置到if语句的条件中，来试验下：
