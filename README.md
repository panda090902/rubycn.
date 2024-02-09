#include<stdio.h>
#include<string.h>
struct frame
{
int seq;
int len;
int flag;
char data[10];
} n[20],m[20],temp;
char str[100];
int count=0;
void frames()
{
int i,j,s,size,total=0;
s=strlen(str);
while(total<s)
{
size=rand()%10+1;
n[count].seq=count+1;
n[count].len=size;
n[count].flag=0;
if((total+size) < s)
{
for(i=total,j=0;j<size;i++,j++)
n[count].data[j]=str[i];
total+=size;
}
else
{
n[count].len=s-total;
for(j=0;j<n[count].len;j++)
n[count].data[j]=str[total++];
}
count+=1;
}
printf("\n SHOW THE PACKETS:\n\n");
for(i=0;i<count;i++)
{
printf("\t%d:%d\t",n[i].seq,n[i].len);
for(j=0;j<n[i].len;j++)
printf("%c",n[i].data[j]);
printf("\n");
}
}
void trans()
{
int i,j;
int c=0;
while(c<count)
{
i=rand()%count;
if(n[i].flag==0)
{
m[c++]=n[i];
n[i].flag=1;
}
}
printf("\n\n SHOW THE RANDOM PACKETS:\n\n");
for(i=0;i<count;i++)
{
printf("\t%d:%d\t", m[i].seq, m[i].len);
for(j=0;j<m[i].len;j++)
printf("%c", m[i].data[j]);
printf("\n");
}
}
void sort()
{
int i,j;
for(i=0;i<count;i++)
for(j=i+1;j<count;j++)
if(m[i].seq>m[j].seq)
{
temp=m[i];
m[i]=m[j];
m[j]=temp;
}
printf("\n\n SHOW THE SEQUENCED PACKETS:\n\n");
for(i=0;i<count;i++)
{
printf("\t%d:%d\t",m[i].seq,m[i].len);
for(j=0;j<m[i].len;j++)
printf("%c",m[i].data[j]);
printf("\n");
}
}
main()
{
printf("Enter the data: ");
scanf("%s",(str));
frames();
trans();
sort();
}
