# 列表
## 简单数据类型
整型<class 'int'>
浮点型<class 'float'>
布尔型<class 'bool'>

## 容器数据类型
列表<class 'list'>
元组<class 'tuple'>
字典<class 'dict'>
集合<class 'set'>
字符串<class 'str'>

##向列表添加数据
```python
x.append('tuesday')
```
- 此元素如果是一个 list，那么这个 list 将作为一个整体进行追加，注意append()和extend()的区别
- list.extend(seq) 在列表末尾一次性追加另一个序列中的多个值（用新列表扩展原来的列表）
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.extend(['Thursday', 'Sunday'])
print(x)  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday', 'Thursday', 'Sunday']

print(len(x))  # 7
```
- 严格来说 append 是追加，把一个东西整体添加在列表后，而 extend 是扩展，把一个东西里的所有元素添加在列表后。

- list.insert(index, obj) 在编号 index 位置插入 obj。
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
x.insert(2, 'Sunday')
print(x)
# ['Monday', 'Tuesday', 'Sunday', 'Wednesday', 'Thursday', 'Friday']

print(len(x))  # 6
```
## 删除
list.remove(obj) 移除列表中某个值的第一个匹配项
list.pop([index=-1]) 移除列表中的一个元素（默认最后一个元素），并且返回该元素的值
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
y = x.pop()
print(y)  # Friday

y = x.pop(0)
print(y)  # Monday

y = x.pop(-2)
print(y)  # Wednesday
print(x)  # ['Tuesday', 'Thursday']
```
- remove 和 pop 都可以删除元素，前者是指定具体要删除的元素，后者是指定一个索引。
- 如果知道要删除的元素在列表中的位置，可使用del语句。
## 索引
```python
x = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(x[3:])  # ['Thursday', 'Friday']
print(x[-3:])  # ['Wednesday', 'Thursday', 'Friday']

3 “：”复制所有元素
week = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
print(week[:])  
# ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']
```

## 常用操作符
- 等号操作符：==
- 连接操作符 +
- 重复操作符 *
- 成员关系操作符 in、not in
- 「等号 ==」，只有成员、成员位置都相同时才返回True。

列表拼接有两种方式，用「加号 +」和「乘号 *」，前者首尾拼接，后者复制拼接。
```python
list1 = [123, 456]
list2 = [456, 123]
list3 = [123, 456]

print(list1 == list2)  # False
print(list1 == list3)  # True

list4 = list1 + list2  # extend()
print(list4)  # [123, 456, 456, 123]

list5 = list3 * 3
print(list5)  # [123, 456, 123, 456, 123, 456]

list3 *= 3
print(list3)  # [123, 456, 123, 456, 123, 456]

print(123 in list3)  # True
print(456 not in list3)  # False
```
## 其它
- list.count(obj) 统计某个元素在列表中出现的次数
- list.index(x[, start[, end]]) 从列表中找出某个值第一个匹配项的索引位置 
- list.reverse() 反向列表中元素
- list.sort(key=None, reverse=False) 对原列表进行排序
reverse -- 排序规则，reverse = True 降序， reverse = False 升序（默认）。
```python
x = [123, 456, 789, 213]
x.sort()
print(x)
# [123, 213, 456, 789]

x.sort(reverse=True)
print(x)
# [789, 456, 213, 123]


# 获取列表的第二个元素
def takeSecond(elem):
    return elem[1]


x = [(2, 2), (3, 4), (4, 1), (1, 3)]
x.sort(key=takeSecond)
print(x)
# [(4, 1), (2, 2), (1, 3), (3, 4)]

x.sort(key=lambda a: a[0])
print(x)
# [(1, 3), (2, 2), (3, 4), (4, 1)]
```

# 元组 tuple
**小括号把所有元素绑在一起，逗号隔开**
- tuple被创建后就不能对其进行修改，类似字符串。
- 元组与列表类似，也用整数来对它进行索引 (indexing) 和切片 (slicing)
- tuple里面元素是各种类型的
- 元组中只包含一个元素时，需要在元素后面添加逗号，否则括号会被当作运算符使用。
```python
print(8 * (8))  # 64
print(8 * (8,))  # (8, 8, 8, 8, 8, 8, 8, 8)
```
## 内置方法
- 元组大小和内容都不可更改，因此只有 count 和 index 两种方法。
【例子】
```python
t = (1, 10.31, 'python')
print(t.count('python'))  # 1
print(t.index(10.31))  # 1
count('python') 是记录在元组 t 中该元素出现几次，显然是 1 次
index(10.31) 是找到该元素在元组 t 的索引，显然是 1
```
## 解压元组
```python
t = (1, 10.31, 'python')
(a, b, c) = t
print(a, b, c)
# 1 10.31 python

