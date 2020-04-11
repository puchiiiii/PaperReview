```c++
int a[1001][1001];
 long int step[1001][1001];
 int main()
 {
 	int n,i,j,flag = 0;
 	scanf("%d",&n);
 	for (i=1;i<=n;i++)
 	{
 		for(j=1;j<=i;j++)
 		{
 			scanf("%d",&a[i][j]);
 			step[i][j] = 100000;
 		}
 	}
 	step[1][0] = a[1][1];
 	step[1][2] = a[1][1];
 	for (i=2;i<=n;i++)
 	{
 		while(1)
 		{	
 			step[i][0] = step[i][i];
 			step[i][i+1] = step[i][1];
 			flag = 1;
 			for (j=1;j<=i;j++)
 			{
 				//
 				if (step[i][j]>step[i-1][j]+a[i][j])
 				{
 					step[i][j] = step[i-1][j]+a[i][j];
 					flag = 0;
 				}
 				if (step[i][j]>step[i-1][j-1]+a[i][j])
 				{
 					step[i][j] = step[i-1][j-1]+a[i][j];
 					flag = 0;
 				}
 				if (step[i][j]>step[i][j-1]+a[i][j])
 				{
 					step[i][j] = step[i][j-1]+a[i][j];
 					flag = 0;
 				}
 				if (step[i][j]>step[i][j+1]+a[i][j])
 				{
 					step[i][j] = step[i][j+1]+a[i][j];
 					flag = 0;
 				}
 			}
 			if (flag == 1)
 				break;
 		}
 
 	}
 
 	printf("%ld",step[n][1]);
 	//system("pause");
 	return 0;
 
 }
```
