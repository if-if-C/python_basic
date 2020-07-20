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
作用在基本类型变量X，只要不为0、0.0,就是True
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
