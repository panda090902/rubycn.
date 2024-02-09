#include<stdio.h>
#include<stdlib.h>
int d[10][10],via[10][10];
int main()
{
int i,c,j,k,n,m,cost,g[10][10],ch,count;
printf("\n enter the number of nodes:");
scanf("%d",&n);
for(i=0;i<n;i++)
{
printf("\n enter the record for router %c:\n",i+97);
for(j=0;j<n;j++)
{
printf("(%c:%c)::",i+97,j+97);
scanf("%d",&g[i][j]);
}
}
 do
 { 
 count=0;
 for(i=0;i<n;i++)
 for(j=0;j<n;j++)
 for(k=0;k<n;k++)
 if(g[i][j]+g[j][k]<g[i][k])
 {
 g[i][k]=g[i][j]+g[j][k];
 count++;
 }
 
 }while(count!=0);
 for(i=0;i<n;i++)
 {
 printf("cost table of router %c:\n",i+97);
 for(j=0;j<n;j++)
 printf("%c:%d via %c \n",j+97,g[i][j],via[i][j]+97);
 }
}
