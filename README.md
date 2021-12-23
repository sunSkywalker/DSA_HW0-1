#include <iostream>
#include <windows.h>
#include <conio.h>
#include <unistd.h>
using namespace std;

char map[10][20] = {"@@@@@@@@@@@@@@@@@@@",
                    "@      =          @",
					"@                 @",
					"@                 @",
					"@           =     @",
					"@                 @",
					"@                 @",
					"@                 @",                   
					"@                 @",				   				   
					"@@@@@@@@@@@@@@@@@@@"};

bool rungame = true;



int main()
{
	int x = 7;
	int y = 1;
	
	int xx = 12;
	int yy = 4;
	
	while(rungame == true)
	{
		system("cls");
		for(int i = 0; i < 10; i++)
		{
			for(int j = 0; j < 20; j++)
				cout << map[i][j];
			cout << endl;
		}
		

		if(map[y + 1][x] == ' ')
		{
			map[y][x] = ' ';
			y++;
			map[y][x] = '=';
		}
		else if(map[y + 1][x] == '@')
			map[y][x] = ' ';



		if(map[yy + 1][xx] == ' ')
		{
			map[yy][xx] = ' ';
			yy++;
			map[yy][xx] = '=';
		}
		else if(map[yy + 1][xx] == '@')
			map[yy][xx] = ' ';
		
		
		Sleep(250);

	}
	
	
	return 0;
}	
