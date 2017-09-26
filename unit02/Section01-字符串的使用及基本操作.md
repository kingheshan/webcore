# Unit02 Python中的字符串和列表

## 2.1 字符串的使用及基本操作

### 2.1.1 字符串

字符串是Python中最常用的数据类型,字符串就是一系列字符。在Python中，用引号括起的都是字符串，引号相当于字符串的定界符，要成对出现，其中的引号可以是单引号，也可以是双引号。

```python

# 输出Hello World,引号之间的就是字符串,不论使用单引号还是双引号

print('Hello World') # Hello World

# 双引号包裹也可以

print("Hello World") # Hello World

```

创建字符串特别简单：

```python

# 创建一个字符串

string1 = '' # 空字符串

username = 'domi'

addr = '北京'

sex = '女'

# 输出下相关变量的值

print(string1) # 空字符串，什么也看不到

print(username) # domi

print(addr,sex) # 北京 女

```

空字符串是字符串吗？我们在命令行中print(1) 和 print('1') 看到的结果都是1，那我们如何验证一个变量是字符串类型呢？

其实很简单，可以通过type(x)来打印变量的类型：

```python

string1 = ''

print(type(string1)) # <class 'str'> 严格地说，在Python中的字符串是一种对象类型，这种类型用str表示


a = 1

b = '1'

print(type(a),type(b)) # <class 'int'> <class 'str'>

```

定义简单的字符串没有问题了，那现在我想创建一个类似这样的字符串，"I'm Ok" 该如何定义呢？我们应该选择什么作为定界符呢？

```python

# 单引号当定界符

string1 = '"I'm Ok"'

"""
程序已经报错,语法错误
File "<stdin>", line 1
    string1 = '"I'm Ok"'
                  ^
SyntaxError(语法错误): invalid syntax(无效的语法)
"""

# 双引号当定界符

string1 = ""I'm Ok""

"""
程序同样报错
File "<stdin>", line 1
    string1 = ""I'm Ok""
                ^
SyntaxError(语法错误): invalid syntax(无效的语法)
"""

```

不论是使用单引号还是双引号，程序都会产生语法错误，因为当字符串中的内容和定界符冲突的时候计算机就懵逼了，computer搞不清楚该谁包裹谁了，谁和谁是一对的~所以此时需要使用转义符来解决。

### 2.1.2 转义符

所谓转义，就是让某个符号不再表示某个含义，而是表示另外一个含义。转义符的作用就是它能够转变符号的含义。在Python中，用反斜线 \ 作为转义符（其实很多语言，只要有转义符的，都是用这个符号）。

<table>
    <thead>
        <tr>
            <th>转义字符</th>
            <th>描述</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>\(在行尾时)</td>
            <td>续行符</td>
        </tr>
        <tr>
            <td>\\</td>
            <td>反斜杠符号</td>
        </tr>
        <tr>
            <td>\'</td>
            <td>单引号</td>
        </tr>
        <tr>
            <td>\"</td>
            <td>双引号</td>
        </tr>
        <tr>
            <td>\n</td>
            <td>换行</td>
        </tr>
        <tr>
            <td>\r</td>
            <td>回车</td>
        </tr>
        <tr>
            <td>\t</td>
            <td>横向制表符</td>
        </tr>
    </tbody>
</table>

---

以上是常用的转义符，有了这些转义符之后刚刚的问题就迎刃而解了。

```python

# 使用单引号当做定界符，此时内容中的单引号和定界符冲突，需要使用\'进行转义

string1 = '"I\'m Ok"'

print(string1) # "I'm Ok"

# 如果使用双引号当做定界符，此时内容中的双引号需要转义

string1 = "\"I'm Ok\""

print(string1) # "I'm Ok"

```

其它那几个转义符我们也来一一试试。

```python

# 续行符，当字符串很长的时候可以使用一行的末尾使用续行符，接着在下一行继续书写
# 毕竟python推荐一行中最多写79个字符是比较合适的

string1 = 'hello\
world\
!'

print(string1) # helloworld!

# \n代表换行

string1 = 'a\nb\nc\nd'

print(string1)

"""
a
b
c
d
"""

string1 = '\\'

print(string1) # \

```

