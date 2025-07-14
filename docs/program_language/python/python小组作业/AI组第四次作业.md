# 第四次AI组作业

## 1.数据容器

```python
# list 容器  name1  name2  name3 防止一次一次的多次声名
name_list = ['小红','小兰','小黄']
print(name_list)
```

数据容器根据特点的不同，如：

- 是否支持重复元素

- 是否可以修改

- 是否有序，等

分为五类，分别是：

1. 列表: list

2. 元组: tuple

3. 字符串：str

4. 集合：set

5. 字典：dict   

 可以储存多个元素的python数据类型



```python
my_list = [1,2,3,4,5,6]
print(type(my_list))
```

嵌套列表

```python
my_list = [1,4,6,6,[3,4],[4,3]]
print(type(my_list))
print(my_list)
print(my_list[6])  # list out of range
# <class 'list'>
```

0 	1  	2	3	4

下表索引：对应相对位置的元素

列表常用操作

```python
my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]
test = my_list.index(1)
print(f"1的下标索引是{test}")
# 1的下标索引是0
my_list[0] = 2  # 修改指定下标的值

my_list.insert(1, "best")
print(f"列表插入元素后结果是{my_list}")  # insert 方法
my_list.append(3)
print(f"列表在尾部插入元素后的结果是{my_list}")  # append 方法
# 追加一个新的列表
my_list2 = ['hello', 'yes', 'nihao']
my_list.extend(my_list2)
# 列表删除元素
"""
del 列表[下表]
列表.pop(下标)
"""
del my_list[1]
print(f"delete第二个元素后的情况是{my_list}")
element = my_list.pop(1)  # pop 可以删除，并作为返回值返回
print(f"pop出第一个元素是{element}")
my_list.remove(element)  # remove方法只能删除第一个element
my_list.clear()
print(f"清空列表后{my_list}")
my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]
count = my_list.count(1)
print(f"列表中1的数量有{count}个")
count = len(my_list)
print(f"列表的总共元素有{count}个")
```

```python
sumary:
1.list.append(元素)
2.list.extend(容器)
3.list.insert(下标,元素)
4.del list[下标]
5.list.pop(下标)
6.list.remove(元素)
7.list.clear()
8.list.count(元素)
9.list.index(元素)
10.len(list)
```

列表的遍历循环

```python
mylist = ['hello', 'python', 'test']
index = 0
while index < len(mylist):
element = mylist[index]
print(f"遍历：{element}", end=' ')
index += 1
print()
for element in mylist:
print(f"遍历：{element}", end=" ")

"""
遍历：hello 遍历：python 遍历：test 
遍历：hello 遍历：python 遍历：test 
"""
```

```python
mylist = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]


def find_double():
index = 0
list_test = []
for element in mylist:
    element = mylist[index]
    if element % 2 == 0:
        list_test.append(element)
    index += 1
print(list_test)


find_double()
```

## 数据容器：元组

tuple：只读的list，防止被篡改

* 使用( ) 

* ```python
  t1 = (1, "hello", "name")
  t2 = ()
  t3 = tuple()
  for i in range(1, 4):
  value = f"t{i}"
  print(f"t{i}的类型是 {type(eval(value))}")

# 定义单个元素的元素
t4 = ("Hello",)  # 后面要加上 , 否则就不是元组
# 元组的嵌套
t5 = ((1,2,3),(4,5,6))
print(f"t5的类型是：{type(t5)},内容是{t5}")
# 下标索引取出的内容
num = t5[1,2]
print(f"下表索引取出的内容是:{num}")
```

##### 元组的相关操作

```python
index()   # 查找数据
count()	  # 统计某个数据在当前元组出现的次数
len(元组)	 # 统计元组的元素个数
```

```python
t6 = ("设置", "系统", "代码")
index = t6.index("设置")
print(f"设置在t6里面的下标是{index}")
t7 = ("设置", "设置", "系统", "代码")
count = t7.count("设置")
print(f"设置在t7里面出现了{count}次")
t8 = ("设置", "设置", "系统", "代码", "系统")
num = len(t8)
print(f"t8里面的元素数量有{num}个")
```

##### 元组的遍历

```python
# while 循环的遍历
index1 = 0
while index1 < len(t8):
  element = t8[index1]
  print(f"元组t8的元素有：{element}" , end = ' ')
  index1 += 1
# for 循环的遍历
for element in t8:
  print(f"元组t8的元素有：{element}")
```

**不能修改元组里面的元素 **

<img src="C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241130103353007.png" alt="image-20241130103353007" style="zoom:50%;" />

不支持元素的item assignment （元素的重新赋值）

```python
t9 = (1,2,3,["itcast","ittheima"])
t9[3][1] = "test"  
print(f"t9的内容是{t9}")
# t9的内容是(1, 2, 3, ['itcast', 'test'])
# 这里的内容是可以修改的
```

**元组的内部列表可以改变**

#### 字符串的定义和操作

