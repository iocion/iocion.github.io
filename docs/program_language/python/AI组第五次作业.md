思考题

黑马第七章，函数。掌握函数的定义，不同形式的参数（位置参数，关键字参数，默认参数，可变参数）。以及如果一个函数要接受这些不同形式的参数，怎样设计这些参数的先后顺序？了解Python中函数的返回值与C语言中的不同，以及Python中的函数可以返回哪些数据类型。了解变量的全局作用域和局部作用域的区别，掌握global关键字的使用。

```python
x = 10 # 这里的x为全局变量，函数定义里面对x的修改只能使用global关键字来修改 (这里x就相当于全局作用域)
#函数的定义
def func(*args,**kwargs):
    for arg in args:
        print(arg)   # 这里的*arg就是位置参数 ,这里的**kwargs就是关键字参数



import time

# 我在学习了python装饰器之后加深了我对函数参数位置的理解,例如计时器装饰器如下：
def calcu_time(func):
    def wrapper(*args, **kwargs):
        start_time = time.time()
        result = func(*args, **kwargs)
        end_time = time.time()
        print('总耗时为：', end_time - start_time)
        return result
    return wrapper

@calcu_time
def square(x):
    #global x 
    x = x**2  # 函数内部是局部作用域里面的内容
    print(x)
    
    

def square_test(n):
    global x
    x = x*x
    
 
 
if __name__=="__main__":   
    square(x)
    print(x) # 这里输出10，没有改变全局变量
    square(x)
    print(x)  # 这里输出100
# 通过学习到的python函数内容，python函数可以返回 整数、浮点数、字符串、列表、元组、字典、集合
# c语言返回只能返回一个值，除非你使用指针和结构体，python可以一次返回上面我所写道的所有python数据类型，显然这是python可以作为数据分析的绝对优势所在
```



函数的参数在**默认情况下是没有强制类型的**，不需要指定数据类型，python会根据传入的参数自动推断其类型。也可以在函数签名中使用类型注解，增强代码的可读性和可维护性。函数的第二行可以用文档字符串解释函数的功能。

将一个可变对象（列表，字典，集合等）传入一个函数，并在函数中改变修改数据，会不会改变原可变对象的值？不可变对象呢（字符串，元组等）？（跟C语言传入指针或者数组的区别？）（将可变对象传入函数，传递的是对象的引用。不可变对象传递的是副本）

```python

# 在c语言中，你传递数组或者结构体，你基本上都是通过指针进行传递这些数据类型的。显然不同的是，python属于标签语言，你的python中的赋值其实是数字id()里面的位置分配的地址，你传入的基本数据类型其实知识一个数值的副本，而不是应用，很难想cpp已经c一样传递出现内存泄漏等问题。

```



如何让一个形参变为可选的？（不传递这个参数时依然可以使用这个参数）数值0，空值None，单引号空字符串 '' ,双引号字符串 "" , 空列表 [] ,空元组（），空字典 {} 作为表达条件时都会返回False

```python
# 想要实现可选参数，不选使用当前的默认值
# 其实有多种方式可以实现
def test(name ="lihua"):
	print(f"名字是{name}")

test() # 不传入参数就默认使用name ="lihua"
name = "zhangsan"
test(name) #传入参数就会变成新的name

def test1(item, my_list=None):
    if my_list is None:
        my_list = [] 
    my_list.append(item)
    return my_list

print(test(1))  # 输出: [1]
print(test(2))  # 输出: [2] (而不是 [1, 2])


import random 
for _ in range(20):
    # print("".join(random.sample(list("1353535356")))
    print(''.join(random.sample(list("123456789"),6))) # 随机抽出6个字符组成随机数
```



第一题

![](C:\Users\han\Pictures\Saved Pictures\2024-06\1.png)

第二题

![image-20241222142053521](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241222142053521.png)

第三题

![image-20241222142157178](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241222142157178.png)

第四题

![image-20241222142446798](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241222142446798.png)

第五题

![image-20241222142622768](C:\Users\han\AppData\Roaming\Typora\typora-user-images\image-20241222142622768.png)



