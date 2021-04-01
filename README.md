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

|ALU operation|Operation code|
|-------------|--------------|
|`add`|`00`|
|`mul`|`01`|
|`div`|`10`|
|`log`|`11`|

|Operation|Operation code|
|---------|--------------|
|`addp`|`000`|
|`mulp`|`001`|
|`divp`|`010`|
|`log`|`011`|
|`add`|`100`|
|`mul`|`101`|
|`div`|`110`|

|Operation|Operation code|
|---------|--------------|
|`addp`|`0000`|
|`mulp`|`0001`|
|`divp`|`0010`|
|`log`|`0011`|
|`add`|`0100`|
|`mul`|`0101`|
|`div`|`0110`|
|`gen`|`0111`|
|`beq`|`1000`|
|`noop`|`1111`|

||Constant|Opcode|Operand 1|Operand 2|
|-|--------|------|---------|---------|
|__Instruction indices__|15|14-12|11-6|5-0|

## Example instructions

`addi 4, 6`
- `addi`: `000`
- `4`: `000100`
- `6`: `000110`

```
addp 4, 6
0 000 000100 000110

0000 0001 0000 0110

In hexadecimal:
0x0106


mul 4, 6
0 101 000100 000110

0101 0001 0000 0110

In hexadecimal:
0x5106


div 2, 5
0 110 000010 000101

0110 0000 1000 0101

In hexadecimal:
0x6085

```
