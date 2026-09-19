# Ex. No : 1	
# IMPLEMENTATION OF SYMBOL TABLE 
## Register Number : 212225040356
## Name : SAHANA S
## Date : 18.07.2026

## AIM   
To write a C program to implement a symbol table.

## ALGORITHM
1.	Start the program.
2.	Get the input from the user with the terminating symbol ‘$’.
3.	Allocate memory for the variable by dynamic memory allocation function.
4.	If the next character of the symbol is an operator then only the memory is allocated.
5.	While reading, the input symbol is inserted into symbol table along with its memory address.
6.	The steps are repeated till ‘$’ is reached.
7.	To reach a variable, enter the variable to be searched and symbol table has been checked for corresponding variable, the variable along with its address is displayed as result.
8.	Stop the program. 

## PROGRAM
```
%{
#include <stdio.h>
#include <ctype.h>
%}

%%

"if"        { printf("Keyword: %s\n", yytext); }
"else"      { printf("Keyword: %s\n", yytext); }
"while"     { printf("Keyword: %s\n", yytext); }
"for"       { printf("Keyword: %s\n", yytext); }

[0-9]+      { printf("Number: %s\n", yytext); }
[a-zA-Z_][a-zA-Z0-9_]*   { printf("Identifier: %s\n", yytext); }

"=="|"="    { printf("Symbol: %s\n", yytext); }
"+"|"-"|"*"|"/" { printf("Symbol: %s\n", yytext); }

[ \t\n]     ;   // Ignore whitespace
.           { printf("Unknown: %s\n", yytext); }

%%

int main(int argc, char **argv) {
    yylex();
    return 0;
}

int yywrap() {
    return 1;
}
```
## OUTPUT 

<img width="682" height="665" alt="image" src="https://github.com/user-attachments/assets/bfee4e95-6c02-4008-b47c-16c88205c60c" />


## RESULT
The program to implement a symbol table is executed and the output is verified.