t = (1, 10.31, ('OK', 'python'))
(a, b, (c, d)) = t
print(a, b, c, d)
# 1 10.31 OK python

```
- 通配符 #
```python
t = 1, 2, 3, 4, 5
a, b, *rest, c = t
print(a, b, c)  # 1 2 5
print(rest)  # [3, 4]
```
- 如果你根本不在乎 rest 变量，那么就用通配符「*」加上下划线「_」。
```python
t = 1, 2, 3, 4, 5
a, b, *_ = t
print(a, b)  # 1 2
```
# 练习题
1、元组概念
写出下面代码的执行结果和最终结果的类型
(1, 2)*2
(1, )*2
(1)*2
分析为什么会出现这样的结果.
答：
(1, 2)*2 输出： （1，2，1，2） tuple
(1, )*2  输出：  （1，1）     tuple
(1)*2    输出：   2          int

2、拆包过程是什么？
a, b = 1, 2
上述过程属于拆包吗？
可迭代对象拆包时，怎么赋值给占位符？
答：不属于拆包
- 拆包: 对于函数中的多个返回数据, 去掉元组, 列表 或者字典 直接获取里面数据的过程.
- 对字典拆包后获取的是字典的key值, 而不是value值
- 任何可迭代对象(列表、元祖、字符串、文件对象、迭代器和生成器等)拆包时，可以用\*_对不需要的元素占位

# 字符串
- 三引号允许一个字符串跨多行，字符串中可以包含换行符、制表符以及其他特殊字符。
## 字符串常用的内置方法
- capitalize() 将字符串的第一个字符转换为大写。
- lower() 转换字符串中所有大写字符为小写。
- upper() 转换字符串中的小写字母为大写。
- swapcase() 将字符串中大写转换为小写，小写转换为大写
```python
str2 = "DAXIExiaoxie"
print(str2.lower())  # daxiexiaoxie
print(str2.upper())  # DAXIEXIAOXIE
print(str2.swapcase())  # daxieXIAOXIE
```
- count(str, beg= 0,end=len(string)) 返回str在 string 里面出现的次数，如果beg或者end指定则返回指定范围内str出现的次数。
```python
str2 = "DAXIExiaoxie"
print(str2.count('xi'))  # 2
```
- endswith(suffix, beg=0, end=len(string)) 检查字符串是否以指定子字符串 suffix 结束，如果是，返回 True，否则返回 False。如果 beg 和 end 指定值，则在指定范围内检查。
- startswith(substr, beg=0,end=len(string)) 检查字符串是否以指定子字符串 substr 开头，如果是，返回 True，否则返回 False。如果 beg 和 end 指定值，则在指定范围内检查。
- find(str, beg=0, end=len(string)) 检测 str 是否包含在字符串中，如果指定范围 beg 和 end，则检查是否包含在指定范围内，如果包含，返回开始的索引值，否则返回 -1。
- rfind(str, beg=0,end=len(string)) 类似于 find() 函数，不过是从右边开始查找。
```python
str2 = "DAXIExiaoxie"
print(str2.endswith('ie'))  # True
print(str2.endswith('xi'))  # False
print(str2.startswith('Da'))  # False
print(str2.startswith('DA'))  # True

str2 = "DAXIExiaoxie"
print(str2.find('xi'))  # 5
print(str2.find('ix'))  # -1
print(str2.rfind('xi'))  # 9
```
- isnumeric() 如果字符串中只包含数字字符，则返回 True，否则返回 False。
- strip([chars]) 在字符串上执行lstrip()和rstrip()
删掉左边空格 和 右边空格
- split分割
```python
str5 = ' I Love LsgoGroup '
print(str5.strip().split())  # ['I', 'Love', 'LsgoGroup']
print(str5.strip().split('o'))  # ['I L', 've Lsg', 'Gr', 'up']

u = "www.baidu.com.cn"
# 分割两次
print(u.split(".", 2))  # ['www', 'baidu', 'com.cn']
# 分割两次，并把分割后的三个部分保存到三个变量
u1, u2, u3 = u.split(".", 2)
print(u1)  # www
print(u2)  # baidu
print(u3)  # com.cn

string = "hello boy<[www.baidu.com]>byebye"
print(string.split('[')[1].split(']')[0])  # www.baidu.com
print(string.split('[')[1].split(']')[0].split('.'))  # ['www', 'baidu', 'com']
```
- splitlines([keepends]) 按照行('\r', '\r\n', \n')分隔，返回一个包含各行作为元素的列表，如果参数keepends为 False，不包含换行符，如果为 True，则保留换行符。

```python
str6 = 'I \n Love \n LsgoGroup'
print(str6.splitlines())  # ['I ', ' Love ', ' LsgoGroup']
print(str6.splitlines(True))  # ['I \n', ' Love \n', ' LsgoGroup']
```
## 字符串格式化
- format 格式化函数
```python
str8 = "{0} Love {1}".format('I', 'Lsgogroup')  # 位置参数
print(str8)  # I Love Lsgogroup

