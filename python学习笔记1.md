## python基础语法

[TOC]

### 1.数据类型

| 类型  | 示例         |
| ----- | ------------ |
| int   | 10           |
| float | 2.11         |
| bool  | True , False |

### 2.列表

创建一个列表

```python
x = [1,2, 3, 4, 5, 6, 7]
print(x, type(x))
# [1,2, 3, 4, 5, 6, 7] <class 'list'>
```

添加元素

`list.append(obj)` 在列表末尾添加新的对象，只接受一个参数

`list.extend(seq)` 在列表末尾一次性追加另一个序列中的多个值

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.append('Thursday')
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Thursday']
```

删除列表中的元素

`list.remove(obj)` 移除列表中某个值

`list.pop([index=-1])` 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值

```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.remove('Monday')
print(x)  # ['Tuesday', 'Wednesday', 'Thursday', 'Friday']
```

### 3.元组

创建元组可以用小括号 ()，也可以什么都不用

```python
x=(1,2,3)
```

更新和删除一个元组

```python
week = ('Monday', 'Tuesday', 'Thursday', 'Friday')
week = week[:2] + ('Wednesday',) + week[2:]
print(week)  # ('Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday')
```

### 4.字典

```python
dic1 = {1: 'one', 2: 'two', 3: 'three'}
print(dic1)  # {1: 'one', 2: 'two', 3: 'three'}
print(dic1[1])  # one
print(dic1[4])  # KeyError: 4

dic2 = {'rice': 35, 'wheat': 101, 'corn': 67}
print(dic2)  # {'wheat': 101, 'corn': 67, 'rice': 35}
print(dic2['rice'])  # 35
```

 **字典的内置方法**

`dict.fromkeys(seq[, value])` 用于创建一个新字典，以序列 `seq` 中元素做字典的键，`value` 为字典所有键对应的初始值。

```python
seq = ('name', 'age', 'sex')
dic1 = dict.fromkeys(seq)
print(dic1)
# {'name': None, 'age': None, 'sex': None}

dic2 = dict.fromkeys(seq, 10)
print(dic2)
# {'name': 10, 'age': 10, 'sex': 10}
```



### 5.循环语句

**while**

```python
while 布尔表达式:
    代码块
```

`while`循环的代码块会一直循环执行，直到布尔表达式的值为布尔假。

**for**

```python
for 迭代变量 in 可迭代对象:
    代码块
```

每次循环，迭代变量被设置为可迭代对象的当前元素，提供给代码块使用。

**enumerate**  (会生成两个对象 i , j)

```python
for i,j in enumerate(range(1500,2701)):
    #i是从0，1，2，，，到1200 
```

**break**

`break`语句可以跳出当前所在层的循环。

**continue**

`continue`终止本轮循环并开始下一轮循环。

**列表推导式**

```python
#列表推导式
[print(i) for i in range(100)]
```

### 6.函数

函数的定义

函数以`def`关键词开头，后接函数名和圆括号()。函数执行的代码以冒号起始，并且缩进。return [表达式] 结束函数，选择性地返回一个值给调用方。不带表达式的return相当于返回`None`。

函数的调用

```python
def printme(str):
    print(str)


printme("我要调用用户自定义函数!")  # 我要调用用户自定义函数!
printme("再次调用同一函数")  # 再次调用同一函数
temp = printme('hello') # hello
print(temp)  # None
```

函数的参数

1.位置参数

```
def functionname(arg1):
    "函数_文档字符串"
    function_suite
    return [expression]
```

2.默认参数

```
def functionname(arg1, arg2=v):
    "函数_文档字符串"
    function_suite
    return [expression]
```

3.可变参数

```
def functionname(arg1, arg2=v, *args):
    "函数_文档字符串"
    function_suite
    return [expression]
```

4.关键字参数

```
def functionname(arg1, arg2=v, *args, **kw):
    "函数_文档字符串"
    function_suite
    return [expression]
```

5.命名关键字参数

```
def functionname(arg1, arg2=v, *args, *, nkw, **kw):
    "函数_文档字符串"
    function_suite
    return [expression]
```

函数的返回值

```
def add(a, b):
    return a + b


print(add(1, 2))  # 3
print(add([1, 2, 3], [4, 5, 6]))  # [1, 2, 3, 4, 5, 6]
```



### 7.模块

模块是一个包含所有你定义的函数和变量的文件，其后缀名是`.py`。模块可以被别的程序引入，以使用该模块中的函数等功能。

创建一个模块

```python
# TemperatureConversion.py
def c2f(cel):
    fah = cel * 1.8 + 32
    return fah


def f2c(fah):
    cel = (fah - 32) / 1.8
    return cel
```

- 第一种：import 模块名

【例子】

```python
import TemperatureConversion

print('32摄氏度 = %.2f华氏度' % TemperatureConversion.c2f(32))
print('99华氏度 = %.2f摄氏度' % TemperatureConversion.f2c(99))

# 32摄氏度 = 89.60华氏度
# 99华氏度 = 37.22摄氏度
```

- 第二种：from 模块名 import 函数名

【例子】

```python
from TemperatureConversion import c2f, f2c

print('32摄氏度 = %.2f华氏度' % c2f(32))
print('99华氏度 = %.2f摄氏度' % f2c(99))

# 32摄氏度 = 89.60华氏度
# 99华氏度 = 37.22摄氏度
```

