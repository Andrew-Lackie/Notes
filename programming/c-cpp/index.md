# C/C++ 

## C++

### Libraries
- [iomanip](iomanip/index.md)
- [Ncurses](ncurses/index.md)

### Syntax

#### Basic Syntax/Reference
```cpp
#include <iostream>
using namespace std;

int main(){
	
	system("pause>0");
}
```
#### Output and Input 

```cpp
cin >> a; // user input assigned to a
cout << "Hello World!" << a; // prints string and a
```
#### Variables

```cpp
int a = 1 // assigning an integer 
float a; // initializing floating point number
char character = 'a'; // assigning char
bool a = true; // assigns a boolean value
double a; // assigns a double 
unsigned int a;

int intMax = INT_MAX;
cout << intMax << endl; // prints the maximum value

count << "Size of int is " << sizeof(int) << "bytes\n"; // prints the size of int in bytes
```

#### ASCII Table

```cpp
cout << (int)'a'; // casting operator: will tell the ascii value (a = 97 & A = 65)
cout << int('a'); 

cout << char(65); // will print the letter representation (A)
```

#### if/else

```cpp
int number;
cin >> number

if (number % 2 == 0)
{
	cout << "You have entered an even number."
}
else 
{
	cout << "You have entered an odd number."
		
}
```
#### System Commands

Using the `system()` function, you can run bash system commands.

```cpp
system("clear"); // will run clear and clear the terminal screen
```
#### Ternary Operator (?)

```cpp
double marks;
cin >> marks;
string result = (marks >= 40) ? "passed" : "failed"; // if marks >= 40 then result = "passed" 
						     // if marks <= 40 then result = "failed"

```

#### Switch/Case Statement

```cpp
char x;
cin >> x;

switch (x) {

case 'a' :
	cout << x; 
	break;
	
case 'b' :
	cout << x; 
	break;
	
default:
	cout << "Not a valid operation."
	break;
}
```

#### Loops

##### While Loops

```cpp
int x;
x = 10;
while (x >= 0) {

	cout << x << " is greater than 0";
	x--;
}
```
##### Do While

```cpp
int x = 0;
int y = 0;

do {
	cin >> a;
	if (a != x)
		y++;
} 

while (y < 3 && a != x);
```

##### For Loop

```cpp
int number;
cin >> number;

int factorial = 1;

for (int i = 1; i <= number; i++) {
	factorial = factorial * i;
}
```

#### Functions

##### Basic

```cpp
void function1(string str, int num); // declare function before main

void main() {
	cout << "This is the main function.";
	bool x = function("string", 0); // this invokes function 1, x = true
}

bool function1(string str, int num = 0) { // define function after main, and num defaults to 0

	cout << "This is a function that does not return anything."; 
	cout << "Here is a string." << str;
	cout << "Here is a number." << num;
	
	return true
}


```

##### Generic Functions and Templates

```cpp
template<typename T> // creates a template; typename can be replaced by class

void swap(T& a, T& b) { // T can be any data type
	T temp = a;
	a = b;
	b = temp;
}

void main() {
	int a = 0; b = 0;
	
	swap<int>(a, b); // T is now replaced by int
}

```

##### Recursion and Recursive Functions

Alternative to loops.

```cpp
int recursive _sum(int m, int n) {
	if (m == n) // must have to stop recursion or else stack overflow error
		return m;
	return m + recursive_sum(m + 1, n);
}

```

#### Classes

