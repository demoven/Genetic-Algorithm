/*
	Genetic algorithm that can envolve from random
	string for other one that you want. I don't test 
	very big strings, so don't know if it's work.
	Sometimes it takes a lot of time to evolve, but 
	I'm still trying to improve it.
*/

#include <stdlib.h>
#include <stdio.h>
#include <time.h>
#include <string.h>
#define N 14 //dont forget to change this if you try other string

int calcfitness(char *pop, char *res);

void mutation(char *father, char *mother,char *son);

void selection(char *father, char *mother,char *res,char *son);

void crossover(char *father,char *mother,char *son);

void main(void)
{
	char res[N]=" ",son[N]="",mother[N]="",father[N]="";
	
	clock_t start, stop;

	start = clock();
	for(int i=0;i<N;i++)
	{
		mother[i]=((rand())%(91+65));
		mother[N-1]='\0';
		father[i]=((rand())%(91+65));
		father[N-1]='\0';
	}

	while(calcfitness(son,res)!=0)
	{
		if(rand()%2==0)
			crossover(father,mother,son);
		else
			mutation(father,mother,son);

		selection(father,mother,res,son);
	}

	stop = clock();
	int diff = stop-start;

	printf("Result: %s and you take %d\n\n",res,diff);

	system("pause");
}

int calcfitness(char *pop,char *res)
{
	int fit=0,fitnew=99999999;
	char goal[N]="Hello, World!"; //just exemple
	for(int i=0;i<N;i++)
	{
		fit=fit+abs(goal[i]-pop[i]);
	}
	if(fit==0)
		strcpy(res,pop);

	if(fit<fitnew)
	{
		printf("fit: %d, specie: %s\n\n",fit,pop);
		fitnew=fit;
	}
	
	return fit;
}

void mutation(char *father, char *mother,char *son)
{
	int i=0;

		if((rand() % 2)==0) //mutation
		{
			son[i=rand() % (N-1)]=((rand()) % (91+65));
		}
		else //recive genes from parents
		{
			if((rand() % 2)==0)
			{
				son[i=rand() % (N-1)]=father[i];
			}
			else
			{
				son[i=rand() % (N-1)]=mother[i];
			}
		}
}

void selection(char *father, char *mother,char *res,char *son)
{
	if(calcfitness(son,res)<calcfitness(father,res))
	{
		strcpy(father,son);
	}
	else
	{
		if(calcfitness(son,res)<calcfitness(mother,res))
			{
				strcpy(mother,son);
			}
	}
}

void crossover(char *father,char *mother,char *son)
{
	int i=0,a=0,b=0;
	a=rand() % (N-13);
	b=a;
	
	if(rand() % 3==0)
		{
			for(i=a;i>0;i--)
				son[i]=father[i];
		}
	else
	{
		if(rand() % 3 == 1)
		{
			for(i=a;i>0;i--)
				son[i]=mother[i];
		}
		else
		{
			if(rand() % 3 == 2)
				{
					for(i=(b+1);i<N;i++)
						son[i]=mother[i];
				}
			else
				for(i=(b+1);i<N;i++)
						son[i]=father[i];
		}
	}
}
