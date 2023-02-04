# 树（tree）
1. 线性(1：1)

  a. 链表
  
  b. 栈，队列
  
2. 非线性 

  a. 1：n 树
  
  b. n : n 图
  
  ## 树
  ### 特点
结点有限个
 
结点有分支

层次关系
### 递归定义
一棵树看成一系列的结点的集合（可以为空集--空树）

一棵树由根结点和x个子树组成
### 结点
根节点：没有父结点的结点

叶节点：没由子结点的结点，度为0

兄弟结点：有相同的父节点

度：结点拥有的子树的个数
![image](https://user-images.githubusercontent.com/109082987/216769276-7548b657-61a9-449e-b56e-46f795d5b558.png)
## 树的实现
### 1.链式存储
每个结点由 数据+指针  组成

方法一：第一儿子/下一兄弟表示法
```c++
typedef struct TreeNode* PtrToNode;

struct TreeNode
{
ElemenType  Element;
PtrToNode    FirstChild;     //第一儿子
PtrToNode    NextSibling; //下一兄弟
} 
```
![image](https://user-images.githubusercontent.com/109082987/216769316-5a580415-1439-4e97-b044-9c279390f9a6.png)

方法二：左右儿子表示法

```c++
ypedef struct TreeNode* PtrToNode;
struct TreeNode
{
ElemenType  Element;
PtrToNode left;    //左儿子
PtrToNode right; //右儿子
} 
```
### 2.二叉树的实现（顺序存储）
用数组存储（用数组模拟）

某一个结点的数组下标为n

左儿子 2*n

右儿子 2* n + 1

双亲  2 / n
## 树的三大遍历
![image](https://user-images.githubusercontent.com/109082987/216769380-36b54cd7-8e43-473c-b7da-b01890aa146d.png)


