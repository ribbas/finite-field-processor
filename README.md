# gfau-logisim

## Requirements

|Module|Description|Importance|Difficulty|Accept|
|------|----------|------|------|------|
|is_primitive|Check if an input polynomial is irreducible|Optional|Very hard|N|
|poly_gen|Generate all 2^n terms of a polynomial in GF(n)|Optional|Medium|N|
|add|Add 2 terms|Basic|Easy|Y|
|mul|Multiply 2 terms|Basic|Medium|Y|
|div|Divide 2 terms|Basic|Medium|Y|
|log|Find the log of a term|Basic|Easy|Y|
|twos_comp|Generate the two's complement of an integer|Prerequisite|Medium|Y|
|indices|A priority encoder to find the n-th index|Prerequisite|Medium|Y|
|control_unit|Control unit of the ALU|Basic|Hard|Y|
|mem|Memory block(s) of the ALU|Basic|Hard|Y|
|mem_control|Memory interface of the ALU|Basic|Hard|Y|

## Instruction Format

|Term form|Operation code|
|---------|--------------|
|`element`|`0`|
|`polynomial`|`1`|

|ALU operation|Operation code|Description|
|-------------|--------------|-----------|
|`add`|`000`|XOR values (e -> p)|
|`mul`|`001`|Mod add values (e -> e)|
|`div`|`010`|Mod subtract values (e -> e)|
|`log`|`011`|Lookup value (e -> p)|
|`ld`|`100`|Load value into opand1|
|`rst`|`101`|Reset|
|`init`|`110`|Initialize polynomial generator constants|
|`gen`|`111`|Generate polynomial terms|

| |Opcode|Operand|
|-|------|-------|
|__Instruction indices__|12-9|8-0|

## Example instructions

|ALU operation|Operation code|Description|
|-------------|--------------|-----------|
|`log`|`000`|Lookup value (e -> p)|
|`add`|`001`|XOR values (e -> p)|
|`mul`|`010`|Mod add values (e -> e)|
|`div`|`011`|Mod subtract values (e -> e)|
|`ld`|`100`|Load value into opand1|
|`init`|`101`|Initialize polynomial generator constants|
|`gen`|`110`|Generate polynomial terms|
|`rst`|`111`|Reset|


```
init x^3+x^2+1
101 000000110
1010 0000 0110

In hexadecimal:
0xA06


gen x^3+x^2+1
110 000000110
1100 0000 0110

In hexadecimal:
0xC06


ld 4
100 000000100
1000 0000 0011

In hexadecimal:
0x803


add 4
001 000000100
0010 0000 0100

In hexadecimal:
0x204


mul 4
010 000000100
0100 0000 0100

In hexadecimal:
0x404


div 4
011 000000100
0110 0000 0100

In hexadecimal:
0x604
```
