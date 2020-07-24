# 异常处理
## 1、2、各种异常/警告
![avatar](/异常类型.png)
## 3、try-except语句
```python
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
```

try 语句按照如下方式工作：

- 首先，执行try子句（在关键字try和关键字except之间的语句）
- 如果没有异常发生，忽略except子句，try子句执行后结束。
- 如果在执行try子句的过程中发生了异常，那么try子句余下的部分将被忽略。如果异常的类型和except之后的名称相符，那么对应的except子句将被执行。最后执行try语句之后的代码。
- 如果一个异常没有与任何的except匹配，那么这个异常将会传递给上层的try中。
```python
try:
    f = open('test.txt')
    print(f.read())
    f.close()
except OSError:
    print('打开文件出错')

# 打开文件出错
```
```python
dict1 = {'a': 1, 'b': 2, 'v': 22}
try:
    x = dict1['y']
except KeyError:
    print('键错误')
except LookupError:
    print('查询错误')
else:
    print(x)

# 键错误
```
错误从精细到粗排列

**可以放多个异常**
```python
try:
    s = 1 + '1'
    int("abc")
    f = open('test.txt')
    print(f.read())
    f.close()
except (OSError, TypeError, ValueError) as error:
    print('出错了！\n原因是：' + str(error))

# 出错了！
# 原因是：unsupported operand type(s) for +: 'int' and 'str'
```
## 4.try-except-finally语句
```python
try:
    检测范围
except Exception[as reason]:
    出现异常后的处理代码
finally:
    无论如何都会被执行的代码
```
不管try子句里面有没有发生异常，finally子句都会执行。
如果一个异常在try子句里被抛出，而又没有任何的except把它截住，那么这个异常会在finally子句执行后被抛出。
```python
def divide(x, y):
    try:
        result = x / y
        print("result is", result)
    except ZeroDivisionError:
        print("division by zero!")
    finally:
        print("executing finally clause")


divide(2, 1)
# result is 2.0
# executing finally clause
divide(2, 0)
# division by zero!
# executing finally clause
divide("2", "1")
# executing finally clause
# TypeError: unsupported operand type(s) for /: 'str' and 'str'
```
## 5.try-except-else
```python
try:
    检测范围
except:
    出现异常后的处理代码
else:
    如果没有异常执行这块代码

```
## 6.raise语句
Python 使用raise语句抛出一个指定的异常
```python
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    
# An exception flew by!
```
## 练习题
1、猜数字游戏

题目描述:

电脑产生一个零到100之间的随机数字，然后让用户来猜，如果用户猜的数字比这个数字大，提示太大，否则提示太小，当用户正好猜中电脑会提示，"恭喜你猜到了这个数是......"。在用户每次猜测之前程序会输出用户是第几次猜测，如果用户输入的根本不是一个数字，程序会告诉用户"输入无效"。
(尝试使用try catch异常处理结构对输入情况进行处理)
获取随机数采用random模块。
答：
```python
import random

i = 1
print('猜测一个0到100之间的整数。')
data = random.randint(0, 100)

while(1):
    user = input('第%d次猜，请输入一个整型数字：' %i)
    try:
        user = int(user)
    except Exception:
        print('输入无效')
    else:
        if user > data:
            print('太大')
        elif user == data:
            print('恭喜你猜到这个数字是 %d' %data)
            break
        else:
            print('太小')
    i+=1
```
![avatar](/task3习题结果.png)

