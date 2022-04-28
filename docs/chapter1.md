## 1. Variable assignment and initialization  
### 1.1 Assignment
After a variable has been defined, you can give it a value using the `=` operator. This operation is called **copy assignment** (or simply **assignment**)

```C++
int x; // define the variable x
x = 5; // copy assignment of value 5 to variable x
```

### 1.2 Initialization  
Instead of first defining a variable and in a second step assigning a variable to it, we can create and assign a variable in a single step, in what's called **initialization**:  

```C++
int x = 5;
```

#### 1.2.1 Brace initialization  
Favor initialization using braces whenever possible, e.g.:  

```C++
int width { 5 }; 
```

### 1.3 Value initialization  
When a variable is initialized with empty braces, **value initialization** takes place. In most cases, **value initialization** will initialize the variable to zero (or empty, if it's more appropriate for a given type). In such cases where zeroing occurs, this is called **zero initialization**.  

```C++
int width {}; // zero initialization to value 0
```  

#### `{}` vs. `{ 0 }`  
Use an explicit value initialization if you're actually using that value:  


```C++
int x { 0 }; // explicit initialization to value 0
std::cout << x; // we're using that zero value
```  

Use value initialization if the value is temporary and will be replaced:  

```C++
int x {}; // value initialization
std::cin >> x; // we're immediately replacing that value
```

### 1.4 Initialize your variables  
Initialize your variables upon creation. You may eventually find cases where you want to ignore this advice for a specific reason (e.g. a performance critical section of code that uses a lot of variables), and that’s okay, as long the choice is made deliberately.
For more discussion on this topic, Bjarne Stroustrup (creator of C++) and Herb Sutter (C++ expert) make this recommendation themselves [here](https://github.com/isocpp/CppCoreGuidelines/blob/master/CppCoreGuidelines.md#es20-always-initialize-an-object).  

## 2. Introduction to iostream: cout, cin, and endl 
The **input/output library** (io library) is part of the C++ standard library that deals with basic input and output. We’ll use the functionality in this library to get input from the keyboard and output data to the console.  

### 2.1 std::cout  
The iostream library contains a few predefined variables for us to use. One of the most useful is std::cout, which allows us to send data to the console to be printed as text. cout stands for **“character output”**:  

```C++
#include <iostream> // includes the iolibrary that defines the std::cout variable

int main()
{
    std::cout << "Hello world!"; // print Hello world! to console

    return 0;
}
```  

In this program, we have included iostream so that we have access to std::cout. Inside our main function, we use std::cout, along with the insertion operator (`<<`), to send the text Hello world! to the console to be printed.

*std::cout* can not only print text, it can also print numbers and variables values:  

```C++
#include <iostream> // for std::cout

int main()
{
    std::cout << 4; // print 4 to console
    
    int x{ 5 }; // define integer variable x, initialized with value 5
    std::cout << x; // print value of x (5) to console
    
    return 0;
}
```

The insertion operator (`<<`) can be used multiple times in a single statement to concatenate multiple pieces of output. For example:  

```C++
#include <iostream> // for std::cout

int main()
{
    int x{ 5 };
    std::cout << "x is equal to: " << x;
    return 0;
}
```

This program prints:  

```
x is equal to: 5
```  

## 2.2 std::endl and `\n`  
Separate output statements don’t result in separate lines of output on the console. For example: 

```C++
#include <iostream> // for std::cout

int main()
{
    std::cout << "Hi!";
    std::cout << "My name is Alex.";
    return 0;
}
```

Will print: 

```
Hi!My name is Alex.
```

If we want to print separate lines of output to the console, we need to tell the console when to move the cursor to the next line. One way to do that is to use *std::endl*:  

```C++
#include <iostream> // for std::cout and std::endl

int main()
{
    std::cout << "Hi!" << std::endl; // std::endl will cause the cursor to move to the next line of the console
    std::cout << "My name is Alex." << std::endl;

    return 0;
}
```  

### Usually we prefer `\n` over *std::endl*  
Using std::endl can be a bit inefficient, as it actually does two jobs: it moves the cursor to the next line, and it makes sure that the output shows up on the screen immediately (this is called flushing the output). When writing text to the console using std::cout, std::cout often flushes output anyway (and if it doesn’t, it usually doesn’t matter), so having std::endl perform a flush is rarely important.

Because of this, use of the ‘\n’ character is typically preferred instead. The ‘\n’ character moves the cursor to the next line, but doesn’t request a flush, so it will perform better in cases where a flush would not otherwise happen. The ‘\n’ character also tends to be easier to read since it’s both shorter and can be embedded into existing text.  

```C++
#include <iostream> // for std::cout

int main()
{
    int x{ 5 };
    std::cout << "x is equal to: " << x << '\n'; // Using '\n' standalone (note: single quotes needed)
    std::cout << "And that's all, folks!\n"; // Using '\n' embedded into a double-quoted piece of text (note: no single quotes when used this way)
    return 0;
}
```  

Prints: 

```
x is equal to: 5
And that's all, folks!
```  

## 2.3 std::cin  
*std::cin* is another predefined variable that is defined in the iostream library. Whereas *std::cout* prints data to the console using the insertion operator (`<<`), *std::cin* (which stands for **“character input”**) reads input from keyboard using the extraction operator (`>>`). The input must be stored in a variable to be used.  
```C++
#include <iostream>  // for std::cout and std::cin

int main()
{
    std::cout << "Enter a number: "; // ask user for a number

    int x{ }; // define variable x to hold user input (and zero-initialize it)
    std::cin >> x; // get number from keyboard and store it in variable x

    std::cout << "You entered " << x << '\n';
    return 0;
}  
```  

For example (I entered 10):  

```
Enter a number: 10
You entered 10
```  

