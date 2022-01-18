# Linked-List-Implementation-of-Queue

#include<stdio.h>
#include<stdlib.h>

struct QNode{

	int key;
	struct QNode*next;
};

struct Queue{
	struct QNode*front ,*rear;
	
};

struct QNode*Insert(int k)               /*here struct QNode is a datatype */
{

	struct QNode *p= (struct QNode*)malloc(sizeof(struct QNode));
	p->key=k;
	p->next=NULL;
	return p;
	
}

struct Queue*createQueue()
{

	struct Queue*q=(struct Queue*)malloc(sizeof(struct Queue));
	q->front = q->rear= NULL;
	return q;
	
}

void enQueue( struct Queue*q, int k)
{

	struct QNode*p= Insert(k);
	if(q->rear==NULL)
	{
		q->front = q->rear= p;
		return;
	}
	
	
		q->rear->next=p;
		q->rear=p;
	
	
}

void DeQueue(struct Queue*q)
{

	if(q->front ==NULL)
	return;
	
	struct QNode*p= q->front;
	 q->front= q->front->next;
	 
	 if( q->front==NULL)
	 q->rear=NULL;
	 free(p);
	 
	
}

int main()
{

	struct Queue*q= createQueue();
	
	enQueue(q,10);
	enQueue(q,20);
	enQueue(q,30);
	enQueue(q,100);
	DeQueue(q);
	DeQueue(q);
	enQueue(q,40);
	enQueue(q,50);
	DeQueue(q);
	
	printf("Queue front =%d ", q->front->key);
	printf("\n Queue rear= %d",q->rear->key);
	return 0;
}
