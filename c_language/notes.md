# Features of C
- portability (przenoszalność)
- less lines of code
- procedural language
- middle (high and low) level language
- popular choide for system level apps
- C offers wide variety of built in functions, standard libraries and header files.

### What does mean middle level language? (System level features)
- direct access to memory through pointers
- Bit manipulation using bitwise operators
- writing assembly code within C code


# C code overwiev

    #include<stdio.h>
    int main()
    {
        printf("Hello World!);
        return 0;
    }

### Pre-processor directive
    #include...

Preprocessor job is to replace text (starting with #) with the actual content.
Preprocessor replaces before the compilation begins

### Source code and Expanded source code
Source code is what I wrote and expanded source code is code after preprocessor replacing.

### Compiler and Machine Code
Compiler gets the expanded source code and return machine code.

### Linker
stdio.h is a header file and consists only definitions of functions like printf. The body of functions declared in header file is in the <b> C Standard Library </b>
Linker maps the prototypes (declaration) mentioned by preprocessor to the actual codes written in the standard library. Linker simply maps, linker do not copy like preprocessor.

# Variables

Name of variable points to some memory location

Declaration of variable should be before the varaible usage. Declaration is the announcing the properties of variable to the compiler. Properties are
- size of the variable (data type)
- name of the variable

Definition: allocating memory to the variable

Most of the time declaration and definition will be done at the same time. It depend of the <b> modifiers </b> (WIP)

    int var;

Initialization
    
    int var = 3;

## Naming convention
1. Combined from letters and digits
2. Cannot start with digit
3. Can contains underscore but a lot of system variables starts with underscore
4. Case sensitive
5. Special characters are not allowed
6. Blanks and whitespaces are not allowed
7. Do not use keywords (if, else, ...)


# printf
First argument is string. Next arguments are optional and the type is not specified. It prints on the screen and return number of successfully printed characters.

    printf("%d %d", v1, v2);

- %d - decimal value
- %u - unsigned decimal value
- %ld - long decimal
- %lu - long unsinged
- %lld - long long
- %llu - unsigned long long
- %.16f - float with precision 16
- %.16lf - double (depends on compilator, f also works)
- %.16Lf - long double (depends on compilator, f also works)
- %s - string
- %10s - string with 10 characters (if string is shorter there will be whitespaces at the beginning)
- %o - integer in octal
- %x or %X- integer in hexadecimal (capital x - capital letters in the output)

# Fundamental Data Types

Example: 2 bytes (16 bits) 
- unsigned 0 to $2^n -1$
- signed $ - 2^{n-1}$ to $2^{n-1} -1$   <b>2's complements range</b>

## 2's compliement example on 8 bits

$-2^7$ $2^6$ $2^5$ $2^4$ $2^3$ $2^2$ $2^1$ $2^0$

# Asinging value

    int var = 052

This code will assing 52 in Octal so in decimal it is $5*8+2=42$

    int var = 0x12

It means 12 in hexadecimal so 18 in decimal.


## Long and short dependence
sizeof(short) <= sizeof(int) <= sizeof(long) <= sizeof(long long)

sizeof is unary operator, not a function

## Unsigned modifier
decided if variable can be signed or not

All declarations below are correct

    int i1;
    singed int i2;
    signed i3;
    unsigned i4;
    long i5;
    long int i6;
    long long i7;


## Limits

    #include<limits.h>

    int main()
    {
        int var1 = INT_MIN;
        int var2 = INT_MAX;
        int var3 = UINT_MAX;
        int v4 = SHRT_MIN;
        int v5 = SHRT_MIN;
        int v6 = USHRT_MAX; 
    }

## Overflow
in general: X_MAX + 1 = X_MIN

# Character data type
ASCII

    char name = 'a';
    char name2 = 65; // A

Size: 1 byte (8 bits but it uses only 7 bits)
Range unsigned: 0 to 255
Range signed: -128 to 127

Extended ASCII encoding scheme uses all 8 bits.

signed and unsigned has no effect in ASCII.

# Float, Double and Long Double
These types represents fractional or real numbers.

### Size:
- Float - 4 bytes
- Double - 8 bytes
- Long Double - 12 bytes

but these size's can be different depends on the machine.

### Representations:
- Float - IEEE754 Single Precision Floating Point
- Double - IEEE754 Double Precision Floating Point
- Long Double - Extended Precision Floating Point

### Fixed vs. Floating Point

Fixed: |sign|n integers|.|k fraction|

so we have fixed number of representation of integer and fraction part. 

Floating point representation
- |sign|signed exponent|mantissa|
- <b>Formula: </b> $ (0.M)*Base^{Expo} $

Example if Mantissa and Exp has one bit
- Minimum value: $ (-0.9)*10^{9} $
- Maximum value: $ (0.9)*10^{9} $

# Scopes of variables

Compiler first try to find a local variable, then it uses global if any local not found.

Global variables are initialized by default to zero (0)

# auto keyword

auto means Automatic. Variable is destroyed in the end of scope. So there is no sense to use auto in simple data types.

    auto int v1 = 5;
    int v2 = 5;

There is no difference between v1 and v2 variables.
So automatic variable won't waste any memory.

# extern keyword
extern is short name for external

    int var;

In the code above there is a declaration and definition. So we tell compiler this is a integer data type (declaration) and we ask compiler to allocate memory to this variable (definition).

    extern int var;

This simply means declaration only. So any memory is allocated yet.

It is used whe a particular file needs acces a variable from another file.

So I can have main.c

    extern var a;
    int main()
    {
        printf("%d", a);
    }

It won't work until I add second file with global

    int a = 5;

And Linker is the part with combine definiton of <b>a</b> with extern declaration. Linker throws an error if definition is not found.

You can write:

    extern int a;
    extern int a;
    extern int a;

It is allowed because multiple declarations is allowed but multiple definitions are not allowed.

In simply words: Extern says to Linker "Go outside my scope and you will find the definition"

    int a = 8;
    int main()
    {
        extern int a;
        printf("%d",a);
        return 0;
    }

If we initialized extern variable then we also define a variable;

    extern int a = 8;

# register modifier

    register int a;

Register keyword hints the compiler to store a variable in register memory. It is just a hint, decision is made by compiler.

# static modifier
static is used to initalize variable once and save (share) the value between functions calls.

static variable is visible only in current scope. We are not able to get this variable from another scope by extern.

Static variables are automatically initialized to 0.
Static variable should be initialized by constant value.

Static variable remains in memory even if it is declared within a block. Static variable can behave like global one only in file it is declared.

# Constants in C

Two ways to define a constant:
- using #define
- using const

### Using define

    #define NAME value

- It is also called macro. 
- <b>Preprocessor replace NAME with value</b>. 
- Avoid semicolon and the end.
- GOOD PRACTICE: Use Capital name.
- Whatever inside double quotes won't get replaced
- we can use macros like functions 

        #define add(x, y) x+y

        add(4, 3)
- multiple lines using \

        greater(x. y) if(x > y) \
                    printf("true"); \
                    else \
                    printf("false");

- first expansion then evaluation

        5 * add(4, 3)
        \\ 5 * 4 + 3
        \\ 20 + 3
        \\ 23

- Some predefined macros like $\_\_DATE\_\_$  and $\_\_TIME\_\_$ can print current date and time.  

### Using const keyword

simply means we cannot change the assigned value;

# scanf
Scan Formatted string

it is scanning string from user input and take some parts into variables.

    int var;
    scanf("%d", &var);

It is important to use & to give memory location of variable.

# & operator

& - addres of variable

# Memory Layout of C Program

-------------
Command line arguments and environment variables

---------

Stack

--------
### &darr;


### &uarr;

--------
Heap

--------
uninitialized data (bss)

-------
Initialized data

-------
Text/Code segment


## We have two memory segments:
1. Text/Code segment
2. Data segment
    - initialized
        - read only
        - read write
    - uninitialized (bss - Block started by Symbol)
        - read only
        - read write
    - Stack
    - Heap

Text/Code segment contains machine code of compiled program

Initalized data contains Global, extern, static, const global variables

Uninitalized data contains unitialized global, static, const global variables

# Operators in C

Arithmetic: +,  -,  *,  /,  %

*, /, and % is evaluate before + and -

Incremet/Decrement: ++, --

Relational: ==, !=, <=, >=, <, >

Logical: && , || , !

Bitwise: &, ^, |, ~, >>, <<

Assignment: =, +=, -=, *=, /=, %=, <<=, >>=, &=, ^=, |=

Others: ?: , &, *, sizeof(), ,

### Conditional operator (ternary ?:)

    res = cond ? 1 : 2;

### Comma operator

it is just a separator.

    int a=4,b=3;
    int c = (1,2,3,4,5,6,7,8);
    int d = 1,2,3;

Comma operator returns the rightmost operand in the expression and it simply evaluates the rest of the operands and finally reject them. So variable c has value 8.
This operator have the least precedence. So variable d has value 1. 


# lvalue and rvalue

lvalue (left value) means an object that has an identifiable location in memory (having an address). Has capability to hold a data.

rvalue (right value): object that has no identifiable location in memory


# Compilation proces overview

1. Lexical analysis done by lexical analyzer (scanner)
    - scans whole source program and when it finds the meaningful sequence of characters (lexemes) then it converts it into a <b>token</b>
    - it always matches <b>the longest</b> charaters sequence



