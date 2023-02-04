# 动态规划
## 简述
### 动态规划与贪心的区别
贪心是从局部最大最小推出整体最大最小，

动态规划是从局部的状态转移到总体的状态，

叫做状态转移，这些状态中有个决策需要哪个状态的过程。

这个过程是与贪心的最大区别。贪心是一个环环相扣的过程，动态规划不一定。

动态规划是一块技巧很多的一块知识！
### 动态规划的本质
用空间换时间，设定每一步的状态，并用空间记录每一步的状态。然后进行状态转移(也叫递推)，

其中动态规划最核心的部分是状态转移方程(也叫递推公式)。
### 如何辨别需要使用动态规划解题
感觉需要枚举脑子难以想象的情况数(状态)，

而且每种情况只有两个选择(决策)，

选择其中一种进入下一种情况(状态转移)。

使用暴力递归时有重复的数据。其中动态规划就是将这些重复过程略去的做法。
### 动态规划的解题步骤
1.设置dp数组，并清楚下标与其下标所对应的值所表示的含义，

一般代表每个阶段中所问的结果

2.初始化dp数组

3.找到状态的递推关系。

4.枚举所有状态，并对所有的状态操作
## 入门例题
### 斐波那契数列
给定一个n，求斐波那契数列的第n项。
```C++
#include<iostream>
using namespace std;
int main()
{
    int n;
    int f[30];//斐波那契数列超过30项会超过32位整型的范围
    cin >> n;
    f[0]=0;
    f[1]=1;
    for(int i=2;i<=n;i++)
    {
            f[i]=f[i-1]+f[i-2];
    }
    cout <<f[n];
}
```
### 爬楼梯
 ![image](https://user-images.githubusercontent.com/109082987/215500749-54b0460d-fa3d-4bbe-b525-b446852da480.png)
 
给定一个n代表有n阶楼梯，一开始在第0阶，每次可以爬1或2个台阶，问共有多少种的方法可以爬到楼顶。

分析：定义一个数组f[50]，数组下标代表楼梯的阶数。

f[0]代表从第0阶到第0的方案数  1

f[1]代表从第0阶到第1阶的方案数 1

f[2]代表从第0阶到第2阶的方案数 2

   ...
   
f[n]代表从第0阶到第n阶的方案数  

f[n]只能从f[n-1]或f[n-2]到达f[n]，所以我们可以得出

f[n]=f[n-1]+f[n-2]
```c++
#include<iostream>
using namespace std;
int main()
{
    int n;
    int f[30];//斐波那契数列超过30项会超过32位整型的范围
    cin >> n;
    f[0]=1;
    f[1]=1;
    for(int i=2;i<=n;i++)
    {
            f[i]=f[i-1]+f[i-2];
    }
    cout <<f[n];
}
```
### 使用最小费用爬楼梯
给你一个整数数组 cost ，其中 cost[i] 是从楼梯第 i 个台阶向上爬需要支付的费用。

一旦你支付此费用，即可选择向上爬一个或者两个台阶。
一共有n阶梯。

你可以选择从下标为 0 或下标为 1 的台阶开始爬楼梯请你计算并返回达到楼梯顶部的最低花费

#测试点：

输入: cost = [1,100,1,1,1,188,1,1,100,1]

输出: 6

分析：定义一个数组f[30]，下标代表楼梯数，数组的值代表到达该下标所需要的花费。

f[n]只能从f[n-1]或f[n-2]到达f[n]，所以我们可以得出

f[n]的最小花费是min(f[n-1]+cost[n-1],f[n-2]+cost[n-2])

```c++
#include<iostream>
using namespace std;
int main()
{
    int n;
    int f[30];//斐波那契数列超过30项会超过32位整型的范围
    int cost[30]={1,100,1,1,1,188,1,1,100,1}//n=10
    cin >> n;
    f[0]=0;
    f[1]=0;
    for(int i=2;i<=n;i++)
    {
            f[i]=min(f[i-1]+cost[i-1],f[i-2]+cost[i-2]);
    }
    cout <<f[n];
}
```
### 数字三角形
从最底部任选一个起点，找到一条到达最顶部的路径。该路径所经过的数字之和最大。

![image](https://user-images.githubusercontent.com/109082987/215502530-1181540d-8cc3-4936-8d02-22d0fd56db79.png)

分析：

最顶端dp[1][1]只能通过dp[2][1]或dp[2][2]到达，所以dp[1][1]的最大值为

dp[1][1]+max(dp[2][1],dp[2][2]);

由此得出dp[i][j]=dp[i][j]+max(dp[i+1][j],dp[i+1][j+1]);
![image](https://user-images.githubusercontent.com/109082987/215938590-64bcd4a0-eea1-4831-858d-1dd31edc2e5a.png)


```c++
#include<iostream>
using namespace std;
int main()
{
    int dp[50][50];
    int n;
    cin >> n;
    for(int i=1;i<=n;i++)
    {
        for(int j=1;j<=i;j++)
        {
            cin >>dp[i][j];
        }
    }
    for(int i=n-1;i>=1;i--)
    {
        for(int j=1;j<=i;j++)
        {
           dp[i][j]=dp[i][j]+max(dp[i+1][j],dp[i+1][j+1]);
        }
    }
    cout << dp[1][1];
}
```
## 上升子序列问题
有一串数字，找出这一串数字的最大上升子序列的长度是多少。

![image](https://user-images.githubusercontent.com/109082987/215502820-c6e30d5b-1072-46e3-9917-d82807cd4336.png)

分析：设置dp数组，下标i表示第几个数，值代表以该下标数i结尾时最大上升子序列的长度。

以dp[7]结尾时，发现dp[7]与dp[1~6]都可能有关，有关的条件是a[7]>a[1~6]。

在a[1~6]满足条件时，

我们需要求出dp[7]=max(dp[1~6])

注意子序列的最小长度为1。

以dp[i]结尾时，发现dp[i]与dp[1~(i-1)]都可能有关，

有关的条件是a[i]>a[1~(i-1)]。

在a[1~(i-1)]满足条件时，

我们需要求出dp[i]=max(dp[1~(i-1)])

![image](https://user-images.githubusercontent.com/109082987/215938652-b4f13eff-6738-4756-a8e0-dead61e844d3.png)

```c++
#include<iostream>
using namespace std;
int a[100];
int dp[100];
int n;
int main()
{
    cin >> n;
    for(int i=1;i<=n;i++)
    cin>>a[i];
    dp[1]=1;

    int ans=1;
    for(int i=2;i<=n;i++)
    {
        int maxn=1;
        for(int j=1;j<i;j++)
        {
            if(a[i]>a[j])
            {
                if(dp[j]+1>maxn)
                maxn=dp[j]+1;
                
            }
        }
        dp[i]=maxn;
	 if(dp[i]>ans)
        {
            ans=dp[i];
        }
    }
	
    //第二种像动态规划套路的版本
    // for(int i=2;i<=n;i++)
    // {
        
    //     for(int j=1;j<i;j++)
    //     {
    //         if(a[i]>a[j])
    //         {
    //             dp[i]=max(dp[i],dp[j]+1);
    //         }
    //     }
    // }
    // 
    cout << ans;
}
```
## 背包问题
### 简介
解决用最小的代价，获取到最大的价值的问题

且具有每个元素具有不可拆分性
### 01背包
#### 经典做法
 ![image](https://user-images.githubusercontent.com/109082987/216768303-35db7fbd-7411-4c10-a263-ecd8f3d65000.png)
 
 ![image](https://user-images.githubusercontent.com/109082987/216768309-ca7802bb-9d0e-4cc5-a52d-af8c86af8745.png)
 
 输入：
 
4 8       表示4件物品。容量为8

2 3       为行号物品的体积和价值

3 4

4 5

5 6

输出：

10

分析：

定义一个dp数组，代表在装第i件物品时的最大价值，结果是由i-1时的最大价值+第i件物品的价值。

由于由容量限制

定义一个dp[][]数组，行代表物体编号，列代表背包容量,代表在容量为j时装i种物品能装的最大价值，结果为：

dp[i][j]=max(选择第i个物品,不选择第i个物品)

如果选择第i个物品

dp[i-1][j-w[i]]为容量为j-w[i]时的最大价值

dp[i-1][j-w[i]]+c[i]

不选择 

dp[i][j]=dp[i-1][j]

当然选择的前提是j>w[i]

输入：

4 8       表示4件物品。容量为8

2 3       为行号物品的体积和价值

3 4

4 5

5 6

输出：

10

![image](https://user-images.githubusercontent.com/109082987/216768377-ec640ec7-69ed-450e-b745-dc36701dbeac.png)

```c++
#include<bits/stdc++.h>
using namespace std;
int n,c;
int dp[4000][4000];
int w[4000];
int v[4000];
//0-1背包 
int main()
{
    cin >> n >> c;
	for(int i=1;i<=n;i++)
	cin >> w[i] >> v[i];
    for(int i=1;i<=n;i++)
    {
        for(int j=1;j<=c;j++)
        {
            dp[i][j]=dp[i-1][j];
            if(j>=w[i])
            {
               dp[i][j]=max(dp[i][j],dp[i-1][j-w[i]]+v[i]); 
            }    
        }
    }
    cout << dp[n][c];
    
}
```
#### 滚动数组优化
![image](https://user-images.githubusercontent.com/109082987/216768422-f07d84a1-5334-4cbf-8a7d-58ebe72f664a.png)

我们发现，我们数组的每一行都只会用到上一行，来进行对数据的操作，

所以i-1以上行的数据就没有用处。

所以我们可以用一个一维数组来进行枚举，并不断迭代这个一维数组的数据。

这样节省了空间。

不过要逆向枚举这个数组。因为用的是旧数据

如果正向枚举的话

输入：

4 8       表示4件物品。容量为8

2 3       为行号物品的体积和价值

3 4

4 5

5 6

输出：

10

![image](https://user-images.githubusercontent.com/109082987/216768449-8edaa59a-4271-4fce-b242-35a06ae96f38.png)
```c++
#include<bits/stdc++.h>
using namespace std;
int n,c;
int dp[4000];
int w[4000];
int v[4000];
//0-1背包 
int main()
{
    cin >> n >> c;
	for(int i=1;i<=n;i++)
	cin >> w[i] >> v[i];
    for(int i=1;i<=n;i++)
    {
        for(int j=c;j>=w[i];j--)
        {
            dp[j]=max(dp[j],dp[j-w[i]]+v[i]);  
        }
    }
    cout << dp[c];
    
}
```
### 完全背包

![image](https://user-images.githubusercontent.com/109082987/216768543-545d955c-37a3-421c-bb2c-be9db0e98d62.png)

![image](https://user-images.githubusercontent.com/109082987/216768547-492f6a73-e137-4ab8-bd87-24ce5b919cca.png)

#### 朴素做法
分析:定义一个dp[][]数组，代表再背包容量为列号时，装前行号个物品的的最大价值。

dp[i][j]=max(在j容量下，不选第i个物品的价值，在j容量下，max(选择k个i物品时的最大价值))

如果不选择第i个物品，dp[i][j]=dp[i-1][j]

如果选择第i个物品：

选1个dp[i][j]=dp[i-1][j-w[i]]+c[i]

选2个dp[i][j]=dp[i-1][j-2*w[i]]+2*c[i]

...

选k个dp[i][j]=dp[i-1][j-k*w[i]]+k*c[i]

其中k<=j/w[i]

![image](https://user-images.githubusercontent.com/109082987/216768589-f86f650b-a945-47eb-8111-703cbd2dcce5.png)

![image](https://user-images.githubusercontent.com/109082987/216768595-9658db25-e48b-4d0d-ae88-5cbe2b8fc5ce.png)

```c++
#include<iostream>
using namespace std;
int n,m,c;
int dp[4000][4000];
int w[4000];
int v[4000];
int main()
{
    cin >> n >> c;
	for(int i=1;i<=n;i++)
	cin >> w[i] >> v[i];
    for(int i=1;i<=n;i++)
    {
        for(int j=1;j<=c;j++)
        {
            for(int k=0;k<=j/w[i];k++)
            {
                dp[i][j]=max(dp[i-1][j],dp[i-1][j-k*w[i]]+k*c[i];
            }
        }
    }
    cout << dp[n][c];
}

```
#### 经典做法
由于每种物品是无限个，所以，dp[i][j]的上一个状态，也可以继续拿i物品，

所以如果拿第i个物品，它的上一个状态就不是dp[i-1]那一行了，而是dp[i]那一行。

所以如果拿第i个物品：

dp[i][j]=dp[i][j-w[i]]+c[i]

01背包：dp[i][j]=dp[i-1][j-w[i]]+c[i]
![image](https://user-images.githubusercontent.com/109082987/216768637-3b1e6b74-2b82-4e59-b032-de11b1d376d3.png)

```c++
#include<iostream>
using namespace std;
int n,m,c;
int dp[4000][4000];
int w[4000];
int v[4000];
int main()
{
    cin >> n >> c;
	for(int i=1;i<=n;i++)
	cin >> w[i] >> v[i];
    for(int i=1;i<=n;i++)
    {
        for(int j=1;j<=c;j++)
        {
            if(j>=w[i])
            {
                dp[i][j]=max(dp[i-1][j],dp[i][j-w[i]]+v[i]);
            }
        }
    }
    cout << dp[n][c];
}
```
#### 滚动数组优化

由于i为本行数据，后面的数据依赖前面的新数据，所以，要正向枚举

```c++
#include<iostream>
using namespace std;
int n,m,c;
int dp[4000];
int w[4000];
int v[4000];
int main()
{
    cin >> n >> c;
	for(int i=1;i<=n;i++)
	cin >> w[i] >> v[i];
    for(int i=1;i<=n;i++)
    {
        for(int j=w[i];j<=c;j++)
        {   
             dp[j]=max(dp[j],dp[j-w[i]]+v[i]); 
        }
    }
    cout << dp[n][c];
}
```
