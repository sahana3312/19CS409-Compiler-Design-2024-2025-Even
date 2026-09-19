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
#include "exp3cd.tab.h"
#include <stdio.h>
%}

%%

[0-9]+                  { return NUMBER; }
[a-zA-Z][a-zA-Z0-9]*    { return ID; }

"+"     { return '+'; }
"-"     { return '-'; }
"*"     { return '*'; }
"/"     { return '/'; }
"("     { return '('; }
")"     { return ')'; }

[ \t]   ;          /* ignore spaces */
\n      return 0;

.       return yytext[0];

%%

int yywrap()
{
    return 1;
}
%{
#include <stdio.h>
#include <stdlib.h>

int yylex();
void yyerror(const char *s);

int valid = 1;
%}

%token NUMBER ID

%%

statement:
        expr
        {
            if(valid)
                printf("\nValid Arithmetic Expression\n");
        }
        ;

expr:
        expr '+' term
      | expr '-' term
      | term
      ;

term:
        term '*' factor
      | term '/' factor
      | factor
      ;

factor:
        '(' expr ')'
      | NUMBER
      | ID
      ;

%%

int main()
{
    printf("Enter Expression:\n");
    yyparse();
    return 0;
}

void yyerror(const char *s)
{
    valid = 0;
    printf("\nInvalid Arithmetic Expression\n");
}
```
## OUTPUT 

<img width="1337" height="517" alt="image" src="https://github.com/user-attachments/assets/5d694250-7077-4516-ae62-3f06b64544d1" />


## RESULT
The program to implement a symbol table is executed and the output is verified.
