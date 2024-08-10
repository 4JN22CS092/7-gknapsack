# 7-gknapsack

Greedy Knapsack:
#include<stdio.h>
#include<conio.h>
void Gknapsack();
int max(int,int);
int i,j,n,M1,p[10],w[10], sol[10];
float ratio[10];
void main()
{
printf("\n enter the no. of items:\t");
scanf("%d",&n);
printf("\n enter the weight of the each item:\n");
for(i=1;i<=n;i++)
{
scanf("%d",&w[i]);
}
printf("\nenter the profit of each item:\n");
for(i=1;i<=n;i++)
{
scanf("%d",&p[i]);
}
printf("\nenter the knapsack's capacity:\t");
scanf("%d",&M1);
Gknapsack();
}
void Gknapsack()
{
int sum=0,q;
for(i=1;i<=n;i++)
{
ratio[i]=(float)p[i]/w[i];
//profit to weight ratio
}
for (q=1;q<=n;q++)
{
float max=0.0;
int k = 0; //to store max ratio index
for(i=1;i<=n;i++)
{
if((ratio[i] > max) && (sol[i] == 0))
{
max=ratio[i];
k = i;
}
}
if(M1>= w[k])
{
sol[k] = 1; //selected
M1 = M1 - w[k];
sum = sum + p[k];
}
else
{
sol[k] = -1; //cannot select
}
}
for(i=1;i<=n;i++)
{
if(sol[i] == -1)
sol[i] = 0;
}
printf("\nSolution with Greedy Method:%d ",sum);
printf("The solution vector is:");
for(i=1;i<=n;i++)
printf(" %d\t",sol[i]);
}
