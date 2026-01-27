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

# Fundamental Data Types

Example: 2 bytes (16 bits) 
- unsigned 0 to $2^n -1$
- signed $ - 2^{n-1}$ to $2^{n-1} -1$   <b>2's complements range</b>

## 2's compliement example on 8 bits

$-2^7$ $2^6$ $2^5$ $2^4$ $2^3$ $2^2$ $2^1$ $2^0$

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