# DIT1253-2
Programming assignment 2. DEADLINE 25-10-2019 (FRIDAY)

#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
#include<iostream>
#include<time.h>
#include<chrono>//WARNING!! DOES NOT WORK ON VISUAL STUDIO 2010!!
#include<thread>
#include<iomanip>
using namespace std;

//All definitions go here:
float q2, subt, v1, v2, v3, v31, v4, v41;//Option 2
float dist, dcost;//Option 3
char mem;
char ta;
int option, pc, quan;
int mcount =1;//Loop counter

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
	while (mcount < 255)
	{
		printf("Enter product code, followed by quantity:\nProduct Code: ");
		cin >> pc;
		switch (pc)
		{
			case 101:
				cout << "Quantity: ";
				cin >> quan;
				v1 = quan * 100;
				cout << setprecision(2) << fixed << "Cost is " << v1 <<"\n";
				break;
			case 202:
				cout << "Quantity: ";
				cin >> quan;
				v2 = quan * 350;
				cout << setprecision(2) << fixed << "Cost is " << v2 << "\n";
				break;
			case 303:
				cout << "Quantity: ";
				cin >> quan;
				v3 = quan * 500;
				v31 = v3 * 0.8;
				cout << setprecision(2) << fixed << "Cost is " << v31 << "\n";
				break;
			case 404:
				cout << "Quantity: ";
				cin >> quan;
				v4 = quan * 850;
				v41 = v4 * 0.75;
				cout << setprecision (2) << fixed << "Cost is " << v41 << "\n";
				break;
			default:
				printf("Error\n%d is a non-existent product!\n", pc);
				break;
		}
		printf("Anymore items to add? (Y/N)\n");
		cin >> ta;
		switch (ta)
		{
			case 'Y':
				break;
			case 'N':
				subt = v1 + v2 + v31 + v41;
				cout <<setprecision (2) << fixed << "Subtotal is RM" << subt << "\n";
				system("pause");
				return 0;
				break;
		}
	}
		system("pause");
		return 0;
}

int dccal()//Option 3
{
	cout << "First 30KM=RM50\nAdditional RM3.00 per KM for every subsequent KM\n";
	cout << "Delivery beyond 100KM from the mall is not available\nDistance(KM):";
	cin >> dist;
	if (dist <= 30)
	{
		cout << "Delivery charge is RM50.00\n";
	}
	else if (dist > 30 && dist <= 100)
	{
		dcost = 50 + ((dist - 30) * 3);
		cout << "Delivery charge is RM" << dcost << "\n";
	}
	else
	{
		cout << "Delivery beyond 100KM not available\n";
	}
	system("pause");
	return 0;
}

int tcalc()//Option 4
{
	cout << "WIP\n";
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
	cin >> mem;
	
	while (mcount < 255)
	{
		printf("Select Options:\n");
		printf("1) Product & Price Details\n2) Price Calculator\n3) Delivery Charge Calculator\n");
		printf("4) Total Pay Amount Calculator\n5) Exit\nOption: ");
		cin >> option;
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
			break;
		case 5:
			printf("Exiting\n");
			return 0;
			break;
		default:
			printf("Error\n");
			system("pause");
		}
		printf("You selected option %d\n", option);
	}

}

//By Group Rendang
//Chiew Kar Heng
//Matthew Kong
//Low Cheng An
//Steven Soh
//DO NOT COPY!!
