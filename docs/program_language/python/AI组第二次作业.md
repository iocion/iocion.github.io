# AI组第二次作业

#### 第一章

##### 1.了解和配置python的使用环境

python导学->初识python->什么是编程->python环境的搭建   

第一个python 程序：helloworld    [已完成]

#### 第二章

##### 1.字面量

六种数据类型
1.Number   2.String   3.List   4.Tuple   5.Set   6.Dictionary

字符串加上双引号，写到print里面的任然是字面量
```python
print("黑马程序员")
```

##### 2.注释

一般建议#和注释的内容用一个空格隔开   python规范要求

1.单行注释

```python
import sys  # 引入sys库
print(sys.path)  # 输出python下载的路径
```

2.多行注释

```python
"""
openeuler操作系统
opengauss数据库
kunpengkit开发者
"""
```

##### 3.变量

1.变量赋值

```python
money = 50
print("钱包还有多少钱：", money)
# 变量可以进行运算
cost = 10
leave = money - cost
print("钱包还剩多少钱：", leave, "yuan")
```

课后练习

```python
money = 50
print("当前钱包余额：", money, "元")
icream = 10
coke = 10
print("购买了冰淇凌，花费：", icream,"元")
print("购买了可乐，花费：", coke,"元")
money = money - icream - coke
print("最终钱包剩余：", money, "元")
```

##### 4.数据类型

1.type()语句可以查看变量"存储的数据"的类型信息

```python
words = 'AI组组长最美'
number = 666
int_type = type(number)
print(type(words),type(number),int_type)
```

#####    5.数据类型的转换

1.场景：字符串转数字，数字转字符串，input()语句，默认结果是字符串，如果是数字也需要转换，同时将数字转换为字符串用以写出到外部系统，等等场景的需要.

```python
number = str(888)  #万物可以转字符串，但是字符串转int类型的时候要注意""<---里面只能放数字
print(type(number), number) 
string = int("114514")
print(type(string))
float_number = float(11)
print(type(float_number),float)
```

##### 6.标识符

1.什么是标识符：变量的名字，方法的名字，类的名字

*****

标识符的命名中，只能出现

- 英文 
- 中文
- 数字
- 下划线(_)                 这四类元素，不能**使用关键字**

```python
1_name ="张三"  # 首字母不能是数字，wrong！
name_1 ="张三"  # 可以使用，True
class = 1  #不能使用关键字 wrong！
Class = 1 #True,python里面大小写是区分的
```

- 变量的命名：简短清晰 ，表明清晰每一个变量的意义——————遵守规则和规范

##### 7.运算符

1.数学运算符

```python
  # +  -  *  /   //    %   **
  # attention：//表示取整除   **表示取指数  
```

```python
print(2**4)  #得到16
```

2.赋值运算符

```python
a + = 1  # 等价于a = a + 1
a - = 1  # 等价于a = a - 1
a // = 2
```

##### 8.字符串的三种定义方式

1.单引号定义法 2.双引号定义法 3.三引号定义法

```python
name = '你好'  # 单引号定义法
name = "你好"  # 双引号定义法
name = """你好"""  # 三引号定义法  可以进行多行的赋值eg：
words = """今天过得怎么样
not bad
"""
```

2.引号的嵌套：特殊情况：需要转义字符 \ 来转义

```python
man = "'manba out'"  # 可以使用""来输出'',并且不会出现冲突
man = ""manba out"" #会出现报错 wrong!
man = "\"manba out\"" #True
```

##### 9.字符串的连接

usually 进行字面量和变量之间进行拼接

```python
name = " hellokity "
number = "110"
print("我是谁："+name + ",我的身份证是：" + number) #attention：variable 都是string类型的
#否则会throw out typeError，简单相加的缺陷，为后面的字符串格式化做铺垫
```

##### 10.字符串的格式化

```python
name = " hellokity "
number = 110
print("我是谁："+ name + ",我的身份证是：%s " % number) # % 表示我要占位  s表示将变量放入占位的地方
print("我的信息是：%s %s" %(name,number))
```

常用的三种占位符

- %d      将内容转换成整数，放入占位置
- %s       将内容转换成字符串，放入占位置
- %f        将内容转换成浮点型，放入占位置
- python3.6以后引入了f-string的占位符

```python
name = "Alice"
age = 23
print(f"Hello, {name}! You are {age} years old.")
```

##### 11.格式化的精度控制

1.可以使用辅助符号"m .n"来控制数据的宽度和精度

- m 控制宽度，要求是数字（比较少使用），设置宽度小于数字自身，不生效
- .n 控制小数点的精度，要求是数字，会进行小数点的四舍五入

