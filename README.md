# Note: C++ Language In My Eyes

## First, You Should Know About ......
  - Compiler and Linker
  - Base
  - Memory Layout
## Basics of C++
  - Structure of a program
  - Variables and types
    - Identifiers
    - Fundamental data types
    - Declaration of variables
    - Type deduction: `auto` and `decltype`
    - `std::string`
  - Constants
    - Literals
      - Attention: **Character and string literals**
      - Attention: **nullptr**
    - Typed constant expressions
    - Preprocessor definitions (`#define`)
  - Operators
    - Assignment operator (`=`)
    - Arithmetic operators ( `+`,` -`, `*`, `/`,`%`)
    - Compound assignment (`+=`, `-=`, `*=`, `/=`,`%=`, `>>=`, `<<=`, `&=`,`^=`, `|=`)
    - Increment and decrement (`++`,`--`)
      - Attention: **Undefined behaviours like `i=i++`**
    - Relational and comparison operators ( `==`, `!=`, `>`, `<`, `>=`, `<=` )
    - Logical operators (`!`, `&&`, `||` )
    - Conditional ternary operator ( `?:` )
    - Comma operator ( `,` )
    - Bitwise operators ( `&`, `|`, `^`, `~`, `<<`, `>>` )
    - Explicit type casting operator
    - `sizeof`
    - `typeid`
    - Precedence of operators
  - Basic Input/Output 
    - Standard output (std::cout)
    - Standard input (std::cin)
    - `std::cin` and strings
    - `std::stringstream`
## Program Structure
  - Control Structure
    - Selection statements: `if` and `else`
    - Iteration statements (loops)
      - Attention: **Range-based for loop**
      - Jump statements
        - `break` and `continue`
        - `goto` and Labels
      - Another selection statement: `switch`.
  - Functions
    - Functions with no type. The use of `void`
    - The return value of `main`
    - Arguments passed by value and by reference
    - Efficiency considerations and const references
    - Inline functions
    - Default values in parameters
    - Declaring functions
    - Recursivity
  - Overloads and Templates
    - Overloaded functions
      - Attention: **How to overload operator `<<` and `>>` for classes**
    - Function templates
    - Non-type template arguments
    - Template Dark Magic (f\*\*k)
  - Name Visibility
    - Scopes
    - Namespace
      - Namespace aliasing
    - `using`
    - The `std` namespace
    - Storage classes
      - Static
      - Automatic
      - Dynamic (**Deprecated since c++11**)
- Compound data types
  - Arrays
    - Memory Layout
    - Initializing arrays
    - Accessing the values of an array
    - Multidimensional arrays
    - Arrays as parameters
    - **Please use `std::array` instead**
  - Character Sequences (aka "string")
    - Memory Layout
    - Initialization of null-terminated character sequences
    - Strings and null-terminated character sequences
    - `std::string` and `std::string_view`
  - Poiners
    - Address-of operator (`&`)
    - Dereference operator (`*`)
    - Declaring pointers
    - Pointer initialization 
    - Pointer arithmetics
    - Pointers and const
    - Pointers and string literals
    - Pointers to pointers
    - `void` pointers
    - Invalid pointers and null pointers
    - Pointers to functions
    - **Use `nullptr` Instead of `NULL`**
    - **Never Use Raw Pointers If Possible**
      - `std::shared_ptr`
      - `std::unique_ptr`
      - etc...
  - Dynamic Memory
    - Operators `new` and `new[]`
    - Operators `delete` and `delete[]`
    - Dynamic memory in C
      - Attention: **Do not Use These APIs If Possible**
      - `malloc`, `realloc`, `calloc`, `alloca`, `free`
      - and so on.....
  - Data Structures (`struct`)
    - Declaration
    - Access fields(and methods) of a `struct`
    - Pointers to structures
    - Nesting structures
  - Other Data Types
    - `union`
    - `enum`
    - `enum class`
## Classes
  - Basics(1)
    - Fields and Methods
    - Constructors
    - Overloading constructors
    - Uniform initialization
    - Member initialization in constructors
    - Classes defined with `struct` and `union`
    - Pointers to classes
  - Basics(2)
    - Overloading operators
    - The keyword `this`
    - Static members
    - Const member functions
    - Class templates
    - Template specialization
  - Special members
    - Default constructor
    - Destructor
    - Copy constructor
    - Copy assignment
    - Move constructor and assignment
    - Implicit members
  - Friendship and inheritance
    - Friend functions
    - Friend classes
    - Inheritance between classes
    - Multiple inheritance
    - What is inherited from the base class?
  - Polymorphism
    - Pointers to base class
    - Virtual members
    - Abstract base classes
  - `public`, `private` and `protected`
## Other language features  
  - Type conversions
    - Implicit conversion
    - Implicit conversions with classes
    - Keyword `explicit`
    - Type casting
    - `dynamic_cast`, `static_cast`, `reinterpret_cast` and `const_cast`
    - `typeid`
  - Exceptions
    - What the heck are exceptions? **ANYTHING**
    - `throw` and `catch`
    - Exception specification
    - Standard exceptions: **USE THEM!!!**
  - Move Semantics 
  - Preprocessor directives
    - Attention: **DO NOT USE THEM IF POSSIBLE**
    - macro definitions (`#define`, `#undef`)
    - Conditional inclusions (`#ifdef`, `#ifndef`, `#if`, `#endif`, `#else` and `#elif`)
    - Line control (`#line`)
    - Error directive (`#error`)
    - Source file inclusion (`#include`)
    - Pragma directive (`#pragma`)
    - Predefined macro names
  - `constexpr`
  - Closures and `std::function`
## C++ Standard Library
  - Input/Output with files
    - Open a file
    - Closing a file
    - Text files and binary files
    - Checking state flags
    - get and put stream positioning
    - Buffers and Synchronization
  - Containers: **USE THEM!!!**
  - `<algorithm>`
  - `<random>`
  - Time: `<chrono>`
  - Attention: **DO NOT USE THOSE F\*\*KING C APIs**
  - `<optional>` (since C++17)
  - `<tuple>` and `<pair>`

## Examples

### Range-based for loop
```c++
#include <iostream>
#include <vector>
// ...
std::vector vec{1,2,3};
for(const auto& ele: vec)
std::cout<<ele<<","<<std::endl;
// Will print:
// 1,2,3
```