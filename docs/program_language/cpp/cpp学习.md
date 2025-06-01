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
std::vector<int> dest[] = {1,2,3,4,5}  //这样写是错误的
//声明了一个 std::vector<int> 数组，而不是一个 std::vector<int> 对象。
std::vector<int> dest[] 意味着 dest 是一个数组，它的每个元素都是一个 std::vector<int> 对象。由于没有指定数组大小，编译器会根据初始化列表来推断。
正确的写法如下：
std::vector<int> dest = {1,2,4,5,6} 
for(const int& var : dest)
```



#### 2.cpp的结构体

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

#### 3.C++中的枚举、模板函数、内存操作和类型比较逻辑

**这一段代码示例来自于2025：rmdb数据库系统设计大赛**

```cpp
//枚举类型
enum class Operation { FIND = 0, INSERT, DELETE };  // 三种操作：查找、插入、删除
//这种方式 FIND = 0 --- INSERT = 1 -----DELETE = 2  这里是隐式递增
// enum class 优于 enum 这里存在的问题是 enum可能在隐式转换的过程中改变整形或者其他类型导致枚举类型混淆
```

​	enum class 避免了命名空间污染和隐式转换。例如，不能直接将 Operation::FIND 与整数 0 比较，必须显式转换为整数或使用 Operation::FIND。

```cpp
static const bool binary_search = false;  //const常量的值不可以改变
```

**常量性**：const 确保 binary_search 值不可修改，编译器可能将其优化为内联常量。

**静态性**：static 保证变量在程序运行期间只有一个实例，节省内存。

**硬编码**：直接设为 false 可能是一个默认配置，可能在其他代码中被检查或覆盖。

```cpp
inline int ix_compare(const char *a, const char *b, ColType type, int col_len) {  //单列版本ix_compare
    switch (type) {
        case TYPE_INT: {
            int ia = *(int *)a;
            int ib = *(int *)b;
            return (ia < ib) ? -1 : ((ia > ib) ? 1 : 0);
        }
        case TYPE_FLOAT: {
            float fa = *(float *)a;
            float fb = *(float *)b;
            return (fa < fb) ? -1 : ((fa > fb) ? 1 : 0);
        }
        case TYPE_STRING:
            return memcmp(a, b, col_len);
        default:
            throw InternalError("Unexpected data type");
    }
}
```

```cpp
inline int func(){
    //inline 内联函数，一般将内联函数的定义放在头文件中，放在cpp文件可能导致函数重定义
    //不同编译器的优化程度不同导致性能优化程度大不相同
    //不要过度使用 inline，让编译器根据其启发式规则进行优化。 现代编译器通常足够智能，能够自动判断哪些函数应该被内联，即使你没有显式地使用 inline 关键字。
}
```

​	是否内联取决于编译器的决策，更在一方面显示了编译器的强大，会选择性的优化代码可能关键的内容

```cpp
inline int ix_compare(const char* a,const char* b,const std::vector<ColType>& col_type,const std::vector<int>& col_lens)
{
    int offset = 0; //在内存中通常表示 ： 指从内存块的起始地址或文件开头算起的字节数
    //offset 通常表示偏移量 print(arr[1+offset]) 
    for(size_t i = 0;i < con_type.size();++i){
        int res = ix_compare(a+offset,b+offset,col_type[i],col_lens[i]);
        if(res!=0) return res;
        offset += col_lens[i];
    }
    return 0;
}
```

```TXT
采用const T*的好处
高效： 因为没有进行对象拷贝。
安全： 因为函数保证不会修改原始数据
```

#### 4.cmake多文件链接构建

```bash
[ 18%] Linking CXX static library ../../lib/libstorage.a
# 加载静态库 static library ../../lib/libstorage.a
[ 24%] Built target storage
Consolidate compiler generated dependencies of target index
[ 33%] Built target index
Consolidate compiler generated dependencies of target recovery
[ 42%] Built target recovery
Consolidate compiler generated dependencies of target transaction
[ 54%] Built target transaction
Consolidate compiler generated dependencies of target system
[ 60%] Built target system
Consolidate compiler generated dependencies of target record
[ 69%] Built target record
Consolidate compiler generated dependencies of target execution
[ 75%] Built target execution
Consolidate compiler generated dependencies of target parser
[ 93%] Built target parser
Consolidate compiler generated dependencies of target rmdb

# 加载link executable ../bin/rmdb
[ 96%] Linking CXX executable ../bin/rmdb
# 最终的可执行文件是
./bin/rmdb
```

