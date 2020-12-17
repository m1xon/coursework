#include <iostream>
#include <conio.h>
#include <windows.h>
#include <ctime>
#include <stdlib.h>

using namespace std;

void mapmake(char**, int, int);

void MapClear(char** map, int mapY, int mapX) {
	for (int i = 0; i < mapY; i++) {
		for (int j = 0; j < mapX; j++) {
			if (map[i][j] == '.') {
				map[i][j] = ' ';
			}
		}
	}
}

void ShowMap(char** map, int height, int width) {
	for (int i = 0; i < height; i++) {
		for (int j = 0; j < width; j++) {
			cout << map[i][j];
		}
		cout << endl;
	}
	cout << endl;
}

void enemy_spawn(char** map, int enemyX, int enemyY) {
	bool enemy_spawned = false;\
	while (enemy_spawned != true) {
		if (map[enemyY][enemyX] != '#' && map[enemyY][enemyX] != '|' && map[enemyY][enemyY] != 'H') {
			enemy_spawned = true;
			map[enemyY][enemyX] = '0';
		}
		else {
			enemyX = rand() % 31, enemyY = rand() % 17;
		}
	}
}

void gameover(int score) {
	Sleep(1000);
	system("cls");
	cout << "GAME OVER!" << endl;
	cout << "Your SCORE: " << score;
}

