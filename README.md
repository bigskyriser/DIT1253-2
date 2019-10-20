# DIT1253-2
Programming assignment 2. DEADLINE 25-10-2019 (FRIDAY)

#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
#include<time.h>
#include<iostream>
#include<chrono>//WARNING!! DOES NOT WORK ON VISUAL STUDIO 2010!!
#include<thread>
using namespace std;

//All definitions (except arrays) go here:
float q2, pcost, v3, v4;//Option 2
float dist, dcost;//Option 3
float subt, gt, gp;//Option 4
char mem;
char ta;
int option, pc;
int c22 = 0;//Array counter
int mcount =1;//Loop counter

//Arrays go here:
int o2101[64], o2202[64], o2303[64], o2404[64];
float v1[64], v2[64], v31[64], v41[64];

int price()//Option 1
{
	printf("+--------------+---------------------+------------------+------------------+\n");
	printf("| Product Code | Product Description | Retail Price(RM) | Special Discount |\n");
	printf("+--------------+---------------------+------------------+------------------+\n");
	printf("|     101      |    Wall Scrapper    |      100.0       |        -         |\n");
	printf("|     202      |     Tiles Waxes     |      350.0       |        -         |\n");
	printf("|     303      |   Mud/Tar Remover   |      500.0       |   20%% Discount   |\n");
	printf("|     404      |      Dry Blower     |      850.0       |   25%% Discount   |\n");
	printf("+--------------+---------------------+------------------+------------------+\n");
	system("pause");
	return 0;
}

int pcalc()//Option 2
{
	for (c22 =1; c22 <64; c22++)
	{
		printf("Enter product code, followed by quantity:\nProduct Code: ");
		scanf_s("%d", &pc);
		switch (pc)
		{
			case 101:
				printf("Quantity: ");
				scanf_s("%d", &o2101[c22]);
				v1[c22] = o2101[c22] * 100;
				printf("Cost is: RM%.2f\n", v1[c22]);
				break;
			case 202:
				printf("Quantity: ");
				scanf_s("%d", &o2202[c22]);
				v2[c22] = o2202[c22] * 350;
				printf("Cost is RM%.2f\n", v2[c22]);
				break;
			case 303:
				printf("Quantity: ");
				scanf_s("%d", &o2303[c22]);
				v3 = o2303[c22] * 500;
				v31[c22] = v3 * 0.8;
				printf("Cost is RM%.2f\n", v31[c22]);
				break;
			case 404:
				printf("Quantity: ");
				scanf_s("%d", &o2404[c22]);
				v4 =o2404[c22]* 850;
				v41[c22] = v4 * 0.75;
				printf("Cost is RM%.2f\n", v41[c22]);
				break;
			default:
				printf("Error\n%d is a non-existent product!\n", pc);
		}
		printf("Anymore items to add? (Y/N)\n");
		scanf_s("%c", &ta);

		if (ta == 'Y')
		{
			;
		}
		else
		{
			break;
		}
	}
	for (c22 = 1; c22 < 64; c22++)
	{
		pcost += v1[c22] + v2[c22] + v31[c22] + v41[c22];
	}
	printf("Subtotal is RM%.2f\n", pcost);
	system("pause");
	return 0;
}

int dccal()//Option 3
{
	printf("First 30KM=RM50\nAdditional RM3.00 per KM for every subsequent KM\n");
	printf("Delivery beyond 100KM from the mall is not available\nDistance(KM):");
	scanf_s("%f", &dist);
	if (dist <= 30)
	{
		printf("Delivery charge is RM50.00\n");
		dcost = 50.00;
	}
	else if (dist > 30 && dist <= 100)
	{
		dcost = 50 + ((dist - 30) * 3);
		printf("Delivery charge is RM%.2f\n", dcost);
	}
	else
	{
		printf("Delivery beyond 100KM not available\n");
	}
	system("pause");
	return 0;
}

int tcalc()//Option 4
{
	subt = pcost + dcost;
	gt = subt * 0.1;
	gp = subt * 1.1;
	printf("+---------------+\n");
	printf("| Products(RM)  |%.2f\n", pcost);
	printf("| Delivery(RM)  |%.2f\n", dcost);
	printf("+---------------+\n");
	printf("| Subtotal(RM)  |%.2f\n", subt);
	printf("| 10%% Gov. Tax  |%.2f\n", gt);
	printf("|Grand Price(RM)|%.2f\n", gp);
	printf("+---------------+\n");
	if (mem == 'Y')
	{
		if (gp >= 800 && gp <= 1000)
		{
			gp *= 0.9;
			printf("\nMember Discount 10%%\n+---------------+\n");
			printf("|Grand Price(RM)|%.2f\n+---------------+\n", gp);
		}
		else if (gp > 1000)
		{
			gp *= 0.88;
			printf("\nMember Discount 12%%\n+---------------+\n");
			printf("|Grand Price(RM)|%.2f\n+---------------+\n", gp);
		}
		else
		{
			;
		}
	}
	else
	{ }
	system("pause");
	return 0;
}
int main()//Main Menu
{
	printf("Initialising...\n");
	using namespace std::this_thread;
	using namespace std::chrono;
	sleep_for(seconds(2));
	sleep_until(system_clock::now() + seconds(1));
	printf("\nReady!\nBestPrice Mall Point of Sales Program\nversion 1.0\n");
	printf("Welcome!\n");
	printf("_#####___#####__\n_#____#__#____#_\n_#____#__#____#_\n_#####___#####__\n");
	printf("_#____#__#______\n_#____#__#______\n_#####___#______\n");
	printf("BEST PRICE MALL\n");
	printf("Do you have a membership? (Y/N)\n");
	scanf_s("%c", &mem);
	
	while (mcount < 255)
	{
		printf("Select Options:\n");
		printf("1) Product & Price Details\n2) Price Calculator\n3) Delivery Charge Calculator\n");
		printf("4) Total Pay Amount Calculator\n5) Exit\nOption: ");
		scanf_s("%d", &option);
		switch (option)
		{
		case 1:
			printf("Product Listing\n");
			price();
			break;
		case 2:
			printf("Price Calculator\n");
			pcalc();
			break;
		case 3:
			printf("Delivery\n");
			dccal();
			break;
		case 4:
			printf("Total payment\n");
			tcalc();
			break;
		case 5:
			printf("Exiting\n");
			return 0;
			break;
		default:
			printf("Error\n");
			system("pause");
		}
	}

}

//By Group Rendang
//Chiew Kar Heng
//Matthew Kong
//Low Cheng An
//Steven Soh
//DO NOT COPY!!
