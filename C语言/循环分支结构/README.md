# 选择流程控制 
![image](https://user-images.githubusercontent.com/109082987/223958997-67d24fc1-4090-4868-839b-881dd73dfdce.png)

if/else，if/else if/else if....../else
## 一般形式
```c
#include<stdio.h>
int main() {
	int a = 1, b = 2, c = 3;

    if (1) {
		printf("TRUE\n");
	}
	if (0) {
		printf("FALSE\n");
	}

    if (0) {
		printf("YES\n");
	} else {
		printf("NO\n");
	}
    
	if (a == b) {
		printf("YES");
	} else {
		printf("NO");
	}

    
    if(a == b & a == c){
		printf("ALL");
	} else if (a == b & a != c) {
		printf("TWO");
	} else if (a == c & a != b) {
		printf("TWO");
	} else if (b == c & a != b ) {
		printf("TWO");
	} else if (a != b & a != c) {
		printf("NITHER");
	}

    return 0;
} 
```
## if语句的嵌套
```c
#include<stdio.h>
int main() {
	int a = 1, b = 2;
	//a为奇数，b为偶数，输出1，a,b均为奇数输出2 
	//a为偶数输出0；
	scanf("%d %d", &a, &b);
	if(a % 2 ==0){
		printf("0");
	} else {
		if (b % 2 ==0){
			printf("1");
		} else {
			printf("2");
		}
	}
	
	return 0;
} 
```
##   开关选择    switch     default
```c
#include<stdio.h>
int main() {
	int a;
	printf("input integer number :");
	scanf("%d", &a);
	switch (a) {
		case 1: printf("Monday\n");
		case 2: printf("Tuesday\n");
		case 3: printf("Wednesday\n");
		case 4: printf("Thursday\n");
		case 5: printf("Friday\n");
		case 6: printf("Saturday\n");
		case 7: printf("Sunday\n");
		default: printf("Error\n");
	}
	return 0;
} 
```
## default放在前面
```c
#include<stdio.h>
int main() {
	int n;
	scanf("%d", &n);
	switch(n) {
		case 1: n++;
		break;
		case 2: n+=2;
		break;
		default:
			n--;
	}
	
	
//	switch(n) {
//		default:
//			n--;
//		case 1: n++;
//		break;
//		case 2: n+=2;
//		break;
//		
//	}
	
	printf("%d",n);
	return 0;
} 
```
##   break 跳出操作 对循环也同样适用（星期几）
```c
#include<stdio.h>
int main() {
	int a;
	printf("input integer number :");
	scanf("%d", &a);
	switch (a) {
		case 1: printf("Monday\n");
		break;
		case 2: printf("Tuesday\n"); 
		break;
		case 3: printf("Wednesday\n"); 
		break;
		case 4: printf("Thursday\n"); 
		break;
		case 5: printf("Friday\n"); 
		break;
		case 6: printf("Saturday\n"); 
		break;
		case 7: printf("Sunday\n"); 
		break;
		default: printf("Error\n");
	}
	return 0;
} 
```
## 输入“yyyy/mm/dd”（即“年/月/日”），求是一年的第多少天
```c
#include<stdio.h>
int main(){
	int y, m, d, n = 28, sum = 0;
	scanf("%d/%d/%d", &y, &m, &d);
	if ( y % 4 == 0 & y % 100 != 0 || y % 400 == 0){
        n = 29;
    } 
	switch (m) {//switdh()括号中的结果必须是整型（或者是字符型）数据
		case 12:sum += 30;//case后面的结果必须是整型常量（包含字符型常量）
		case 11:sum += 31;//或者结果是整型（字符型）的表达式
		case 10:sum += 30;
		case 9:sum += 31;
		case 8:sum += 31;
		case 7:sum += 30;
		case 6:sum += 31;
		case 5:sum += 30;
		case 4:sum += 31;
		case 3:sum += n;
		case 2:sum += 31;
		}
		sum += d;
		printf("%d\n", sum);
	return 0;
}
```
# 循环流程控制

![image](https://user-images.githubusercontent.com/109082987/223960026-b510493e-d14c-489f-84d8-1e45c953d0fb.png)

