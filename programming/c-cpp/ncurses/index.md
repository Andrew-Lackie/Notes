# ncurses

**ncurses** (new curses) is a programming library providing an application programming interface (API) that allows the programmer to write text-based user interfaces in a terminal-independent manner. It is a toolkit for developing "GUI-like" application software that runs under a terminal emulator. It also optimizes screen changes, in order to reduce the latency experienced when using remote shells. 

## Basic Format

```cpp

#include <ncurses.h>

using namespace std;

int main(int argc, char** argv)
{
	// initializes the screen
	// sets up memory and clears the screen
	
	initscr();
	
	// everything ncurses between these two functions	
	
	endwin();
	// deallocates memory and ends ncurses
	
	
	return 0
}

```

## Compiling

```sh
g++ -lncurses filename.cpp -o filename
```
```sh
./filename
```
## Functions

### Basic Functions

```cpp
refresh(); // refreshes the screen to match what's in memory
```

```cpp
cbreak(); // This function allows ctrl_c to be used to exit the program
```

```cpp
raw(); // This function doesn't allow special characters (like ctrl_c) and will display it as raw text
```

```cpp
noecho(); // will not print out any keys pressed
```

```cpp
getch(); // waits for user input, returns int value of that key
```

```cpp
printw("Hello World"); // prints a string(const char*) to a window
```

```cpp
clear(); // clears the screen
```

### Moving Cursors

```cpp
move(y,x); // moves the cursor to the specified location
```

```cpp
int c = getch();
mvprintw(y, x, "%d", c); // moves the cursor and prints
```

### Windows

```cpp
WINDOW * win = newwin(height, width, start_y, start_x); // creates window
refresh(); // must refresh for the box to be displayed
```
```cpp
int a,b;
box(win, a, b); // creates a border around the window defined by the decimal value e.g., g = 103
wborder(win, left, right, top, bottom, tlc, trc, blc, brc); // more customizable border
```
```cpp
wprintw(win, "This is my box"); // prints string on the top left corner of the window
mvwprintw(win, 1, 1, "This is my box"); // prints string in the location specified in the window
```
### Attributes and Colors

#### Attributes

```cpp
int main(int argc, char** argv)
{
	/* NCURSES START */
	start_ncurses(true, true);
	
	// ATTRIBUTES
	
	/* 
	* A_NORMAL
	* A_STANDOUT
	* A_RESERVE
	* A_BLINK
	* A_DIM
	* A_BOLD
	* A_PROTECT
	* A_INVIS
	* A_ALTCHARSET
	* A_CHARTEXT 
	*/

	attron(ATTRIBUTE); // activated attribute
	
	attroff(ATTRIBUTE); // deactivates attribute
	
```
#### Colors

```cpp

	//COLORS
	
	if(!has_color()) // check to see if terminal supports color
	{
		printw("Terminal does not support color");
		getch();
		return -1; // error status
	}
		
	if(can_change_color()) // check to see if terminal can change color
	{
		printw("can change color");
	}
	start_color();
	
	init_pair(1, FOREGROUND, BACKGROUND); // initiate color pair
	init_pair(2, FOREGROUND, BACKGROUND); // initiate color pair
	
	init_color(COLOR_CYAN, 0-999, 0-999, 0-999); // change color
	
	attron(COLR_PAIR(1)); // start color
	
	attron(COLOR_PAIR(1)); // end color
	
	/*
	* COLOR_PAIR(N) 
	* COLOR_BLACK   0
	* COLOR_RED     1
	* COLOR_GREEN   2
	* COLOR_YELLOW  3
	* COLOR_BLUE    4
	* COLOR_MAGENTA 5
	* COLOR_CYAN    6
	* COLOR_WHITE   7
}
```
