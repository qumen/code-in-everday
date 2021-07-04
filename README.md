# de
c
#include "youxi.h"
int denglu()
{
   int i;
   char a[20]="2283025597";
   char b[20]="qumeng";
   char x[20];
   char y[20];
   printf("请输入账号和密码\n");
   for(i=0;i<3;i++)
   {
   	 scanf("%s%s",&x,&y);
   	 if(strcmp(a,x)==0 && strcmp(b,y)==0)
   	 {
   	 	return 1;
	 }
	 printf("账号密码有错，请重新输入\n");
   }
   
}
void isborad(char borad[ROW][COL],int row,int col)
{
	int i,j;
	for(i=0;i<row;i++)
	{
		for(j=0;j<col;j++)
		{
			borad[i][j]=' ';
		}
	}
}
void tableborad(char borad[ROW][COL],int row,int col)
{
	int i,j;
	for(i=0;i<row;i++)
	{
		for(j=0;j<col;j++)
		{
			printf(" %c ",borad[i][j]);
			if(j<COL-1)
			printf("|");
			   //控制列字符 
		}
	    printf("\n");
			if(i<row-1)
			{
			  for(j=0;j<col;j++)
			 {
				printf("---");
				if(j<col-1)
			    printf("|");
			    //控制分割线 
			 }	
		}
		printf("\n");
	}
}
void people(char borad[ROW][COL],int row,int col)   //定义用户走 
{
	int x=0,y=0;
	while(1)
	{
		printf("用户请输入>\n");
		scanf("%d%d",&x,&y);
        if(x>=1&&x<=row && y>=1&&y<=col)
        {
        	if(borad[x-1][y-1]==' ')
			{
				borad[x-1][y-1]='*';
				break;
			}
			else
			{
				printf("此坐标已被占用\n");
			}
		}
		else
		{
			printf("您输入的坐标非法\n");
		}
	}
}
void computer(char borad[ROW][COL],int row,int col)
{
	int x=0;
	int y=0;
	printf("人机输入>\n");
	while(1)
	{
		x=rand()%ROW;
		y=rand()%COL;
		if(borad[x][y]==' ')
		{
			borad[x][y]='#';
			break;
		}
	}
}
int isfull(char borad[ROW][COL],int row,int col)
{
	int i,j;
	for(i=0;i<row;i++)
	{
		for(j=0;j<col;j++)
		{
			if(borad[i][j]==' ')
			{
				return 0;  //没满 
			}		
		}
	}
	return 1;  //满了 
} 
char iswin(char borad[ROW][COL],int row,int col)
{
	int i;
	for(i=0;i<row;i++)
	{
		if(borad[0][i]==borad[1][i]&&borad[1][i]==borad[2][i] && borad[1][i]!=' ')  //横三行 
		{
			return borad[0][i];
		}
	}
	for(i=0;i<col;i++)
	{
		if(borad[i][0]==borad[i][1]&&borad[i][1]==borad[i][2] && borad[i][1]!=' ')  //竖三行 
		{
			return borad[i][0];
		}
	}
	for(i=0;i<row;i++)
	{ //双斜边 
		if(borad[0][0]==borad[1][1] && borad[1][1]==borad[2][2] &&borad[1][1]!=' ')
		{
			return borad[1][1];
		}
		if(borad[0][2]==borad[1][1] && borad[1][1]==borad[2][0] &&borad[1][1]!=' ')
		{
			return borad[1][1];
		}
		
	}
			if(1==isfull(borad,row,col))   //判断是否平局 
			{
				return 'Q';   //平局 
			}
			else
			{
				return 'C';   //继续 
			}
}