如果我想输出电脑中的某个文件的绝对路径(Windows电脑)，类似c:\some\name的路径：

```python

print('c:\some\name')

"""
得到的结果类似这样，因为\n代表换行的意思
C:\some
ame
"""

```

一种方式是将字符串中的 \ 转义：

```python

print('c:\\some\\name') # c:\some\name

```

另外一种方法是在第一个引号前面加上一个 r或者 R，代表不对特殊字符进行转义

```python

print(r'c:\some\name') # c:\some\name

print(R'c:\some\name') # c:\some\name

print(r'\\') # \\

```

当我们内容很多的时候，我们想将其放置在多行，这时候可以使用"""..."""三引号的形式。

```python

string1 = """
Good Good Study,
Day Day Up~
"""

print(string1)

"""
发现输出的文本中多了两个空行，因为行尾的换行符会被包含在字符串中，想解决这个问题也很简单，使用在行首和行尾使用续行符即可。

Good Good Study,
Day Day Up~

"""

string1 = """\
Good Good Study,

Day Day Up~

Failure is the fog through which we glimpse triumph.\
"""

print(string1)

"""
此时行首和行尾就不包含换行了
Good Good Study,
Day Day Up~
Failure is the fog through which we glimpse triumph.
"""

```

### 2.1.3 字符串操作符

在字符串中可以做很多操作，这时候就需要配合不同的操作符完成不同的功能。

- \+，拼接字符串
- \*，重复字符串
- []，获取字符串中的指定字符
- [:]，字符串切片操作，形式如[start:end:step]
- in | not in ,成员运算符，检测字符串中是否存在某个值
- %，格式化字符串

我们一一来看下这些运算符如何使用。

首先先看拼接字符串，这里想到一个段子：

>小学语文老师布置这样一个题目：请用“不约而同”造句。
>
>一小朋友回答：
>
>我问姐姐，“约吗？”，姐姐说，不约儿童。
>

上面这句话，就是多个字符串连接到了一起。所以，字符串是可以连接起来的。

连接字符串使用 + 号，这个和数学的+不一样，它是用来拼接字符串的。

```python

print("py" + "thon") # python

print("hello" + "world" + "!") # helloworld!

a = 'hello'

b = 'world'

# 等量代换的效果

print(a + b + '!') # helloworld!

username = 'Jordan'

age = 23

print(username + age)

"""
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: cannot concatenate 'str' and 'int' objects
字符串类型不能和整型连接
"""

```

用 + 所连接的两个对象，必须是同一种类型。如果是不同类型的，则"cannot concatenate"或者"unsupported"。

如果两个都是数字，毫无疑问是正确的，就是求和；如果都是字符串，那么就得到一个新的字符串。

那如果想解决这个问题怎么办呢？我们可以通过str()将其它对象转换成字符串对象：

```python

username = 'Jordan'

age = 23

print(username + str(age)) # Jordan23

# 将12转换成字符串

print(str(12)) # 12

# 将68.8转换成字符串

print(str(68.8)) # 68.8

# 将True转换成字符串

print(str(True)) # True

```

还有一种自动连接字符串的方式,相邻的两个字符串文本自动连接在一起:

```python

print('py''thon') # python

print('hello' 'world' '~') # helloworld~

```

注意：它只用于字符串文本，不能用于字符串表达式:

```python

str1 = 'hello'

print(str1 'world')

```

这个功能在你想切分很长的字符串的时候特别有用:

```python

text = ('This is a test '
' hello world ')

print(text) # this is a test hello world

```

---

重复字符串中的内容可以使用*号：

```python

print('hi~') # hi~

# 重复3次hi~

print('hi~' * 3) # hi~hi~hi~

# 输出Google

print('G' + 'o' * 2 + 'gle')

```

---

如果我们想读取字符串中的指定字符，可以根据字符串中的下标或者索引找到对应的字符,形式如str[索引]。字符串的索引是从0开始的，也是第一个字符的索引为0，我们可以尝试下：

```python

string = 'python'

# 取出p，对应索引为0

print(string[0]) # p

# 取出h，对应索引3

print(string[3]) # h

# 取出最后一位，对应索引5

print(string[5]) # n

```

如果字符串长度不固定，那取出最后一位就需要得到字符串长度之后再减去1，即可得到最后一位。索引从0开始，所以要减去1。

