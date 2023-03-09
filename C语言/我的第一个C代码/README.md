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
  
