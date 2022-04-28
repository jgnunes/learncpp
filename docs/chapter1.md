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
