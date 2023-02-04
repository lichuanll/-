# 链表
一种线性存储结构
## 静态链表
```c++
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
```
## 动态链表
### 链表的定义
```c++
struct Node//静态指针 
{
int value;
Node *next;
};
int size=0;//记录链表大小
```
### 链表的创建
创建头节点
```c++
Node *head=new Node;
```
### 链表的操作
链表的操作主要是增删改查

#### 链表的插入操作(增)
![image](https://user-images.githubusercontent.com/109082987/216769040-2caa5887-bb4a-4463-a16a-d86aac67264c.png)
```c++
void add(int element,int index)
{
    if (index < 0 || index >= _size)
    {
        return;
    } 
    if(index==0)
    {
        Node *temp=head->next; 
        head->value=element;
        head->next=temp; 	
    }
    else
    {
        Node *_node=head;
        for(int i=0;i<index-1;i++)
            {
                _node=_node->next;
            }
        Node *temp=new Node;
        temp->value=element;
        temp->next=_node->next;
        _node->next=temp;
    }
    size++;
}
void adds(int element)
{

    Node *End=new Node;
    Node *_node=head;
    for(int i=0;i<size-1;i++)
        {
            _node=_node->next;
        }
    _node->next=End;
    End->value=element;
    End->next=NULL; 
    size++;
}
```
#### 链表的删除操作(删)
![image](https://user-images.githubusercontent.com/109082987/216769066-66cd74d2-cfd4-453d-9667-65b0559bb50e.png)

```c++
void deletes(int index)
{
    Node* _node = head;
    Node* prve = head;
    for (int i = 0;i < index - 1;i++)
        {
            _node = _node->next;
        }
    for (int i = 0;i < index - 2;i++)
        {
            prve = prve->next;
        }
    prve->next = _node->next;
    delete _node;
    _node = NULL;
    _size--;
}
```
#### 链表的修改操作(改)
![image](https://user-images.githubusercontent.com/109082987/216769087-8fd6b450-6fba-434b-9a26-07927ae81b36.png)

```c++
void set(int element, int index)
{
    Node* _node = head;
    for (int i = 0;i < index - 1;i++)
        {
            _node = _node->next;
        }
    _node->value = element;
}
```
#### 链表的查找操作(查)
![image](https://user-images.githubusercontent.com/109082987/216769122-c6223005-7de3-4b17-a4de-6ee5cea66e9f.png)
```c++
int get(int index)
{
    Node* _node = head;
    for (int i = 0;i < index - 1;i++)
        {
            _node = _node->next;
        }
    return _node->value;
}
```