str8 = "{a} Love {b}".format(a='I', b='Lsgogroup')  # 关键字参数
print(str8)  # I Love Lsgogroup

str8 = "{0} Love {b}".format('I', b='Lsgogroup')  # 位置参数要在关键字参数之前
print(str8)  # I Love Lsgogroup

str8 = '{0:.2f}{1}'.format(27.658, 'GB')  # 保留小数点后两位
print(str8)  # 27.66GB
```
|符 号|	描述|
|:--:|:--:|
|%c|	格式化字符及其ASCII码
%s|	格式化字符串，用str()方法处理对象
%r|	格式化字符串，用rper()方法处理对象
%d|	格式化整数
%o|	格式化无符号八进制数
%x|	格式化无符号十六进制数
%X|	格式化无符号十六进制数（大写）
%f|	格式化浮点数字，可指定小数点后的精度
%e	|用科学计数法格式化浮点数
%E|	作用同%e，用科学计数法格式化浮点数
%g|	根据值的大小决定使用%f或%e
%G|	作用同%g，根据值的大小决定使用%f或%E
```python
print('%c' % 97)  # a
print('%c %c %c' % (97, 98, 99))  # a b c
print('%d + %d = %d' % (4, 5, 9))  # 4 + 5 = 9
print("我叫 %s 今年 %d 岁!" % ('小明', 10))  # 我叫 小明 今年 10 岁!
print('%o' % 10)  # 12
print('%x' % 10)  # a
print('%X' % 10)  # A
print('%f' % 27.658)  # 27.658000
print('%e' % 27.658)  # 2.765800e+01
print('%E' % 27.658)  # 2.765800E+01
print('%g' % 27.658)  # 27.658
text = "I am %d years old." % 22
print("I said: %s." % text)  # I said: I am 22 years old..
print("I said: %r." % text)  # I said: 'I am 22 years old.'
```
- 格式化操作符

|符号|	功能|
|:--:|:--:|
m.n|	m 是显示的最小总宽度,n 是小数点后的位数（如果可用的话）
-	|用作左对齐
+	|在正数前面显示加号( + )
\#	|在八进制数前面显示零('0')，在十六进制前面显示'0x'或者'0X'(取决于用的是'x'还是'X')
0	|显示的数字前面填充'0'而不是默认的空格
```python
print('%5.1f' % 27.658)  # ' 27.7'
print('%.2e' % 27.658)  # 2.77e+01
print('%10d' % 10)  # '        10'
print('%-10d' % 10)  # '10        '
print('%+d' % 10)  # +10
print('%#o' % 10)  # 0o12
print('%#x' % 108)  # 0x6c
print('%010d' % 5)  # 0000000005
```
# 练习题
1、字符串函数回顾
- 怎么批量替换字符串中的元素？
答： replace(old, new [, max]) 把 将字符串中的old替换成new，如果max指定，则替换不超过max次。
- 怎么把字符串按照空格进⾏拆分？
答： s.split()
- 怎么去除字符串⾸位的空格？
答： s.lstrip()
2、实现isdigit函数
题目要求
实现函数isdigit， 判断字符串里是否只包含数字0~9
```python

def isdigit(string):
    """
    判断字符串只包含数字
    :param string:
    :return:
    """
    # your code here
    if not string:
        return False
    for i in string:
        if not(48 <= ord(i) <= 57):
            return  False
    return True

```
3、leetcode 5题 最长回文子串
给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为 1000。
示例:
输入: "babad"
输出: "bab"
输入: "cbbd"
输出: "bb"
```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        size = len(s)
        if size < 2:
            return s
        #判断给定字符串的长度，长度为1的一定是回文，直接返回
        dp = [[False for _ in range(size)] for _ in range(size)] #初始化二维数组dp[i][j]都为False
        max_len = 1
        start = 0
        for i in range(size):
         #dp[i][j]表示子串是否为回文子串。单个字符一定是回文串，因此把对角线初始化为true
            dp[i][i] = True
        for j in range(1, size):  #i为行，j为列（从上到下，从左到右填表）
            for i in range(0, j):
                if s[i]==s[j]: #回文序列必须满足左右两头相等
                    if j-i<3:
                        dp[i][j] = True
                    else:
                        dp[i][j] = dp[i+1][j-1] #状态转移方程（左右边界各往中间移动）
                else:
                    dp[i][j] = False
                if dp[i][j]:
                    cur_len = j-i+1 #记录子串长度
                    if cur_len > max_len:
                        max_len = cur_len
                        start = i#子串起始位置
        return s[start:start+max_len]
```