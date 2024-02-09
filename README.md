#include<stdio.h>
struct frame
{ char msg[20];
int seq;
}fr[40];
int f_no=0,front=0,rear=-1,count=0,q_size;
char q[10][20];
void insert(int i)
{
if(count==q_size)
{
printf("\n bucket is full\n");
("\n packet lost is %s\n",fr[i].msg);
sleep(4);
return;
}
rear=(rear+1)%q_size;
strcpy(q[rear],fr[i].msg);
count++;
printf("\n inserted message into the bucket is %s\n",fr[i].msg);
sleep(5);
}
void del()
{
if(count==0)
{
printf("\n bucket is empty\n");
return;
}
printf("\n deleted message is %s\n",q[front]);
sleep(5);
front=(front+1)%q_size;
count--;
}
int main()
{
int i,j,k,arrival[40],clk=0,n;
char str[100];
printf("\n enter the message: ");
scanf("%s",str);
printf("\n enter the queue size: ");
scanf("%d",&q_size);
for(i=0;str[i]!='\0';)
{
fr[f_no].seq=f_no;
for(j=i,k=0;str[j]!='\0' && k<5;j++,k++)
fr[f_no].msg[k]=str[j];
fr[f_no].msg[k]='\0';
f_no++;
i=j;
}
printf("\n show the packets: \n");
for(i=0;i<f_no;i++)
printf("frame %d is : %s\n",i,fr[i].msg);
sleep(5);
arrival[0]=1;
for(i=1;i<f_no;i++)
{
n=rand()%6;
arrival[i]=arrival[i-1]+n;
}
printf("\n arrival time of the packets\n");
for(i=0;i<f_no;i++)
printf("frame %d : %d \n",i,arrival[i]);
printf("size of the bucket is %d\n",q_size);
sleep(5);
i=0;
while(i<f_no||clk<=5*f_no)
{
printf("\nclk:: %d",clk);
while(clk==arrival[i])
{
insert(i);
i++;
}
if((clk%5)==0)
del();
clk++;
}
}
