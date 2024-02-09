#include<stdio.h>
#include<conio.h>
void prims(int n,int a[10][10],int source)
{
 int s[10],i,j,min=999,sum=0,u,v,k,t=0;
 for(i=0;i<n;i++)
 s[i]=0;
 s[source]=1;
 k=1;
 while(k<=n-1)
 {
 min=999;
 for(i=0;i<n;i++)
 {
 for(j=0;j<n;j++)
 {
 if(s[i]==1 && s[j]==0)
 {
 if(i!=j && min>a[i][j])
 {
 min=a[i][j];
 u=i;
 v=j;
 }
 }
 }
 }
 printf("\n(%d,%d)=%d",u,v,min);
 sum=sum+min;
 s[u]=1;
 s[v]=1;
 k++;
 }
 for(i=0;i<n;i++)
 {
 if(s[i]!=1)
 t=1;
 }
 if(t==0)
 printf("\ncost of min spanning tree is %d",sum);
 else
 printf("\nminimum spanning tree not possible");
}
void main()
{
 int a[10][10],n,i,j,source;
 
 printf("==========================================\n");
 printf(" Find minimum cost spanning tree using Prim's Algorithm \n");
 printf("==========================================\n");
 printf("\n Enter the number of vertices");
 scanf("%d",&n);
 printf("Enter the cost matrix 0 for self loop and 99 for no edge \n");
 printf("Enter the n*n matrx\n");
 for(i=0;i<n;i++)
 for(j=0;j<n;j++)
 scanf("%d",&a[i][j]);
 printf("Enter the source node\n");
 scanf("%d",&source);
 prims(n,a,source);
 getch();
}
