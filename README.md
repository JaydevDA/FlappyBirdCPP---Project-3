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
  - _void gotoxy(int x, int y)_
  - _void setcursor(bool visible, DWORD size)_
  - _void drawBorder()_
  - _void genPipe(int ind)_
  - _void erasePipe(int ind)_
  - _void drawBird()_
  - _void eraseBird()_
  - _int collision()_
  - _void debug() [Not necesssary]_
  - _void updateScore()_
  - _void instructions() [Not necessary]_
  - _void play()_

- apply all the functions in int main().

## Applications of the Functions 📃

1. **void gotoxy(int x, int y)**

```cpp
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

2. **setcursor(bool visible, DWORD size)**

```cpp
void setcursor(bool visible, DWORD size) 
{
	if(size == 0)
		size = 20;	
	
	CONSOLE_CURSOR_INFO lpCursor;	
	lpCursor.bVisible = visible;
	lpCursor.dwSize = size;
	SetConsoleCursorInfo(console,&lpCursor);
}
```

- Purpose:
  - Controls the visibility and size of the blinking console cursor.

- Why It’s Used:
  - The game hides the cursor (visible = false) to prevent it from flickering or interfering with the game visuals.

- If size = 0, it defaults to 20 (but since the cursor is hidden, this doesn’t affect gameplay).  

3. **drawBorder()**

```cpp
void drawBorder(){ 
	
	for(int i=0; i<SCREEN_WIDTH; i++){
		gotoxy(i,0); cout<<"�";
		gotoxy(i,SCREEN_HEIGHT); cout<<"�";
	}
	
	for(int i=0; i<SCREEN_HEIGHT; i++){
		gotoxy(0,i); cout<<"�";
		gotoxy(SCREEN_WIDTH,i); cout<<"�";
	}
	for(int i=0; i<SCREEN_HEIGHT; i++){
		gotoxy(WIN_WIDTH,i); cout<<"�";
	}
}
```

- Purpose:
  - Draws a border around the game area to define the playable space.

- How It Works:
  - Uses gotoxy() and cout to draw lines around the edges.

- A vertical line at WIN_WIDTH (70) separates the game area from the score display.

4. **genPipe(int ind)**

```cpp
void genPipe(int ind){
	gapPos[ind] = 3 + rand()%14; 
}
```

- Purpose:
  - Randomly generates the vertical position of a pipe’s gap.

- How It Works:
  - gapPos[ind] = 3 + rand() % 14; ensures the gap is between rows 3 and 16.

This prevents impossible gaps (too high or too low).

- Example:
  - If rand() % 14 returns 7, then gapPos[0] = 10, meaning the gap starts at row 10.
 
5. **drawPipe(int ind)**

```cpp
void drawPipe(int ind){
	if( pipeFlag[ind] == true ){
		for(int i=0; i<gapPos[ind]; i++){ 
			gotoxy(WIN_WIDTH-pipePos[ind],i+1); cout<<"***"; 
		}
		for(int i=gapPos[ind]+GAP_SIZE; i<SCREEN_HEIGHT-1; i++){ 
			gotoxy(WIN_WIDTH-pipePos[ind],i+1); cout<<"***"; 
		}
	} 
}
```

- Purpose:
  - Draws a pipe (made of ***) at the specified index.

- How It Works:
  - If pipeFlag[ind] is true (active), it draws:

  - A top pipe from row 1 to gapPos[ind].

  - A bottom pipe from gapPos[ind] + GAP_SIZE to the bottom of the screen.  
  
The gap in between is where the bird must fly.










