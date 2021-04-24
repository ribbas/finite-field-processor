# gfau-logisim

## Requirements

|Module|Description|Importance|Difficulty|Accept|
|------|----------|------|------|------|
|is_primitive|Check if an input polynomial is irreducible|Optional|Very hard|N|
|poly_gen|Generate all 2^n terms of a polynomial in GF(n)|Optional|Hard|Y|
|add|Add 2 terms|Basic|Easy|Y|
|mul|Multiply 2 terms|Basic|Medium|Y|
|div|Divide 2 terms|Basic|Medium|Y|
|log|Find the log of a term|Basic|Easy|N|
|twos_comp|Generate the two's complement of an integer|Prerequisite|Medium|N|
|indices|A priority encoder to find the n-th index|Prerequisite|Medium|Y|
|control_unit|Control unit of the ALU|Basic|Medium|Y|
|mem|Memory block(s) of the ALU|Basic|Hard|Y|
|mem_control|Memory interface of the ALU|Basic|Hard|Y|

## Instruction Format

|ALU operation|Operation code|Description|
|-------------|--------------|-----------|
|`ldi`|`000`|Load immediate/element value into opand1|
|`add`|`001`|XOR values (e -> p)|
|`mul`|`010`|Mod add values (e -> e)|
|`div`|`011`|Mod subtract values (e -> e)|
|`ld`|`100`|Load memory value/polynomial into opand1|
|`init`|`101`|Initialize polynomial generator constants|
|`gen`|`110`|Generate polynomial terms|
|`rst`|`111`|Reset|


| |Opcode|Operand|
|-|------|-------|
|__Instruction indices__|12-9|8-0|

## Example instructions

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
1000 0000 0100

In hexadecimal:
0x804


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