void movements(char** map, int mapY, int mapX, int enemyX, int enemyY) {

	system("cls");
	int key = 0;
	int heroX = 3, heroY = 2, score = 0;
	map[heroY][heroX] = 'H';
	srand(static_cast<unsigned int>(time(0)));
	int direction;

	// enemy spawn

	enemy_spawn(map, enemyX, enemyY);

	// moves
	while (true) {
		ShowMap(map, mapY, mapX);
		if (score == 999) {
			system("cls");
			cout << "to unclock next location pay 300$ buck";
			MapClear(map, mapY, mapX);
			break;
		}
		//enemy moves
		cout << "SCORE: " << score << "/999";
		direction = rand() % 4;
		if (enemyY == heroY && enemyX == heroX) {
			gameover(score);
			map[enemyY][enemyX] = ' ';
			break;
		}
		if (direction == 0) {
			if (map[enemyY + 1][enemyX] == '0') {
				gameover(score);
				map[enemyY + 1][enemyX] = ' ';
				map[enemyY][enemyX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			else if (map[enemyY + 1][enemyX] != '#' && map[enemyY + 1][enemyX] != '|') {
				enemyY++;
				if (enemyY >= 0) {
					map[enemyY - 1][enemyX] = '.';
					map[enemyY][enemyX] = '0';
				}
				//Sleep(200);
			}
		}
		if (direction == 1) {
			if (map[enemyY - 1][enemyX] == '0') {
				gameover(score);
				map[enemyY - 1][enemyX] = ' ';
				map[enemyY][enemyX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			else if (map[enemyY - 1][enemyX] != '#' && map[enemyY - 1][enemyX] != '|') {
				enemyY--;
				if (enemyY >= 0) {
					map[enemyY + 1][enemyX] = '.';
					map[enemyY][enemyX] = '0';
				}
				//Sleep(200);
			}
		}
		if (direction == 2) {
			if (map[enemyY][enemyX + 1] == '0') {
				gameover(score);
				map[enemyY][enemyX + 1] = ' ';
				map[enemyY][enemyX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			else if (map[enemyY][enemyX + 1] != '#' && map[enemyY][enemyX + 1] != '|') {
				enemyX++;
				if (enemyX >= 0) {
					map[enemyY][enemyX - 1] = '.';
					map[enemyY][enemyX] = '0';
				}
				//Sleep(200);
			}
		}
		if (direction == 3) {
			if (map[enemyY][enemyX - 1] == '0') {
				gameover(score);
				map[enemyY][enemyX - 1] = ' ';
				map[enemyY][enemyX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			else if (map[enemyY][enemyX - 1] != '#' && map[enemyY][enemyX - 1] != '|') {
				enemyX--;
				if (enemyX >= 0) {
					map[enemyY][enemyX + 1] = '.';
					map[enemyY][enemyX] = '0';
				}
				//Sleep(200);
			}
		}

		// hero moves

		key = _getch();


		if (key == 115) {   // s
			if (heroY == enemyY && heroX == enemyX) {
				gameover(score);
				map[heroY ][heroX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			if (map[heroY + 1][heroX] == '0') {
				gameover(score);
				map[heroY + 1][heroX] = ' ';
				map[heroY][heroX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			else if (map[heroY + 1][heroX] != '#' && map[heroY + 1][heroX] != '|') {
				heroY++;
				if (map[heroY][heroX] == '.') {
					score++;
					map[heroY - 1][heroX] = ' ';
					map[heroY][heroX] = 'H';
				}
				if (heroY >= 0 && map[heroY - 1][heroX] != '0') {
					map[heroY - 1][heroX] = ' ';
					map[heroY][heroX] = 'H';
				}
				else if (map[heroY - 1][heroX] == '0') {
					gameover(score);
					map[heroY - 1][heroX] = ' ';
					map[heroY][heroX] = ' ';
					MapClear(map, mapY, mapX);
					break;
				}

				Sleep(100);
			}

		}

		if (key == 119) {               //w
			if (heroY == enemyY && heroX == enemyX) {
				gameover(score);
				map[heroY][heroX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			if (map[heroY - 1][heroX] == '0') {
				gameover(score);
				map[heroY - 1][heroX] = ' ';
				map[heroY][heroX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			else if (map[heroY - 1][heroX] != '#' && map[heroY - 1][heroX] != '|') {
				heroY--;
				if (map[heroY][heroX] == '.') {
					score++;
					map[heroY + 1][heroX] = ' ';
					map[heroY][heroX] = 'H';
				}
				if (heroY >= 0 && map[heroY + 1][heroX] != '0') {
					map[heroY + 1][heroX] = ' ';
					map[heroY][heroX] = 'H';
				}
				else if (map[heroY + 1][heroX] == '0') {
					gameover(score);
					map[heroY + 1][heroX] = ' ';
					map[heroY][heroX] = ' ';
					MapClear(map, mapY, mapX);
					break;
				}

				Sleep(100);
			}
		}

		if (key == 100) {              //d
			if (heroY == enemyY && heroX == enemyX) {
				gameover(score);
				map[heroY][heroX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			if (map[heroY][heroX + 1] == '0') {
				gameover(score);
				map[heroY][heroX + 1] = ' ';
				map[heroY][heroX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			else if (map[heroY][heroX + 1] != '#' && map[heroY][heroX + 1] != '|') {
				heroX++;
				if (map[heroY][heroX] == '.') {
					score++;
					map[heroY][heroX - 1] = ' ';
					map[heroY][heroX] = 'H';
				}
				if (heroX >= 0 && map[heroY][heroX - 1] != '0') {
					map[heroY][heroX - 1] = ' ';
					map[heroY][heroX] = 'H';
				}
				else if (map[heroY][heroX - 1] == '0') {
					gameover(score);
					map[heroY][heroX - 1] = ' ';
					map[heroY][heroX] = ' ';
					MapClear(map, mapY, mapX);
					break;
				}

				Sleep(20);
			}
		}

		if (key == 97) {                         //a
			if (heroY == enemyY && heroX == enemyX) {
				gameover(score);
				map[heroY][heroX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			if (map[heroY][heroX - 1] == '0') {
				gameover(score);
				map[heroY][heroX - 1] = ' ';
				map[heroY][heroX] = ' ';
				MapClear(map, mapY, mapX);
				break;
			}
			else if (map[heroY][heroX - 1] != '#' && map[heroY][heroX - 1] != '|') {
				heroX--;
				if (map[heroY][heroX] == '.') {
					score++;
					map[heroY][heroX + 1] = ' ';
					map[heroY][heroX] = 'H';
				}
				if (heroX >= 0 && map[heroY][heroX + 1] != '0') {
					map[heroY][heroX + 1] = ' ';
					map[heroY][heroX] = 'H';
				}
				else if (map[heroY][heroX + 1] == '0') {
					gameover(score);
					map[heroY][heroX + 1] = ' ';
					map[heroY][heroX] = ' ';
					MapClear(map, mapY, mapX);
					break;
				}

				Sleep(20);
			}
		}
		system("cls");
	}

}

int main() {

	srand((unsigned)time(NULL));
	int enemyX = rand() % 31, enemyY = rand() % 17;
	int  mapY = 21, mapX = 31;
	char** map = new char* [mapY];
	for (int i = 0; i < mapY; i++)
		map[i] = new char[mapX];

	mapmake(map, mapY, mapX);

	int ch;
	cout << "press any key to start the game" << endl;
	ch = _getch();

	while (ch != 27) {
		system("cls");
		cout << "\nStart new game?";
		cout << "\n 1 - yes" << "\n 2 - no" << "\nesc - exit";
		ch = _getch();
		if (ch == 49) {
			movements(map, mapY, mapX, enemyX, enemyY);
			Sleep(1000);
		}
		else if (ch == 50) {
			system("cls");
			cout << "Thanks for the game";
			break;
		}
	}
}

void mapmake(char** map, int height, int width) {
	int x(0);

	for (int i = 0; i < height; i++) { // Массив заполняется землей
		for (int j = 0; j < width; j++) {
			map[i][j] = ' ';
		}
	}
	for (int i = 0; i < height; i++) {  // верхняя и нижняя граница
		for (int j = 0; j < width; j++) {
			map[i][j] = '#';
		}
		i += height - 2;
	}
	for (int j = 0; j < width; j++) { // правая и левая граница
		for (int i = 1; i < height - 1; i++) {
			map[i][j] = '|';
		}
		j += width - 2;
	}
	while (x < 5) {
		for (int i = (height / 2) - 1; i < 1 + rand() % 21; i++) { // wtynh
			for (int j = (width / 2) - 1; j < 1 + rand() % 31; j++) {

				map[i][j] = '#';
			}
		}

		for (int i = height - 4; i > rand() % 21; i--) {//нп
			for (int j = width - 4; j > rand() % 31; j--) {

				map[i][j] = '#';
			}
		}

		for (int i = height - 4; i > rand() % 21; i--) { // нл
			for (int j = 3; j < rand() % 31; j++) {
				map[i][j] = '#';
			}
		}

		for (int i = 3; i < rand() % 21; i++) { // вл
			for (int j = 3; j < rand() % 31; j++) {
				map[i][j] = '#';
			}
		}

		for (int i = 3; i < rand() % 21; i++) { // вп
			for (int j = width - 4; j > rand() % 31; j--) {
				map[i][j] = '#';
			}
		}
		x++;
	}
}