```python
a = 11.234
print("%7.2f" % a)
# 输出  11.23 //attention：输出的情况是保留两位小数，并在前面补齐了两个空格由于11.23是五位字符，7-5=2
```

if m<本身的宽度：不生效

2.快速格式化字符串的方式即：f-string的占位符，不关心精度控制

##### 12.对表达式进行格式化

```python
print(f"1*3={1*3}")
```

课后练习

```python
name, stock_price, stock_code, stock_price_daily_growth_factor, growth_days = "传智科技", 19.19, "003032", 1.2, 7
# 打印基本信息
print(f"公司：{name}, 股票代码：{stock_code}, 当前股价：{stock_price}")
# 计算增长后的股价
final_stock_price = stock_price * (stock_price_daily_growth_factor ** growth_days)
# 打印增长信息
print("每日的增长系数是：%.1f, 经过%d天的增长后，股价达到了：%.2f" % (stock_price_daily_growth_factor, growth_days, final_stock_price))
```

##### 15.输入数据（input语句）

```python
name = input("what's your name:")
print("i know you are : %s" % name)  
```

可以放入提示信息在input()的语句里面，input:默认接受字符串

课后练习

```python
username = input()
usertype = input()
print("您好：%s，您是尊贵的：%s 用户，欢迎您的光临。" %(username,usertype))
#输入可以使用 username, usertype = input("请输入用户名和用户类型（用空格分隔）：").split()
# .split 可以实现通过空格将字符串分割成两个部分
```

#### 第三章

##### 1.布尔类型以及比较运算

| Type       | Describe                        | 说明                                          |
| ---------- | ------------------------------- | --------------------------------------------- |
| Number     | suport: int  float complex bool | 整数，浮点数，复数，布尔：True False          |
| String     | 描述文本的一种数据类型          | 由任意数量的字符组成                          |
| List       | 有序的可变序列                  | Python中最频繁使用的记录数据类型              |
| Tuple      | 有序的不可变序列                | 有序记录一堆不可变的Python数据集合            |
| Set        | 无序的不重复集合                | 无序记录一堆不重复的Python数据集合            |
| Dictionary | 无序Key-Value集合               | 可以无序的记录一堆Key-Value型的Python数据集合 |

```python
num1 = 10
num2 = 15
print(f"{num1 == num2}")  #attention! 这里的==不要写成=的赋值符号
```

##### 2.if语句的基本格式

```python
age =35
if age>=18:
    print(f"我没有{age}岁我只是一个18岁的程序员QWQ")
if age<30:
    print("Hello World")
print("这个时候的if 不能控制print语句")  #注意行缩进的问题，if语句下面至少要执行一个语句
```

##### 3.if elif else 语句的组合用法

```python
print("欢迎来到黑马儿童游乐园")
age = int(input("请输入你的年龄："))
if age >= 18:
    print("成年了，游玩需要补票10元")
elif age<18:
    print("您未成年，可以免费游玩。")
else:
    print("祝你玩的开心")
```

如果要使用的语句>=3,可以使用elif语句，要注意两两之间的if，和elif 以及else的搭配

```python
guess_num = input("请输入第一猜想的数字：")
if guess_num != str(10):
    guess_num = input("不对，再猜一次：")
else:
    print("恭喜一次你猜对啦")
if guess_num != str(10):
    guess_num = input("不对，请再猜最后一次：")
else:
    print("恭喜两次你猜对啦")
if guess_num != str(10):
    print("Sorry,全部猜错啦，我想的是：10")
else:
    print("恭喜最后一次成功你猜对啦")
```

##### 4.判断语句的嵌套

```python
age , year ,level = input("分别输入年龄以及入职时间以及等级：").split()
if int(age) >= 18:
    print("成年人符合，继续判断")
    if int(age) < 30:
        print("年龄达标继续判断")
        if int(year) > 2:
            print("小于30岁的成年人且入职超过2年，满足条件，可以领取")
        else:
            print("Sorry，年龄符合，但是入职时间不足")
    elif int(level) > 3:
        print("级别大于3的成年人可以直接领取礼物")
    else:
        print("您的年龄过大或者级别小于或等于3，不可以领取")

else:
    print("Sorry,未成年人不可以领取礼物")
```

##### 5.实战案例

```python
import random
num = random.randint(1,10)import random
num = random.randint(1, 10)

guess_num = int(input("输入你想要猜测的数字："))
if guess_num == num:
    print("恭喜你一次猜对了")
else:
    if guess_num > num:
        print("猜数大了")
    elif guess_num < num:
        print("猜小了")
    guess_num = int(input("再次输入你要猜测的数字："))
    if guess_num == num:
        print("恭喜你第二次猜中了")
if int(input("在1-10的范围内猜数："))>num:
    print("猜大了")
    
```





