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

||Constant|Opcode|Operand 1|Operand 2|
|-|--------|------|---------|---------|
|__Instruction indices__|15|14-12|11-6|5-0|

## Example instructions
<!-- 
`addi 4, 6`
- `addi`: `000`
- `4`: `000100`
- `6`: `000110`

```
ld x^3+x^2+1
0 100 001000 000110
0100 0010 0000 0110

In hexadecimal:
0x4206


gen x^3+x^2+1
0 111 000110 000110
0111 0001 1000 0110

In hexadecimal:
0x7186


loop 8
0 110 000000 001000
0110 0000 0000 1000

In hexadecimal:
0x6008


add 4, 6
0 000 000100 000110

0000 0001 0000 0110

In hexadecimal:
0x0106


mul 4, 6
0 001 000100 000110

0001 0001 0000 0110

In hexadecimal:
0x1106


div 2, 5
0 010 000010 000101

0010 0000 1000 0101

In hexadecimal:
0x2085

```
 -->


## Example instructions

`addi 4, 6`
- `addi`: `000`
- `4`: `000100`
- `6`: `000110`

```
init x^3+x^2+1
110 000000110
1100 0000 0110

In hexadecimal:
0xC06


gen x^3+x^2+1
111 000000110
1110 0000 0110

In hexadecimal:
0xE06


ld 4
100 000000100
1000 0000 0011

In hexadecimal:
0x803

add 4
000 000000100
0000 0000 0100

In hexadecimal:
0x004
```
