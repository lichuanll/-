# 前缀和&差分
详细内容请参考 https://oi-wiki.org/basic/prefix-sum/
## 前缀和
前缀和可以简单理解为「数列的前  项的和」，是一种重要的预处理方式，

能大大降低查询的时间复杂度。

中心思想：求一个范围内所有元素的和 
## 二维/多维前缀和
多维前缀和的普通求解方法几乎都是基于容斥原理。
### 洛谷P1387最大正方形
```c++
/*
在一个 n * m 的只包含 0 和 1 的矩阵里找出一个不包含 0 的最大正方形，输出边长。
*/
#include <algorithm>
#include <iostream>
using namespace std;
int a[103][103];
int b[103][103];  // 前缀和数组，相当于上文的 sum[]

int main() {
  int n, m;
  cin >> n >> m;

  for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= m; j++) {
      cin >> a[i][j];
      b[i][j] =
          b[i][j - 1] + b[i - 1][j] - b[i - 1][j - 1] + a[i][j];  // 求前缀和
    }
  }

  int ans = 1;

  int l = 2;
  while (l <= min(n, m)) {  // 判断条件
    for (int i = l; i <= n; i++) {
      for (int j = l; j <= m; j++) {
        if (b[i][j] - b[i - l][j] - b[i][j - l] + b[i - l][j - l] == l * l) {
          ans = max(ans, l);  // 在这里统计答案
        }
      }
    }
    l++;
  }

  cout << ans << endl;
  return 0;
}

```
## 差分
是一种和前缀和相对的策略，可以当做是求和的逆运算。

中心思想：对一个范围内的所有元素进行相同的改变 时间复杂度 O(1)
