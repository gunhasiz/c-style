## Coding rules for C programming development

This document described coding rules for C development used by Krzysztof Oflus in his projects.

# General rules

Down below are listed most important rules that can be used for best and clearest code.

- Use `C99` or `C11` standard
- Use __ONLY__ English names/text for functions, variables, comments
- Within project, non-obvious operations describe the code with proper comment
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
- Always use `const` for pointer if function should not modify memory pointed to by `pointer`
- Never use *Variable Length Array*. Use dynamic memory allocation with `malloc`, `calloc` and `free`
- Avoid usage of `alloc.h` library with `alloc` and `alloca` memory allocation
- Use *lowercase* characters for local variables and *uppercase* for global variables
- Use *undescore* for variable containing multiple names, eg. `multi_name_variable`
- Always use `<>` for C Standard Library include files
- Always use `""` for custom libraries
- Always respect code style that is already used in project or library
