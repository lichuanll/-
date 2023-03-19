# 时间复杂度与空间复杂度以及几种排序
## 时间复杂度
### 常数时间的操作
如果一个操作的执行时间不以具体样本量为转移，每次执行时间都是固定时间。称这样的时间为常数时间操作。
1. •常见的位运算（>>, >>>, << , | , &, ^等） 

2. • 带符号右移 ， 不带符号右移 ， 带符号左移 ，或， 与，异或(无进位相加)  

3. •赋值，比较，自增，自减操作等

4. •数组寻址操作

总之，执行时固定的操作都是常数时间的操作。

反之，执行时间不固定的操作，都不是常数时间的操作（链表的寻址）
### 常见的时间复杂度
•排名从好到差
•O(1)

•O(logN)

•O(N)

•O(N*logN)

•O(N^2)  O(N^3) … O(N^K)

•O(2^N) O(3^N) … O(K^N)

•O(N!)
### 三种时间复杂度为O(N^2)的排序方式
#### 选择排序
```c++
for (int i = 0; i < n; i++) 
    {
        int t = i;
        int min = num[i];
        for (int j = i; j < n; j++) 
            {
                if (min > num[j]) {
                    min = num[j];
                    t = j;
                }
            }
        num[t] = num[i];
        num[i] = min;
    }
```
#### 冒泡排序
```c++
for (int i = n; i > 0; i--) 
    {
        for (int j = 0; j < n - 1; j++) 
            {
                if (num[j + 1] < num[j]) 
                {
                    num[j] = num[j] ^ num[j + 1];
                    num[j + 1] = num[j] ^ num[j + 1];
                    num[j] = num[j] ^ num[j + 1];
                }
            }
    }
```
#### 插入排序
```c++
for (int i = 0; i < n; i++) 
{
    for (int j = i - 1; j >= 0 && num[j] > num[j + 1]; j--) 
        {
            num[j] = num[j] ^ num[j + 1];
            num[j + 1] = num[j] ^ num[j + 1];
            num[j] = num[j] ^ num[j + 1];
        }
}
```
## 额外空间复杂度
•你要实现一个算法流程，在实现算法流程的过程中，你需要开辟一些空间来支持你的算法流程。

•作为输入参数的空间，不算额外空间。

•作为输出结果的空间，不算额外空间。

•因为这些都是必要的，和现实目标有关的。所以都不算。

•但除此之外，你的流程如果还需要开辟空间才能让你的流程继续下去，这部分空间就是额外空间。

如果你的流程只需要开辟有限几个变量，额外空间复杂度就是O（1）
## 算法流程的常数项
•我们会发现，时间复杂度这个指标，是忽略低阶项和所有常数系数的。

•难道同样时间复杂度的流程，在实际运行时候就一样的好吗？

•当然不是

•时间复杂度只是一个很重要的指标而已，如果两个时间复杂度一样的算法，你还要去在时间上拼优劣，就进到拼常数时间

的阶段，简称拼常数项。
## 递归
### 用递归求数组最大值
•1.将[L…R]范围分成左右两半。左：[L…Mid],右[Mid…R]

•2.左部分求最大值，右部分求最大值

•3.[L…R]范围上的最大值，是max{左部分最大值，右部分最大值}

•注意 ：当2只有一个数时，就可以不用递归了
```c++
#include<stdio.h>

int process(int num[], int L, int R) {
    if (L == R) {
        return num[L];//num[L ...R]范围只有一个数，直接返回，base case
    }
    int mid = L + ((R - L) >> 1);
    int leftMax = process(num, L, mid);
    int rightMax = process(num, mid + 1, R);
    return leftMax > rightMax ? leftMax : rightMax;
}

int main() {
    int n;
    scanf("%d", &n);
    int num[1000] = { 0 };
    for (int i = 0; i < n; i++)
        {
            scanf("%d", &num[i]);
        }

    int  max = process(num, 0, n - 1);

    printf("%d", max);

    return 0;
}
```
### 汉诺塔问题
•汉诺塔（又称河内塔）问题是源于印度一个古老传说的益智玩具。大梵天创造世界的时候做了三根金刚石柱子，

