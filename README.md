# Coding rules for C programming development

This document described coding rules for C development used by Krzysztof Oflus in his projects.

## General Rules

Down below are listed most important rules that can be used for best and clearest code.

### Main Rules

- Use `C11` standard
- Use __ONLY__ English names/text for functions, variables, comments
- Within project, non-obvious operations describe with proper comment
- Name the variables so that someone else can understand what it is needed for
- Don't use tabs, use 4 spaces insted for one indent level
- Use `1` space between keyword and opening bracket
- Don't use space between function name and opening bracket
```c
int a = 1;              // Correct
int function(int a);    // Correct
/*------------------------------*/
int a=1;                // Wrong
int function (int a);   // Wrong
```
- Opening bracket for functions and keywords is always on the same line
```c
for (int i = 0;i < 3;i++) {     // Correct
}
if (var < 2) {                  // Correct
}
/*--------------------------------------*/
for (int i = 0;i < 3;i++){     // Wrong
}
if (var < 2)                   // Wrong
{
}
```
- Single instruction below `if`, `while`, `for` should be indented with 4 spaces
```c
for (int i = 0;i < 3;i++)       // Correct
    a = a + c;
if (var < 2)                    // Correct
    var = 30;
/*--------------------------------------*/
for (int i = 0;i < 3;i++) {     // Wrong
    a = a + c;
}
if (var < 2)                    // Wrong
{
    var = 30;
}
if (var > 2)                    // Wrong
var = 30;
```
- Use space before and after comparison and assignment operators (This rule does not apply for `for` loop)
```c
int var = 2 * 2;        // Correct
if (var == 4)           // Correct
/*------------------------------*/
int var=2* 2;           // Wrong
if (var==4)             // Wrong
```
- Use space in `for` loop after comparison and assignment operators but not before and after semicolon
```c
for (int i = 0;i < 10;i++)     // Correct
/*-------------------------------------*/
for (int i=0;i<10;i++)         // Wrong
for (int i = 0 ; i < 10 ; i++) // Wrong
```
- Use space after every comma
```c
function(1, var);       // Correct
/*------------------------------*/
function(1,var);        // Wrong
```
- Declare all variables, which are not initialized, of the same type in the same line
```c
int a, b, c;        // Correct
char d, e, f;       // Correct
char f;             // Wrong, variable already exist
```
- Declare all variables in order
    1. Custom structures and enumerations
    2. Numeric, alphanumeric, characters
    3. Single/Double floating point
- Declare variable within `for` loop
```c
for (int i = 3;i < 12;i++)      // Correct
int i;                          // Correct if you need variable later
for (i = 3;i < 12;i++)
    i = a + b;
if (i == 11) {
    // Some code here
}
/*--------------------------------------*/
int i;                          // Wrong if you don't use i variable later
for (i =3;i < 12;i++)
    i = a + b;
```
- Variables assignment in the same line is permitted
```c
int a = 1, b = 2, c = 3;    // Correct
```
- Avoid function calls when declaring variable
```c
int a, b;                   // Correct
b = function();
/*----------------------------------*/
int a, b = function();      // Wrong
```
- Use `stdbool.h` library if you need `true` or `false` comparision.
  Using `1` or `0` is also permitted.
```c
#include <stdbool.h>
bool flag = true;           // Correct
int i_flag = 1;             // Also correct
```
- Always use `size_t` for length or size variables
- Never use *Variable Length Array*. Use dynamic memory allocation with `malloc`, `calloc` and `free`
- If declaraing *pointer* then use asterix straight after data type
```c
int* pointer;       // Correct
int * pointer;      // Wrong
int *pointer;       // Wrong
```
- Use *lowercase* characters for local variables and *uppercase* for global variables
- Use *undescore* for variable containing multiple names, eg. `multi_name_variable`
- Always use `<>` for C Standard Library include files
- Always use `""` for custom libraries
- Always respect code style that is already used in project or library

### Comments Rules

- For single line comments always use `//`. For multi line always use `/* some comment*/`.
```c
// This single line comment is ok 
/* This single line comment is not ok */

// This multi line comment,
// is not ok
/*
 * This multi line comment,
 * is ok
 */
```
- For multi line comments us `space + *` for every line
```c
/*
 * This multi line comment,
 * is ok with space + asterix
 */

/*
* This multi line comment,
* is not ok with space + asterix
*/
```
- Use comments only in new lines. However if you need to comment something within code, then comment line after first 80 symbols in total (example below)
```c
int some_variable;                                                              // Comment
```

### Local Variables Rules

- Variables naming have a few cases which are:
    1. Variable name must be lowercase
    2. Variable with multi word name must be separated with underscore `_`
    3. Variable name must be adequate to its purpose
```c
int index;              // Correct
int data_base_index;    // Correct
/*------------------------------*/
char a1;                // Wrong
char a2;                // Wrong
double Floatingpoint;   // Wrong
double FLOATingpoint;   // Wrong
```
- Group variables together by *type*
```c
// All of this variables are correct
int index;
int credit_card_number;
char local_character;
char symbol;
char* address;
double addition_sum;
/*--------------------------------*/
// All of this variables are wrong
int index;
char local_character;
double addition_sum;
int credit_card_number;
char* address;
char symbol;
```
- You may declare new variables inside next indent level
```c
int flag = 2;
if (flag == 2) {
    int new_flag;
    new_flag == ++flag;
}
```
- Declare pointer variables with asterix aligned to type
```c
char* pointer;      // Correct
/*-----------------------------*/
char *pointer;      // Wrong
char * pointer;     // also wrong
```
- Declaring multiple pointers within same line is permitted

### Global Variables Rules

- Variables naming have a few cases which are:
    1. Variable name must be uppercase
    2. Variable with multi word name must be separated with underscore `_`
    3. Variable name must be adequate to its purpose
```c
int Flag;              // Correct
int Main_Counter;      // Correct
char List[];           // Correct
/*------------------------------*/
char a1;                // Wrong
char A2;                // Wrong
double Floatingpoint;   // Wrong
double FLOATingpoint;   // Wrong
```
- Avoid global pointers
- Use Global variables __ONLY__ if necessery

### Functions Rules

- Every function must be included with *function prototype*
```c
void function();

int main() {
    // Some code here
    return 0;
}

void function(){
    // Function logic here
}
```
- Functions naming have a few cases which are:
    1. Function name must be lowercase
    2. Function with multi word name must be separated with underscore `_`
    3. Function name must be adequate to its logic
```c
void bubble_sort();     // Correct
void bubblesort();      // Wrong
void BubbleSort();      // Wrong
```
- Align all function prototypes for cleaner code
- Function implementation must include type and optional other keywords in the same line as function name
```c
int function(void) {        // Correct
    return 1;
}

int
function(void) {            // Wrong
    return 1;
}
```
- Function with no parameters must include void within brackets
```c
int function (void) {       // Correct
    return 1;
}

int function () {            // Wrong
    return 1;
}
```
- Functions which returns a pointer, must have asterix character after last function type keyword
```c
int* function () {          // Correct
    return *p;
}

int * function () {         // Wrong
    return *p;
}

int *function () {          // Wrong
    return *p;
}
```
