#jms
 #include<stdio.h>
#include<conio.h>
void main() {
int i,m;
 long int opt[10],ml[10],pess[10],hisdata,laborrate;
 float estvalue,Total=0,Cost,TotalCost,Effort;
 printf("Enter the number of modules:");
 scanf("%d",&m);
 for( i=0;i<m;i++)
   {
    printf("Enter the optimistic,most Likely,Pessimistic for module %d",i+1);
    scanf("%ld%ld%ld",&opt[i],&ml[i],&pess[i]);   }
   printf("\n Enter the Historical Data :");
   scanf("%ld",&hisdata);
   printf("\n Enter the Labor Rate:");
   scanf("%ld",&laborrate);
   for(i=0;i<m;i++)
    {
     estvalue=(opt[i]+(4*ml[i])+pess[i])/6 ;
     printf("The Estimated value for module %d is %f\n",i+1,estvalue);
     Total=Total+estvalue;
    }
    printf("The Total Estimated Lines Of Code is %f\n",Total);
    Cost= laborrate/hisdata;
    printf("The Cost per LOC is %f\n",Cost);
    TotalCost=Total*Cost;
    printf("The Cost per software is 0.2%f\n",TotalCost);
    Effort=Total/hisdata;
    printf("The Effort per software is %f\n",Effort);

 }
     







