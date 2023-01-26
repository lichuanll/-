# 数据结构与算法

## 链表

''' c++
struct student
{
int sum;
double score;
student *next;
};
int main()
{
    student *head;
    student a,b,c;
    a.sum=1001;
    a.score=99.3;
    b.sum=1005;
    b.score=98.6;
    c.sum=1006;
    c.score=56.2;
    head=&a;
    a.next=&b;
    b.next=&c;
    c.next=NULL; 
    while(head!=NULL)
        {
            printf("%d %5.1lf\n",head->sum,head->score);//指针指向结构体时，用指针代替结构体的地址，引用结构体中的变量时用->正常变量用“.” 
            head=head->next;
        }
}
'''

