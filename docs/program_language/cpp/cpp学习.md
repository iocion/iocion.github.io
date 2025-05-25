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

