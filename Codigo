#include <stdio.h>
#include <windows.h>
#include <conio.h>

#define ARRIBA 72
#define IZQUIERDA 75
#define DERECHA 77
#define ABAJO 80

using namespace std;

void gotoxy (int x, int y)
{
	HANDLE hCon;
	hCon = GetStdHandle(STD_OUTPUT_HANDLE);
    COORD dwPos;
	dwPos.X =x;
	dwPos.Y =y;
	SetConsoleCursorPosition(hCon, dwPos);
}
void OcultarCursor()
{
	HANDLE hCon;
	hCon = GetStdHandle(STD_OUTPUT_HANDLE);
	CONSOLE_CURSOR_INFO cci;
	cci.dwSize = 100; // Tamaño del cursor
	cci.bVisible = FALSE; // Si es verdadero se muestra, si es falso se oculta
	SetConsoleCursorInfo(hCon,&cci);
}
void pintar_limites()
{
	for(int i = 2; i<78 ; i++)
	{
		gotoxy(i,3);printf("%c",205);
		gotoxy(i,33);printf("%c",205);
	}
	for(int i = 4; i<33 ; i++)
	{
		gotoxy(2,i);printf("%c",186);
		gotoxy(77,i);printf("%c",186);
	}
	gotoxy(2,3); printf("%c",201);
	gotoxy(2,33); printf("%c",200);
	gotoxy(77,3); printf("%c",187);
	gotoxy(77,33); printf("%c",188);
}
class NAVE
{
	int x,y;
	int corazones;
	int vidas;
public:
	NAVE(int _x, int _y, int _corazones, int _vidas): x(_x), y(_y),corazones(_corazones), vidas(_vidas){}
	void pintar();
	void borrar();
	void mover();
	void pintar_corazones();
	void morir();
};
void NAVE::pintar()
{
	gotoxy(x,y); printf("  %c",30);
	gotoxy(x,y+1); printf(" %c%c%c",40, 207, 41);
	gotoxy(x,y+2); printf("%c%c %c%c",30, 190, 190, 30);
}
void NAVE::borrar()
{
	gotoxy(x,y); printf("     ");
	gotoxy(x,y+1); printf("     ");
	gotoxy(x,y+2); printf("     ");
}
void NAVE::mover()
{
	if(_kbhit())
		{
			char tecla = _getch();
			borrar();
			if(tecla == IZQUIERDA && x>3)
				{
					x--;
				}
			if(tecla == DERECHA && x+6< 77)
				{
					x++;
				}
			if(tecla == ARRIBA && y>4)
				{
					y--;
				}
			if(tecla == ABAJO && y+3 < 33)
				{
					y++;
				}
			if(tecla == 'e')corazones--;
			pintar();
			pintar_corazones();
		}
}
void NAVE::pintar_corazones()
{
	gotoxy(50,2); printf("VIDAS %d",vidas);
	gotoxy(64,2);printf("Salud");
	gotoxy(70,2); printf("    ");
	for(int i =0 ; i < corazones; i++)
	{
		gotoxy(70+i,2); printf("%c",3);
	}

}
void NAVE::morir()
{
	if(corazones ==0)
	{
		borrar();
		gotoxy(x,y);   printf("   **   ");
		gotoxy(x,y+1); printf("  ****  ");
		gotoxy(x,y+2); printf("   **   ");
		Sleep(200);

		borrar();
		gotoxy(x,y);   printf(" *  **  *");
		gotoxy(x,y+1); printf("   ****   ");
		gotoxy(x,y+2); printf(" *  **  * ");
		Sleep(200);

		vidas--;
		corazones = 3;
		pintar_corazones();
		pintar();
	}
}
int main()
{
	OcultarCursor();
	pintar_limites();
	NAVE N(7,7,3,3);
	N.pintar();
	N.pintar_corazones();
	bool game_over =false;
	while(!game_over)
	{
		N.morir();
		N.mover();
		Sleep(30);
	}
  
	system("pause>null");
    return 0;
}
