# Flappy Bird Console Game - Technical Documentation

## Table of Contents
1. [Game Overview](#game-overview)
2. [Code Structure](#code-structure)
3. [Key Functions](#key-functions)
4. [Game Logic](#game-logic)
5. [Controls](#controls)
6. [Limitations](#limitations)
7. [Potential Improvements](#potential-improvements)

## Game Overview
A console-based implementation of Flappy Bird using:
- Windows API for console manipulation
- ASCII art for graphics
- Simple collision detection
- Score tracking system

## Code Structure

### Global Variables
```
HANDLE console = GetStdHandle(STD_OUTPUT_HANDLE);
COORD CursorPosition;

int pipePos[3];       // Horizontal positions of pipes
int gapPos[3];        // Vertical positions of pipe gaps
int pipeFlag[3];      // Active status of pipes
char bird[2][6] = {   // ASCII art for the bird
    {'/','-','-','o','\\',' '},
    {'|','_','_','_',' ','>'}
};
int birdPos = 6;      // Vertical position of bird
int score = 0;        // Player score
```