```python
my_str = "sklhdfklhsd"
value = my_str[2]
value1 = my_str[-9]
print(value, value1)  # 字符串不支持修改指定下标的值
value = my_str.index("hdf")
print(f"字符串{my_str}中查找hdf,它的起始下标是{value}")
```

**字符串的替换 **

```python
使用replace方法 字符串.replace(str1,str2)
不是修改字符串，而是整体改变得到了一个新的字符串
```

**字符串的分隔**

```python
split方法，字符串.split(分割符字符串)
字符串本身不发生改变，而是得到了一个列表对象
```

**字符串的规整操作**

```python
strip方法，字符串.strip()  # 删除首尾的空格部分
或者是传入一个需要删除的东西 字符串.strip("12")  # 注意这里删除的只是首尾的12，不分顺序，只是简单的删除
```

```python
# str.count(str0)  统计str里面str0的数量
# len(str)   统计字符串的字符数量
同样也支持遍历
```

**序列的切片**

```python
# 对list进行切片
my_list = [1, 2, 3, 4, 5, 6, 7]
result = my_list[1:4]
print(f"result = {result}")
```

```python
# 对tuple进行切片
my_tuple = (1, 3, 5, 7, 9)
result = my_tuple[1:4]
print(f"result = {result}")
```

```python
# 对str进行切片
my_str = "Hello World"
result = my_str[::2]  # 步长为2
print(result)
result = my_str[::-1]
print(result)
# HloWrd
# dlroW olleH
```

```python
my_list = [1, 2, 3, 4, 5, 6, 7, 8, 9]
result = my_list[3:1:-1]
print(f"结果是{result}")

```

****



## 2.集合

**集合set，无序而且不重复**

```python
test_set = {"hello", "test", "python", "hello", "test", "python"}
my_set_empty = set()
print(f"my_set的内容是：{test_set},类型是{type(test_set)}")
print(f"my_set_empty的内容是：{my_set_empty},类型是{type(my_set_empty)}")
"""
my_set的内容是：{'hello', 'test', 'python'},类型是<class 'set'>
my_set_empty的内容是：set(),类型是<class 'set'>
"""
```

**无序的不支持下标索引**

```python
# 一些基本操作
set.add("content")
set.remove("content")
set.pop()   # 随机去除一个参数，因为set集合不支持下标访问
set.clear()  # 清空集合
"""
取出差集
set1 = {1, 2, 3, 4, 5}
set2 = {2, 3, 4, 5, 7}
set3 = set1.difference(set2)
print(f"取出差集之后的结果是{set3}")

消除交集相同的元素  删除set1里面和set2相同的元素，同时set2保持不变
set1.difference_update(set2)
print(set1)
set3 = set1.union(set2)
print(set3)
"""

```

```python
集合的遍历
只能使用for循环
for element in set:
  print(element)
```

#### 字典的定义

python中的字典

```python
Key : Value
Key : Value
# 通过字典可以实现key 取出 Value   储存成键值对
{key : Value ,Key : Value, ......, Key : Value}
# 定义空的字典
my_dict = {}	# 空字典定义方式1
my_dict = dict()  # 空字典定义方式2
print(f"my_dict,和my_dict1的类型是：{type(my_dict), type(my_dict1)}")
print(my_dict, my_dict1)
```

字典新的值覆盖之前出现过的key的value的值

```python
score_dict = {
  "张三":{
    "Chinese":92,
      "Math":99,
      "English":88
},"李四":{
    "Chinese":91,
      "Math":99,
      "English":98
  },"王五":{
    "Chinese":10,
      "Math":11,
      "English":18
  }
}
print(score_dict)
print(score_dict["张三"]["Chinese"])
```

##### 字典常用操作

```python
score_dict["张三"]["English"] = 100 
score = score_dict.pop("张三")
print(f"更新后的{score_dict},张三的所有分数是{score}")
```

```python
# 获取全部的Keys
my_dict = {"lili": 89, "libai": 99, "xiaoming": 100}
keys = my_dict.keys()
print(keys)
"""
dict_keys(['lili', 'libai', 'xiaoming'])
"""
for key in keys:
    print(f"字典里面的Key是：{key}")
    print(f"字典的value是：{my_dict[key]}")
    
for key in my_dict:
	print(f"字典里面的Key是：{key}")
    print(f"字典的value是：{my_dict[key]}")
```

## 五类容器的总结

list tuple str  set dict

![291d55fb4c3a09cb2dd90f56ef86b5aa_720](C:\Users\han\Documents\Tencent Files\han27065\nt_qq\nt_data\Pic\2024-11\Thumb\291d55fb4c3a09cb2dd90f56ef86b5aa_720.png)



第四次作业第一题

![image-20241129145124559](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241129145124559.png)

第四次作业第二题

![image-20241129145252738](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241129145252738.png)

第四次作业第三题

![image-20241129145355163](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241129145355163.png)

第四次作业第四题

![image-20241129145449396](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241129145449396.png)

第四次作业第五题

![image-20241129145744254](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241129145744254.png)