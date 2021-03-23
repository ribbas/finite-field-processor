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

||Constant|Opcode|Operand 1|Operand 2|
|-|--------|------|---------|---------|
|__Instruction indices__|15|14-12|11-6|5-0|

## Example instruction

`addi 4, 6`
- `addi`: `000`
- `4`: `000100`
- `6`: `000110`

```
addi 4, 6
0 000 000100 000110

0000 0001 0000 0110

In hexadecimal:
0x0106
```
