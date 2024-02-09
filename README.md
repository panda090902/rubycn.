#include <stdio.h>
void bellmanFord(int src,int graph[10][10],int n) 
{
 int dist[20],sum=0,i; 
 // Initialize distances
 for (int i = 0; i < n; i++)
 dist[i] = 999;
 dist[src] = 0; 
 // Relax all edges V-1 times
 for (int i = 0; i < n - 1; i++) 
 {
 for (int u = 0; u < n; u++)
 {
 for (int v = 0; v < n; v++) 
 {
 if (graph[u][v] && dist[u] != 999 && dist[u] + graph[u][v] < dist[v])
 dist[v] = dist[u] + graph[u][v];
 }
 }
 }
 // Check for negative weight cycles
 for (int u = 0; u < n; u++) 
 {
 for (int v = 0; v < n; v++) 
 {
 if (graph[u][v] && dist[u] != 999 && dist[u] + graph[u][v] < dist[v]) 
 {
 printf("Negative weight cycle found!\n");
 return;
 }
 }
 }
 printf("Vertex Distance from Source\n");
 for (i = 1; i < n; i++)
 printf("Distance from source %d \t to destination\t %d\t is %d\n", src,i, dist[i]); 
}
void main() 
{
 int n,i,j,source,graph[10][10],src; 
 printf(" BellmanFord Algorithm \n");
 printf("==========================================\n");
 printf("\n Enter the number of vertices");
 scanf("%d",&n);
 printf("Enter the cost matrix 0 for self loop and 99 for no edge \n");
 printf("Enter the n*n matrx\n");
 for(i=0;i<n;i++)
 {
 for(j=0;j<n;j++)
 {
 scanf("%d",&graph[i][j]);
 }
 
 }
 printf("Enter the source vertex: ");
 scanf("%d", &src);
 bellmanFord(src,graph,n); 
}
