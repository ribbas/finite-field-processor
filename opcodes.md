# Galois Field ALU Instructions

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
|`addi`|`000`|
|`muli`|`001`|
|`divi`|`010`|
|`log`|`011`|
|`add`|`100`|
|`mul`|`101`|
|`div`|`110`|

|Operation|Operation code|
|---------|--------------|
|`addi`|`0000`|
|`muli`|`0001`|
|`divi`|`0010`|
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
addi 4, 6
0 001 000100 000110

0001 0001 0000 0110

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
