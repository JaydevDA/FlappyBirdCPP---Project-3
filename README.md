# Flappy Bird Console Game - Technical Documentation

## Table of Contents
1. [Game Overview](##Game-Overview)
2. [Code Structure](##*Code-Structure*👷🏻)
3. [applications of the functions](#application_of_the_functions)
4. [Game Logic](#game-logic)
5. [Controls](#controls)
6. [Limitations](#limitations)
7. [Potential Improvements](#potential-improvements)

## *Game Overview*

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

## *Code Structure* 

- Include libraries ( also non- standard libraries like dos.h, windows.h and conio.h ).
- Define or declare Global Variables.
- Create functions.
- apply all the functions in int main().



