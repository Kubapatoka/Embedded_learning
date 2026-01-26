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


