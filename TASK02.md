# 条件语句
## 1.if

```python
if expression:
    balabala
else:
    balabala
```

## 2. if-elif-else

```python
if expression:
    balabala
elif:
    balabala
elif:
    balabala
else:
    balabala
```
## 3.assert关键词
- assert这个关键词我们称之为“断言”，当这个关键词后边的条件为 False 时，程序自动崩溃并抛出AssertionError的异常
- 在进行单元测试时，可以用来在程序中置入检查点，只有条件为 True 才能让程序正常工作。

# 循环语句
## 1.while

```python
while 布尔:
    balabala
```  
当while后写入一个非零整数时，视为真值，执行循环体；写入0时，视为假值，不执行循环体。也可以写入str、list或任何序列，长度非零则视为真值，执行循环体；否则视为假值，不执行循环体。

## 2.while-else

```python
while 布尔:
    balabala
else:
    balabala
``` 
当while循环**全部正常**执行完的情况下，执行else输出，如果while循环中执行了跳出循环的语句，比如**break，将不执行else代码块的内容**

## 3.for循环

```python
for i in 'ILoveLSGO':
    print(i, end=' ')  # 不换行输出
# I L o v e L S G O

###############
member = ['张三', '李四', '刘德华', '刘六', '周润发']

for each in member:
    print(each)

for i in range(len(member)):
    print(member[i])

##############
dic = {'a': 1, 'b': 2, 'c': 3, 'd': 4}
for key, value in dic.items():
    print(key, value, sep=':', end=' ')

for key in dic.keys():
    print(key, end=' ')

for key in dic.values():
    print(values, end=' ')
```

## for-else 循环
```python
for 迭代变量 in 可迭代对象:
    代码块
else:
    代码块
```
当for循环正常执行完的情况下，执行else输出，如果for循环中执行了跳出循环的语句，比如 break，将不执行else代码块的内容，与while - else语句一样。

```python
for num in range(10, 20):  # 迭代 10 到 20 之间的数字
    for i in range(2, num):  # 根据因子迭代
        if num % i == 0:  # 确定第一个因子
            j = num / i  # 计算第二个因子
            print('%d 等于 %d * %d' % (num, i, j))
            break  # 跳出当前循环
    else:  # 循环的 else 部分
        print(num, '是一个质数')

# 10 等于 2 * 5
# 11 是一个质数
# 12 等于 2 * 6
# 13 是一个质数
# 14 等于 2 * 7
# 15 等于 3 * 5
# 16 等于 2 * 8
# 17 是一个质数
# 18 等于 2 * 9
# 19 是一个质数
```

## enumerate函数
返回里面每个值 还返回一个索引值
```python
for i, language in enumerate(languages, 2):
    print(i, 'I love', language)
print('Done!')

'''
2 I love Python
3 I love R
4 I love Matlab
5 I love C++
Done!
'''
```
## break 跳出当前所在层的循环
## continue 语句
终止本轮循环 开始下一轮
## pass语句
pass 语句的意思是“不做任何事”，如果你在需要有语句的地方不写任何语句，那么解释器会提示出错，而 pass 语句就是用来解决这些问题的。
pass是空语句，不做任何操作，只起到占位的作用，其作用是为了保持程序结构的完整性。尽管pass语句不做任何操作，但如果暂时不确定要在一个位置放上什么样的代码，可以先放置一个pass语句，让代码可以正常运行。
## 推导式
```python
x = [-4, -2, 0, 2, 4]
y = [a * 2 for a in x]
print(y)
# [-8, -4, 0, 4, 8]

#################
x = [(i, i ** 2) for i in range(6)]
print(x)

# [(0, 0), (1, 1), (2, 4), (3, 9), (4, 16), (5, 25)]
```

根据外面括号不同，分为数组推导式、元组、字典、集合

# 作业：
## 1、编写一个Python程序来查找那些既可以被7整除又可以被5整除的数字，介于1500和2700之间。
```python
for i in range(1500, 2701):
    if i % 7 == 0 and i % 5 == 0 :
        print(i)

#######

1505
1540
1575
1610
1645
1680
1715
1750
1785
1820
1855
1890
1925
1960
1995
2030
2065
2100
2135
2170
2205
2240
2275
2310
2345
2380
2415
2450
2485
2520
2555
2590
2625
2660
2695
```

## 2、龟兔赛跑游戏

题目描述：

话说这个世界上有各种各样的兔子和乌龟，但是研究发现，所有的兔子和乌龟都有一个共同的特点——喜欢赛跑。于是世界上各个角落都不断在发生着乌龟和兔子的比赛，小华对此很感兴趣，于是决定研究不同兔 子和乌龟的赛跑。他发现，兔子虽然跑比乌龟快，但它们有众所周知的毛病——骄傲且懒惰，于是在与乌龟的比赛中，一旦任一秒结束后兔子发现自己领先t米或以 上，它们就会停下来休息s秒。对于不同的兔子，t，s的数值是不同的，但是所有的乌龟却是一致——它们不到终点决不停止。

然而有些比赛相当漫长，全程观看会耗费大量时间，而小华发现只要在每场比赛开始后记录下兔子和乌龟的数据——兔子的速度v1（表示每秒兔子能跑v1 米），乌龟的速度v2，以及兔子对应的t，s值，以及赛道的长度l——就能预测出比赛的结果。但是小华很懒，不想通过手工计算推测出比赛的结果，于是他找 到了你——清华大学计算机系的高才生——请求帮助，请你写一个程序，对于输入的一场比赛的数据v1，v2，t，s，l，预测该场比赛的结果。

输入:

输入只有一行，包含用空格隔开的五个正整数v1，v2，t，s，l，其中(v1,v2< =100;t< =300;s< =10;l< =10000且为v1,v2的公倍数)

输出:

输出包含两行，第一行输出比赛结果——一个大写字母“T”或“R”或“D”，分别表示乌龟获胜，兔子获胜，或者两者同时到达终点。

第二行输出一个正整数，表示获胜者（或者双方同时）到达终点所耗费的时间（秒数）。

```python
##直接映射，输出字符串
v_r, v_t, t, s, l = map(lambda x:int(x), input('输入一场比赛的数据v1，v2，t，s，l，用空格隔开。'
             '其中(v1,v2< =100;t< =300;s< =10;l< =10000且为v1,v2的公倍数):').split())

###l_r 兔子； l_t乌龟； time时间
l_r = 0
l_t = 0
while(l_r<l and l_t<l):

    if l_r - l_t >= t:
        l_t += s * v_t
    else:
        l_r += v_r
        l_t += v_t
if l_r > l_t:
    print('R')
elif l_r ==l_t:
    print('D')
else:
    print('T')

print(l/v_t)

```
![avatar](/龟兔赛跑.png)