```cpp
// class

class vehicle() {
private: // encapsulated
	string key;
	
protected: // can be accessed by derived classes
	string symbol;
	
public: // public everywhere
	string make;
	string model;
	string color;
	int year;
	list<string> owners;
	
// constructor
	
	vehicle(string make, string model, string color, int year, list<string> owners) {
		Make = make;
		Model = model;
		Color = color;
		Year = year;
		Owners = owners;
	}
	
// method
	
	void GetInfo() {
		cout << "Make: " << Make << endl
		cout << "Model: " << Model << endl
		cout << "Color: " << Color << endl
		cout << "Year: " << Year << endl
		for (string owner : Owners) {
			cout << owner << endl;
		}
	}
	
	void key() {
		cout << "The key is: " << key << endl;
	}
}

int main() {

// method without constructor

	vehicle myCar;
	myCar.make = "Chevrolet";
	myCar.model = "Metro";
	myCar.color = "Black";
	myCar.year = 2000;
	myCar.owners = {"Andrew", "Ryan"};
	
	
// method with constructor

	vehicle myCar("Chevrolet", "Metro", "Black", 2000, {"Andrew", "Ryan"});
	
// invoking the method

	Mycar.GetInfo();
	
	return 0;
}
// Inheritance

class sportsCarVehicle:public vehicle { // creates class that can use vehicle classes methods
public:
	sportCarVehicle(string make, string model, string color, int year, list<string> owners):
	vehicle(make, model, color, year, owners) {

	}

}
```

#### Pointers

##### Basic Pointers
Pointers store an address instead of a variable.
```cpp
int main{
	int n = 5;
	cout << n << endl; // will print 5
	cout << &n << endl; // will print the physical address
	
	int * ptr = &n; // ptr is holding the address of n
	
	cout << ptr << endl; // will print out the address of n
	cout << *ptr << endl; // will print out the value of n (5)
	*ptr = 10; // will change the value stored at the address to 10
	cout << n << endl; // will now print 10
	
	return 0;
}
```

##### Void Pointers

```cpp
// function prints the value of the address stored (int)
void printNumber(int* numberPtr) { 
	cout << *numberPtr << endl;
}
// function prints the value of the address stored (any type)
void print(void* ptr, char type) { // type must match the type of ptr

	switch (type) {
	case 'i': cout << *((int*)ptr) << endl; break; // handle int* 
	case 'c': cout << *((char*)ptr) << endl; break; // handle char*
	}
	
}

int main() {
	int number = 5;
	char letter = 'a';
	printNumber(&number); // function inputs an address and outputs value
	print(&number, 'i'); // function inputs the address of number and outputs the value
	print(&letter, 'c'); // functions inputs the address of letter and outputs the value
	
	return 0;
}

```

##### Pointers and Arrays

```cpp
int main() {
	int numbers[5] = {2, 3, 5, 7, 9};
	cout << numbers << endl; // outputs the address of the first value in the array
	cout << &numbers[0] << endl; // same output as the example above
	
	// example
	
	// this loop will create an array with user input
	
	int values[5];
	for (int i = 0; i <= 4, i++) {
		cout << "Number: ";
		cin << values[i];
	}
	
	// this loop will print the same numbers
	
	for (int i = 0; i <= 4; i++) {
		cout << *(values + i);
	}
	return 0;
}

```

##### Return Multiple Values

```cpp
// this function returns the min number in an array
int getMin(int numbers[], int size) {
	int min = numbers[0];
	for (int i = 1; i < size; i++) {
		if (numbers[i] < min) {
			min = numbers[i];
		}
	}
	return min;
}

// this function returns the max number in an array
int getMax(int numbers[], int size) {
	int max = numbers[0];
	for (int i = 1; i < size; i++) {
		if (numbers[i] > max) {
			max = numbers[i];
		}
	}
	return max;
}
// this function combines the two above using pointers
void getMinAndMax(int numbers, int* min, int* max) {

	for (int i = 1; i < size; i++) {
		if (numbers[i] > *max) {
			*max = numbers[i];
		}
		if (numbers[i] < *min) {
			*min = numbers[i];
		}

	}
}

int main() {
	int numbers[5] = {5, 4, -2, 29, 6};
	cout << " Min is " << getMin(numbers, 5) << endl;
	cout << " Max is " << getMax(numbers, 5) << endl;
	
	int min = numbers[0];
	int max = numbers[0];
	getMinAndMax(numbers, 5, &min, &max);
	cout << "Min is " << min << endl;	
	cout << "Max is " << max << endl;	
	return 0;
}
```
