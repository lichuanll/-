# 我的第一个代码
  a. nclude
 
导入头文件

  b. define（宏定义）
  
    ⅰ. #define   pai   3.1415926
    
    ⅱ. 一般写在include后 
    
    ⅲ. 表示用  pai  代替  3.1415926  ，并不是变量
    
  c. 主函数main
  ```c++
      ⅰ. int main(){
            //代码
        	
            return 0;
    ⅱ. }
  ```
  # 数据类型
  1. 基础类型
  
    ⅰ. 整型：short/int/long/long long
    
    ⅱ. 浮点型：float/double
    
    ⅲ. 字符型：char
    
      1. ASCII
      
用数字来存储字符

https://www.yuque.com/tumaoer-201rr/hyauvg/udkhoi

    ⅳ. 数据范围
    
2. 整型精度：long long>long>int

3. 浮点型精度：double>float

4. 类型转换

           隐式转换：由高精度向低精度转换
           
    显式转换：由低精度向高精度转换
    
  a. 自定义数据类型（结构体）
  # 输入输出
    a. 格式
    
    ⅰ. 不指定格式
    
      1. 输入整型，浮点型，字符型可以用空格或者回车间隔表示结束对一个数据的读取
      
      2. 输入字符串的时候只能用回车表示结束一个数据的的读取
      
    ⅱ. 指定格式
    
      1. 根据自己再scanf函数里的定义的格式表示结束对第一个数据的读取
      
  b. 输入输出控制符

整型	int	%d

浮点型	float(单精度)	%f

	double（双精度）	%lf
  
字符型	char	%c

	字符串	%s
  
  c. 转义字符“\”
  
转义字符	描述

\'	单引号

\"	双引号

\\	反斜杠

\0	空字符

\a	响铃

\b	后退

\f	走纸

\n	换行

\r	回车

\t	水平制表符

\v	垂直制表符

\xnnn	表示十六进制数(nnn)
# 运算符
  b. 优先级
![image](https://user-images.githubusercontent.com/109082987/223956955-4dd66c39-b563-4567-9b00-398309d08ea9.png)

  c. 运算符和数据类型（重点讲=）
  
    ⅰ. +（加）-（减）*（乘）/（除）%（取余，取模）
    
运算符与数据类型构成表达式

    ⅱ. 运算表达式
    
    ⅲ. 判断表达式
    
  d. 条件三目运算符
  
补充：内存中的二进制存储

（常识：一个字节byte = 8位bit）

![image](https://user-images.githubusercontent.com/109082987/223957141-c98655bc-2e3b-4ed5-a51d-1d75c7cfe14e.png)

# 习题课

## 7-8计算球的体积和表面积
```C
#include<stdio.h>
#define Pai 3.14159
int main(void){
    double r;
    scanf("%lf", &r);
    
    double s, v;
    
    s = 4 * Pai * r * r;
    v = 4 / 3.0 * Pai * r * r * r;
    printf("s=%.2lf\nv=%.2lf", s, v);
    
    return 0;
}
```
## 7-9 sdut-C语言实验-三位数整数的各位数字
```C
#include<stdio.h>
int main(void){
    int number;
    int s,b,g;
    scanf("%d", &number);
    if(number <100 || number > 999){
        printf("Please input a three digits number.");
        return 0;
}
    s = number / 100;
    b = (number - s * 100) / 10;
    g = number % 10;
    
    printf("%d = %d + %d*10 + %d*100", number,g,b,s);
    
    return 0;
}
```
## 7-10 FP15 简单求解一元二次方程
```C
#include<stdio.h>
int main(void){
    double a, b, c;
    double x1,x2;
    double derta;
    scanf("%lf %lf %lf", &a,&b,&c);
    
    derta = b * b - 4 * a * c;
    derta = sqrt(derta);
    
    x1 = (derta - b) / (2 * a);
    x2 = (0 - derta - b) / (2 * a);
    
    printf("v1=%.2lf,v2=%.2lf", x2,x1);
    
    return 0;
}
```
## 7-11 踏入计算机系列(1)查看字符的ASCII码
```C
#include<stdio.h>
int main(void){
    char a;
    scanf("%c", &a);
    int number = a;
    printf("%d", number);
    return 0;
}
```
