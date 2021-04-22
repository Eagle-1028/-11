# -11
#include<stdio.h>
#include<malloc.h>
#include<stdlib.h>


typedef struct Node
{
	int date; //数据域 
	struct Node * pNext; //指针域 
	
}NODE, *PNODE; //NODE等价于struct Node   ,PNODE等价于struct Node * 
//函数声明 
PNODE create_list(void);
void traverse_list(PNODE pHead);
bool is_empty(PNODE pHead);
int length_list(PNODE);
bool insert_list(PNODE,int ,int );
bool delete_list(PNODE,int ,int *);
void sort_list(PNODE);


int main()
{
	PNODE pHead=NULL;// 等价于 struct Node * pHead = NULL;
	pHead = create_list(); //create_list()功能：创建一个非循环单链表，并将该链表的头节点的地址付给pHead
	traverse_list(pHead);
	if (is_empty(pHead) )
	printf("链表为空！\n");
	else
	printf("链表不空！\n");
	 
	return 0;
}
PNODE create_list(void)
{
	int len;
	int i;
	int val;
	//分配了一个不存放有效数据的头节点 
	PNODE pHead = (PNODE)malloc(sizeof(NODE));
	if(NULL==pHead)
	{
		printf("分配失败，程序终止！\n");
		exit(-1);
	}
	PNODE pTail = pHead;
	pTail->pNext=NULL;
	
	printf("请输入您需要的链表节点的个数：len=");
	scanf("%d",&len);
	for(i=0;i<len;++i)
	{
		printf("请输入第%d个节点的值：",i+1);
		scanf("%d",&val);
		PNODE pNew = (PNODE)malloc(sizeof(NODE));
			if(NULL==pNew)
	{
		printf("分配失败，程序终止！\n");
		exit(-1);
		
	}
	pNew->date =val;
	pTail->pNext=pNew;
	pNew->pNext=NULL;
	pTail=pNew;
	
}
    return pHead;
}
void traverse_list(PNODE pHead)
{
	PNODE p=pHead->pNext;
	while(NULL!=p)
	{
	printf("%d ",p->date);
	p=p->pNext;	
		
	}
	printf("/n");
	
	return;
	
}
bool is_empty(PNODE pHead)
{
	if(NULL==pHead->pNext)
	return true;
	else
	return false;
	
	
	
	
}
