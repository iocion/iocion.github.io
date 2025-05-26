#### 1.cpp的几种循环方式

```cpp
1.Traditional for loop
for (initialization; condition; increment/decrement)
{
// loop body
}
eg : for (int i = 0 ; i < n ; i++)  //需手动指定范围 
```

```cpp
2.Range-base for loop
for (declaration : range_expression)
{
// loop body
}    //消除索引，让编译器来处理这个问题
eg:
//只读或读写访问
for (Type var : container): 默认是按值复制，var 是容器元素的副本，修改 var 不会影响容器中的原始元素。
for (Type& var : container): 按引用访问，var 是容器元素的引用，修改 var 会直接修改容器中的原始元素。
for (const Type& var : container): 按常量引用访问，效率高，且保证不会修改原始元素。这是最常用和推荐的方式，除非你需要修改元素。
// 缺点不能跳过元素或者倒序遍历，仍需要使用Traditional for loop
// 或者使用高级算法
```

```cpp
//推荐的使用方式
std:vector<int> dest[] = {1,2,3,4,5}
for(const int& var : dest)
```



#### 1.cpp的结构体

```cpp
include <string.h>
#define X 100
//cpp结构体部分
typedef struct Student{
        char name[50];
        const char* school;
        int age;
        int height;
        int weight;
        //构造函数
    	//const 变量是不可修改
        void init(int age,int height,int weight,const char* school, const char* name){
		//在cpp中为了代码规范这里的init函数不要自己命名，会出现每一次结构体的构造都需要运行init函数
         //编译器无法自身优化
        this->age = age;
        this->height = height;
        this->weight = weight;
        strcpy(this->name,name);
        this->school = school;
        }
        void who(){
                printf("我今年%d岁,来自%s大学，身高是%d,体重是%d",this->age,this->school,this->height,this->weight);
        }
        //成员函数，只支持cpp的语法
}Student;  //这种写法更优
//结构体传入函数里面

int main(){
  puts("ok");
  printf("%d\n",X);
  Student s;
  s.init(18,170,110,"安徽理工大学","李白");
  s.who();
  return 0;
      
}
```