在一根柱子上从下往上按照大小顺序摞着64片黄金圆盘。大梵天命令婆罗门把圆盘从

下面开始按大小顺序重新摆放在另一根柱子上。并且规定，在小圆盘上不能放大圆盘，在三根柱子之间一次只能移动一个圆盘。

数学模型：

如下图所示，从左到右有A、B、C三根柱子，其中A柱子上面有从小叠到大的n个圆盘，现要求将A柱子上的圆盘移到C柱子上去，期间只有一个原则：

一次只能移到一个盘子且大盘子不能在小盘子上面，求移动的步骤和移动的次数
![image](https://user-images.githubusercontent.com/109082987/216769762-0e227dba-187b-4040-bf93-6777b12e3767.png)
•解：（1）n == 1  

•第1次  1号盘  A---->C       sum = 1 次      

•(2)  n == 2

•第1次  1号盘  A---->B

•第2次  2号盘  A---->C

•第3次  1号盘  B---->C        sum = 3 次

•（3）n == 3

•第1次  1号盘  A---->C

•第2次  2号盘  A---->B

•第3次  1号盘  C---->B

•第4次  3号盘  A---->C

•第5次  1号盘  B---->A

•第6次  2号盘  B---->C

•第7次  1号盘  A---->C        sum = 7 次 

•不难发现规律：1个圆盘的次数 2的1次方减1

•2个圆盘的次数 2的2次方减1

• 3个圆盘的次数 2的3次方减1

•n个圆盘的次数 2的n次方减1 故：移动次数为：2^n - 1

• 实现这个算法可以简单分为三个步骤：

•（1）     把n-1个盘子由A 移到 B；

•（2）     把第n个盘子由 A移到 C； 

•（3）     把n-1个盘子由B 移到 C；

•从这里入手，在加上上面数学问题解法的分析，我们不难发现，移到的步数必定为奇数步： 

•（1）中间的一步是把最大的一个盘子由A移到C上去； 

（2）中间一步之上可以看成把A上n-1个盘子通过借助辅助塔（C塔）移到了B上， 

•（3）中间一步之下可以看成把B上n-1个盘子通过借助辅助塔（A塔）移到了C上；
```c++
#include<stdio.h>

void move(int x, int y)
{
	printf("%c->%c\n", x, y);
}
void hanoi(int n, char a, char b, char c)
{
	if (n == 1)
	{
		move(a, c);
	}
	else
	{
		hanoi(n - 1, a, c, b);//将A座上的n-1个盘子借助C座移向B座
		move(a, c);//将A座上最后一个盘子移向C座
		hanoi(n - 1, b, a, c);//将B座上的n-1个盘子借助A座移向C座
	}
}
//move中的实参与hanoi函数中的形参相对应，而hanoi函数中形参a，b，c所对应的值也是在有规律的变化
int main()
{
	int n = 0;
	scanf("%d", &n);
	hanoi(n, 'A', 'B', 'C');
	return 0;
}

long move(int n, char A, char B, char C)
{
    long c1, c2;
    if (n == 1)
    {
        return 1;
    }
    else
    {
        c1 = move(n - 1, A, C, B);
        c2 = move(n - 1, B, A, C);
        return c1 + c2 + 1;
    }
}
int main()
{
    int n;
    scanf("%d", &n);
    long a;
    a = move(n, 'A', 'B', 'C');
    printf("%d个盘子需要移动%d次", n, a);
    return 0;
}
```

## 归并排序与快速排序
### 归并排序
整体是递归，左边排好序+右边排好序+merge让整体有序

让其整体有序的过程里用了排外序方法
![image](https://user-images.githubusercontent.com/109082987/216769918-a542f149-5e4b-49c3-828a-d197de78d0d9.png)
```c++
//归并排序

#include<stdio.h>
#include<string.h>
#define ArrLen 2000

void printList(int arr[], int len) {
	int i;
	for (i = 0; i < len; i++) {
		printf("%d\t", arr[i]);
	}
}
void merge(int arr[], int start, int mid, int end) {
	int result[ArrLen];
	int k = 0;
	int i = start;
	int j = mid + 1;

	while (i <= mid && j <= end) {
		if (arr[i] < arr[j]) {
			result[k++] = arr[i++];
		}
		else {
			result[k++] = arr[j++];
		}
	}

	if (i == mid + 1) {
		while (j <= end)
			result[k++] = arr[j++];
	}
	if (j == end + 1) {
		while (i <= mid)
			result[k++] = arr[i++];
	}

	for (j = 0, i = start; j < k; i++, j++) {
		arr[i] = result[j];
	}

}

void mergeSort1(int arr[], int start, int end) {
	if (start >= end)
		return;
	int mid = (start + end) / 2;
	mergeSort1(arr, start, mid);
	mergeSort1(arr, mid + 1, end);
	merge(arr, start, mid, end);
}

//非递归方式
 
 void mergeSort2(int arr[],int N) {
	if (N < 1) {
		return;
	}
	int mergeSize = 1;//当前有序的，左组长度
	while (mergeSize < N) {
		int L = 0;
		// 0...
		while (L < N) {
			// L ... M左组（mergeSize）
			int M = L + mergeSize - 1;
			if (M >= N) {
				break;
			}
			int R = (M + mergeSize) > (N - 1) ? (N - 1) : (M + mergeSize);
			merge(arr, L, M, R);
			L = R + 1;
		}
		if (mergeSize > N / 2) {
			break;
		}
		//防止整数溢出
		mergeSize <<= 1;
	}
}

int main()
{
	int arr[1000];
	int n;
	scanf("%d", &n);
	for (int i = 0; i < n; i++) {
		scanf("%d", &arr[i]);
	}
	mergeSort1(arr, 0, n - 1);
	/*mergeSort2(arr,n);*/
	printList(arr, n);
	return 0;
}
```
### 快速排序
•同样是递归，遍历出大于与小于枢纽值的部分确定位置
  ![image](https://user-images.githubusercontent.com/109082987/216769953-7fdfa114-5924-4611-86cb-bf7e6ab40b0d.png)
```c++
#include <stdio.h>
#include< stdlib.h >

//快速排序
void quick_sort(int num[], int low, int high)
{
    int i, j, temp;
    int tmp;

    i = low;
    j = high;
    /*int t = rand() % (high - low + 1) + low;*/
    tmp = num[low];   //任命为中间分界线，左边比他小，右边比他大,通常第一个元素是基准数

    if (i > j)  //如果下标i大于下标j，函数结束运行
    {
        return;
    }

    while (i != j)//下标不相等，开始排序
    {
        while (num[j] >= tmp && j > i)
        {
            j--;
        }

        while (num[i] <= tmp && j > i)
        {
            i++;
        }//顺序正确，读取下一个

        if (j > i)
        {
            num[i] = num[i] ^ num[j];
            num[j] = num[i] ^ num[j];
            num[i] = num[i] ^ num[j];
        }
    }

    num[low] = num[i];
    num[i] = tmp;

    quick_sort(num, low, i - 1);
    quick_sort(num, i + 1, high);
}

int main()
{
    //创建一个数组
    int num[1000] = { 0 };
    int n;
    scanf("%d", &n);

    for (int i = 0; i < n; i++)
    {
        scanf("%d", &num[i]);
    }

    quick_sort(num, 0, n - 1);

    for (int i = 0; i < n; i++)
    {
        printf("%d ", num[i]);
    }

    return 0;
}
```
