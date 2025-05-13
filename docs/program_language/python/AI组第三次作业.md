# AI组第三次作业 && 第四次作业

## 1.第三次作业部分

### 循环——while  for 循环

1.while循环

```python
i = 0
while i < 100:
    print("Hello World")
    i += 1
```

计算1+2+3...+100

```python
sum = 0
i = 1
while i <= 100:
    sum += i
    i += 1
print(f"1+2+3...+100的值是{sum}")
```

循环猜数案例

```python
import random

num = random.randint(1, 100)
count = 0

flag = True
while flag:
    guess_num = int(input("enter your guess number"))
    count += 1
    if guess_num == num:
        print("correct")
        flag = False
    else:
        if guess_num < num:
            print("less...")
        else:
            print("more...")

print(f"your guess times are:{count}次")
```

while循环的嵌套：

```python
i = 1
while i <= 100:
    print(f"今天是第{i}天,准备表白.....")
    j = 1
    while j<=10:
        print(f"送给小美第{j}只玫瑰花")
        j += 1
    print("小美，我喜欢你")
    i += 1
    
print(f"坚持到第{i-1}天，表白成功")  
```

#### 使用\t对多行字符串进行对齐，等同于tab键

```python
print("Hello\tWorld")
```

>>> print("Hello\tWorld")
>>> Hello   World

打印99乘法表

```python
i = 1
while i <= 9:
    j = 1
    while j <=i:
        pirnt(f"{j}*{i} = {j*i}\t",end ='')

    i += 1
    print()
```

#### for循环的基础语法

```python
# 字符串的遍历
name = "ipconfig"
count = 0

for x in name:
    if x == "p":
    	print(x)
        count += 1
```

#### range语句：

```python
# 语法一
for x in range(10):
    print(x)
# 语法二    
for x in range(5,10):   # 不包含10
    print(x)
# 语法三
for x in range(5,10,2)
	print(x)
```

#### for循环临时变量作用域

```python
i = 0
for i in range(5):
    print(i)

print(i)    
```

#### for循环的嵌套使用

```python
for i in range(1,101):
    print(f"今天是向小美的第{i}天，加油坚持。")
    
	for j in range(1,11):
        print(f"给小美送的第{j}朵玫瑰花")
    
    print("小美我喜欢你")
    
print(f"第{i}天，表白成功")
```

#### 使用for循环打印99乘法表

```python
for i in range(1,10):
    for j in range(1,i+1):
        print(f"{j} * {i} = {j*i}\t" ,end ='')
        
    print()
```

#### break 和continue语法：循环中断

```python
for i in range(1,6):
    print("yes")
    for i in range(1,8):
        print("Hello World")
        continue    #这里直接回到循环开始的部分
        print("你好")
print("no")
```

```python
import random

money = 1000

for i in range(1, 21):
    score = random.randint(1, 10)

    if score < 5:
        print(f"员工{i}的绩效{score},不满足,不发工资，下一位")
        continue  # 跳过本次循环剩余部分，直接进入下一次循环

    if money >= 1000:
        money -= 1000
        print(f"员工{i},满足条件发放工资1000，公司账户余额：{money}")
    else:
        print(f"余额不足，当前余额：{money}元，不足以发放工资")
        break  # 结束循环
```

### 第五章：函数

函数，内置函数len()

```python
str1 = "helloworld"
str2 = "nihao"
count = 0
for i in str1:
    count += 1
print(f"字符串{str1}的长度是:{count}")
# same as len(str1)
#使用function优化


def my_len(data):
    count = 0
    for i in data:
        count += 1
        print(f"字符串{data}的长度是{count}")
        
        
my_len(str2)
```

function定义：

```python
def func(value):
    function_here
    return #返回值
"""
先声明后调用函数
注意：
参数不需要可以省略
返回值不需要可以省略
"""
```

```python
def check():
    print("请出示你的身份证\t以及你的护照")
    
check() 
```

#### 函数的参数传入：

```python
def add(x,y):
    result = x + y
    print(f"{x}+{y}的结果是：{result}")
add(1,1)    
```

```python
# 体温计的function
def check_tem():
    num = int(input("请输入你的体温进行检查："))
    if num <37.5:
        print(f"体温是{num}度,体温正常请进！")
    else:
        print(f"体温是{num}度，体温过高！！！")
        
check_tem()
```

**if function has return value ,it can be resovle by other value**

```python
def add(x,y):
	result = x + y
	return result
	
r = add(1,2)
print(r)
```

**return value ~ "None" ~**

```python
def check_age(age):
    if age<=18:
		return "SUCCESS"
    return None

result = check_age(5)
if not result:   #not result == Ture
    print("未成年，不可以进入")
```

```python
# 函数说明文档
def func(x,y):
	"""
	函数说明
	:param x:形参x的说明
	:param y:形参y的说明
	:return: 返回值的说明
	"""
    函数体
    return 返回值
```

#### 函数嵌套调用

```python
def func_a():
    print("a")
def func_b():
    print("b")
   	func_a()
```

#### 函数的作用域

作用域指的是变量的作用范围（变量在哪里可以用，在哪里用不上来）

主要分为两类：局部变量以及全局变量

```python
def testA():
	num = 100  #在这里定义的num的值
    print(num)

test(A)
print(num) #在外部无法访问在testA的局部变量：出现name 'num' is not defined
```



```python
num = 100
def testA():
    print(num)

def testB():
    global num  #global关键字可以把函数内的定义的变量声名为全局变量
    num = 200
    print(num)


testB()
testA()
print(num)
```

# 源代码截图：

第一题：打印99 乘法表

![第三次第一题](C:\Users\han\Pictures\Saved Pictures\2024-06\第三次第一题.png)

## 第二题错误已更新：（2024.12.6）

**第二题：打印斐波那契数列的前n项**     

![第三次第二题](C:\Users\han\Pictures\Saved Pictures\2024-06\第三次第二题.png)

第三题：输出n到m之间的所有素数

![第三次作业第三题](C:\Users\han\Pictures\Saved Pictures\2024-06\第三次作业第三题.png)

第四题：输入一串只含有a, b, c这三个字符的字符串，输出出现次数最多的字符

![image-20241129150118311](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241129150118311.png)

第五题：输入一串字符，统计vcv出现的次数，如输入vcvcvcc时输出2

![image-20241129150726038](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241129150726038.png)
