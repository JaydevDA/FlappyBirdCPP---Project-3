# Flappy Bird Console Game - Technical Documentation

## Table of Contents
1. [Game Overview](#game-overview)
2. [Code Structure](#code-structure)
3. [Key Functions](#key-functions)
4. [Game Logic](#game-logic)
5. [Controls](#controls)
6. [Limitations](#limitations)
7. [Potential Improvements](#potential-improvements)

## *Game Overview*

This is a console-based clone of the classic mobile game Flappy Bird, built using C++ and Windows console functions. It simulates the original game’s basic mechanics: a bird flying through gaps between pipes, with increasing difficulty and score tracking.

### Objective🎯

- Control a bird (represented with ASCII characters).
- Avoid crashing into pipes.
- Earn points(+1) by successfully passing through pipe gaps.
- Game ends if the bird hits a pipe or the ground.

### Display💻

- When the program initiates, it displays the title of the game along with 3 options --> start, instructions and quit.
- ![title screen image](https://github.com/user-attachments/assets/4423b243-dc7e-4769-8e19-69331a6bd941)
- The whole screen is divided into two sections, one is the console(play) screen, the other is the menu screen (where the score
