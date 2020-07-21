# python_basic
## 1.运算符
|  操作符| 名称 |示例|
|:--:|:--:|:--:|
|  //|  整除|
|**  |幂  |
|==|等于|
|not|非|
|～|按位取反|
|&|按位与|
|^|按位异或|
|\||按位或|
|in|存在|if 'A' in ['A', 'B', 'C']:|
|not in|不存在|
|is|是|"hello" is "hello" #True|

注意：
- ==, != 对比的是两个变量的值
- is, is not 对比的是两个变量的内存地址 
- 顺序：算移位关逻
## 2.数据类型
|类型|名称|示例|
|:--:|:--:|:--:|
|int|整型||
|float|浮点型|
|bool|布尔型|True,Flase|

**布尔型**
```python
print(True + False) #1
```
bool
作用在基本类型变量X，只要不为0、0.0,就是True;
作用在容器变量( ) [ ] { }，只要有元素，就是True

## 3.类型转换
```python
print(int('520'))#520
print(str(10+10))#20
print(float(520))#520.0
```

## 4.print()
```python
list = ['apple', 'orange', 'mango']
for item in list:
    print(item, 'ok', sep='&', end='#')
# end 不换行
# sep 是每个输出后连一个‘ok’
# apple&ok#orange&ok#mango&ok#
```
## 5.原码、反码和补码
||原码|反码|补码|
|:--:|:--:|:--:|:--:|
|正数|符号位0|原码|原码|
|负数|符号位1|符号位不变，其他取反|补码+1|
- **位运算中，符号位也参与运算**

## 6.按位运算

|按位异或^|>>右移||
|:--:|:--:|:--:|
|相异为1|左边补0||
|满足交换律+结合律|n>>m即n/(2^m)|n<<m即n*2^m|
|^迅速交换两个整数-->|a^=b b^=a a^=b||
a&(-a)得最后一位1在哪

## 7.利用位运算实现整数集合


## 练习题：

leetcode 习题 136. 只出现一次的数字

给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。
尝试使用位运算解决此题。
题目说明:
```python
"""
Input file
example1: [2,2,1]
example2: [4,1,2,1,2]

Output file
result1: 1
result2: 4
"""

class Solution:
    def singleNumber(self, nums: List[int]) -> int:    
     # your code here
     res = 0
     for item in nums:
        res ^= item
        return res
```     