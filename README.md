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
    - Get and put stream positioning
    - Buffers and Synchronization
  - Containers: **USE THEM!!!**
  - `<algorithm>`
  - `<random>`
  - Time: `<chrono>`
  - Attention: **DO NOT USE THOSE F\*\*KING C APIs**
  - `<optional>` (since C++17)
  - `<tuple>` and `<pair>`

## Examples

### Range-based For Loop
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
### Linker Error
* `a.c`
```c
void a();
void b();

int main() {
  a();
  b();
}
```
* `b.c`
```c
void b() {}
```
* `c.c`
```c
void b() {}

int main() { b(); }
```
1. Undefined Symbols(s)
```bash
cc a.c b.c
# Step1: Produce a.o
# Step2: Produce b.o
# Step3: Link a.o and b.o together. Error occurs.
```
Output:
```
Undefined symbols for architecture x86_64:
  "_a", referenced from:
      _main in a-dcab57.o
ld: symbol(s) not found for architecture x86_64
clang: error: linker command failed with exit code 1 (use -v to see invocation)
```
2. Duplicate Symbol(s)
```bash
cc b.c c.c
```
Output:
```
duplicate symbol '_b' in:
    /var/folders/tk/hqz0jxgn71v9l0zb32m0svxh0000gn/T/b-c78963.o
    /var/folders/tk/hqz0jxgn71v9l0zb32m0svxh0000gn/T/c-1a77b0.o
ld: 1 duplicate symbol for architecture x86_64
clang: error: linker command failed with exit code 1 (use -v to see invocation)
```
### Compile-time Error
1. Syntax Issues
```c++
int main(){return 0}
```
```
❯ c++ tmp.cc
tmp.cc:1:20: error: expected ';' after return statement
int main(){return 0}
                   ^
                   ;
1 error generated.
```
2. Template
```
template <typename T>
void f(T) {}

int main() {
  f<int>(1);
  f<1>(1);
}
```
```
❯ c++ tmp.cc
tmp.cc:6:3: error: no matching function for call to 'f'
  f<1>(1);
  ^~~~
tmp.cc:2:6: note: candidate template ignored: invalid
      explicitly-specified argument for template parameter 'T'
void f(T) {}
     ^
1 error generated.
```
3. \#error
```
int main() {
#error Mother Fucker
}
```
```
❯ c++ tmp.cc
tmp.cc:2:2: error: Mother Fucker
#error Mother Fucker
 ^
1 error generated.
```
### Flip All Bits Using `~`
```c++
#include <bitset>
#include <cstdlib>
#include <iostream>

auto main() -> int {
  auto bs = std::bitset<8>{0b10000000};  // Equal to: uint8_t v=0b10000000;

  for (size_t i = 1; i <= 8; i++) std::cout << (int)bs[8 - i];

  std::cout << std::endl;

  bs = ~bs;  // Equal to v=~v;

  for (size_t i = 1; i <= 8; i++) std::cout << (int)bs[8 - i];

  std::cout << std::endl;

  return EXIT_SUCCESS;
}
```
```
❯ c++ tmp.cc --std=c++17
❯ ./a.out
10000000
01111111
```

### Initialize Fields In Constructor
```c++
#include <iostream>

class B {
 private:
  const int b_;

 public:
  B(int b) : b_(b) {}
  auto Get() const -> int { return b_; }
};

class A {
 private:
  const B b_;

 public:
  A(int a) : b_(a) {}
  auto Get() const -> int { return b_.Get(); }
};

class C : private A {
 public:
  C(int c) : A(c) {}
  auto Get() const -> int { return A::Get(); }
};

auto main() -> int {
  C c(10);
  std::cout << c.Get() << std::endl;
  return EXIT_SUCCESS;
}
```
```
❯ c++ tmp.cc --std=c++17
❯ ./a.out
10
```
### Function Template
```c++
#include <cstdint>
#include <cstdlib>
#include <iostream>

template <typename T>  // T is the name of a type.
auto DoNothing(const T &ele) -> T {
  return ele;
}

template <size_t S = 0>  // S cannot be non-integer.
auto PrintS() -> void {
  std::cout << S << std::endl;
}

template <typename Type = int32_t>  // With default value `int32_t`
auto UseTypeInsideFunction(Type a) -> Type {
  Type tmp = a * 10;
  return tmp;
}

auto main() -> int {
  std::cout << DoNothing(0) << std::endl;
  std::cout << DoNothing(0.01f) << std::endl;
  PrintS<100>();
  PrintS();
  std::cout << UseTypeInsideFunction(100) << std::endl;
  std::cout << UseTypeInsideFunction(0.01) << std::endl;
  return EXIT_SUCCESS;
}
```
```
❯ c++ tmp.cc --std=c++17
❯ ./a.out
0
0.01
100
0
1000
0.1
```