可以通过len()函数得到字符串的长度：

```python

string1 = 'python'

# 取出最后一位

print(strin1[len(string1)-1]) # n

# 得到string1的长度

print(len(string1)) # 6

string1 = '123456'

print(len(string1)) # 6

string1 = 123

print(len(string1)) # 报错

"""
整型没有len()方法
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: object of type 'int' has no len()
"""

string1 = '123'

print(len(string1)) # 3

```

索引支持负数，代表从右向左查找，最右边的为-1

```python

string1 = 'python'

# 取出最后一位

print(string[-1]) # n

# 取出倒数第三位

print(string[-3]) # h

```

如果索引超出范围，会报错，正向范围要在0~len(str)-1,负数范围在-1~-len(str)

```python

string1 = 'python'

print(string1[6]) # 报错，超出正数范围

"""
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: string index out of range
"""

print(string1[-7]) # 报错，超出负数范围

```

---

字符串也支持切片操作，所谓的切片就是取出子字符串，像我们切肉一样，要从这个🐽身上切下来哪片肉~

用到的形式就是str[起始:结束:步长],切片的时候不包含结束位置的字符

![字符串切片](image/section01/1-string.png)


```python

name = 'My Name is Mike'

print(name[0]) # M

print(name[-4]) # M

print(name[0:2]) # My

print(name[3:8]) # Name

print(name[11:14]) # Mik

print(name[11:15]) # Mike

# 如果给定一个过大的索引值(即下标值大于字符串实际长度)将被字符串实际长度所代替

print(name[5:100]) # me is Mike 相当于取到字符串的末尾

# 同样支持负数


print(name[0:-3]) # My Name is M

print(name[0:-5]) # My Name is

print(name[-5:-1]) # Mik

# 如果只给了起始点，则从起始点一直取到字符串的末尾

print(name[0:]) # My Name is Mike

print(name[3:]) # Name is Mike

# 同样也支持负数

print(name[-4:]) # Mike

print(name[-7:]) # is Mike

print(name[100:]) # '' 空字符串

# 如果省略第一个参数，代表从0开始

print(name[:5]) # My Na

print(name[:-3]) # 'My Name is M'

# 如果两个参数都不写，则返回整个字符串

print(name[:]) # My Name is Mike 不要忘了写冒号:

# 还可以设置步长，通过第三个参数

string1 = 'abcdefghijk'

print(string1[::2]) # 等差数列，每隔两个取一个

print(string1[0:5:2]) # ace

print(string1[-6:-1:2]) # fhj

# 步长同样可以为负数，代表从右向左数
# 实现字符串倒置

print(string1[::-1]) # 'kjihgfedcba'

print(string1[::-2]) # kigeca'


```

>1.接着我们可以来做一个文字小游戏叫做一一“找出你朋友中的魔鬼”也就是拼装出fiend。输入代码：
>
>word = 'friends'
>
>find_the_evil_in_your_friends =  word[0] + word[2:4] + word[-3:-1]
>
>print(find_the_evil_in_your_friends)

>2.再来看一个实际项目中的应用，同样是分片的用法。
>'http://ww1.site.cn/14d2e8ejw1exjogbxdxhj20ci0kuwex.jpg'
>'http://ww1.site.cn/85cc87jw1ex23yhwws5j20jg0szmzk.png'
>'http://ww2.site.cn/185cc87jw1ex23ynr1naj20jg0t60wv.jpg'
>'http://ww3.site.cn/185cc87jw1ex23yyvq29j20jg0t6gp4.gif'
>
>在实际项目中切片十分好用。上面几个网址（网址经过处理，所以你是打不开的）是使用 Python 编写爬虫后，从网页中解析出来的部分图片链接，现在总共有500余张附有这样链接的图片要进行下载，也就是说我需要给这500张不同格式的图片（png.jpg,gif）以一个统一的方式进行命名。通过观察规律，决定以链接尾部倒数10个字符的方式进行命名，于是输入代码如下：

```python
url = 'http://ww1.site.cn/14d2e8ejw1exjogbxdxhj20ci0kuwex.jpg'

file_name = url[-10:]

print(file_name) # 0kuwex.jpg

```
