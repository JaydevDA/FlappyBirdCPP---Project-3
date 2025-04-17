# Flappy Bird Console Game - Technical Documentation

## Table of Contents
1. Game Overview
2. Code Structure
3. applications of the functions
4. Game Logic
5. Controls
6. Limitations
7. Potential Improvements

## *Game-Overview* 🎮

This is a console-based clone of the classic mobile game Flappy Bird, built using C++ and Windows console functions. It simulates the original game’s basic mechanics: a bird flying through gaps between pipes, with increasing difficulty and score tracking. As time passes, the bird will keep falling down, so you have to press 'Space' to make the bird go up

### Objective🎯

- Control a bird (represented with ASCII characters).
- Avoid crashing into pipes.
- Earn points(+1) by successfully passing through pipe gaps.
- Game ends if the bird hits a pipe or the ground.

### Display💻

- When the program initiates, it displays the title of the game along with 3 options, in which you have to choose one --> start, instructions or quit.  
  - start --> Will initiate the game
  - instructions --> Will show the instructions to how to play/exit the game.
  - quit --> end the game.
  
  
 ![title screen image](https://github.com/user-attachments/assets/4423b243-dc7e-4769-8e19-69331a6bd941)
 

- The whole screen is divided into two sections, one is the console(play) screen, the other is the menu screen (where the score and control button is displayed).
  
  
 ![play screen image](https://github.com/user-attachments/assets/178be2de-e149-493d-b9b5-4d66dee2341b)
 
 
- When you press any key, the program will initiate and a bird will be drawn besides the left border of size(6x2) and 6 cells below the ceiling.

## *Code Structure* 👷🏻

- Include libraries ( also non- standard libraries like dos.h, windows.h and conio.h ).

```
#include<iostream>
#include<conio.h>
#include<dos.h>
#include<stdlib.h>
#include<string.h>
#include <windows.h>
#include <time.h>
```

- Define or declare Global Variables.

```
#define SCREEN_WIDTH 90
#define SCREEN_HEIGHT 26
#define WIN_WIDTH 70
#define MENU_WIDTH 20
#define GAP_SIZE 7
#define PIPE_DIF 45

using namespace std;
 
HANDLE console = GetStdHandle(STD_OUTPUT_HANDLE);
COORD CursorPosition;

int pipePos[3];
int gapPos[3];
int pipeFlag[3];
char bird[2][6] = { '/','-','-','o','\\',' ',
					'|','_','_','_',' ','>' };
int birdPos = 6;
int score = 0;
```

- Create functions.
  - void gotoxy(int x, int y)
  - void setcursor(bool visible, DWORD size)
  - void drawBorder()
  - void genPipe(int ind)
  - void erasePipe(int ind)
  - void drawBird()
  - void eraseBird()
  - int collision()
  - void debug() [Not necesssary]
  - void updateScore()
  - void instructions() [Not necessary]
  - void play()

- apply all the functions in int main().

## Applications of the Functions 📃

- void gotoxy(int x, int y)

```
void gotoxy(int x, int y)
{
	CursorPosition.X = x;
	CursorPosition.Y = y;
	SetConsoleCursorPosition(console, CursorPosition);
}
```

- Purpose:
   - Moves the console cursor to a specified (x, y) coordinate.

- How It Works:
  - Uses COORD CursorPosition and SetConsoleCursorPosition() to set the cursor position.

- Allows precise placement of text (like the bird or pipes) on the screen.



