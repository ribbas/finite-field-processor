# Logisim Implementation of a Finite Field Processor

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

## Supported Instructions

|Instruction|Operation code|Description|
|-----------|--------------|-----------|
|`ldi`|`000`|Load immediate/element value into opand1|
|`add`|`001`|XOR values (e -> e)|
|`mul`|`010`|Mod add values (p -> e)|
|`div`|`011`|Mod subtract values (p -> e)|
|`ld`|`100`|Load memory value/polynomial into opand1|
|`init`|`101`|Initialize polynomial generator constants|
|`gen`|`110`|Generate polynomial terms|
|`rst`|`111`|Reset|

### Format

| |Opcode|Operand|
|-|------|-------|
|__Instruction indices__|12-9|8-0|

### Examples

Example input primitive polynomial: `x^3+x^2+1`

Convert `x^3+x^2+1` to its binary representation:

`000000110/0x006`

#### Initialize constants required to compute the values of the polynomial
```
init 6
101 000000110
1010 0000 0110

In hexadecimal:
0xA06
```

#### Generate all the values of the polynomial
```
gen 6
110 000000110
1100 0000 0110

In hexadecimal:
0xC06
```

#### Load immediate value 3 into operand 1
```
ldi 3
000 000000011
0000 0000 0011

In hexadecimal:
0x003
```

#### Load memory value 4 into operand 1
```
ld 4
100 000000100
1000 0000 0100

In hexadecimal:
0x804
```

#### Add immediate value 1 into operand 2 and perform addition
```
add 1
001 000000001
0010 0000 0001

In hexadecimal:
0x201
```

#### Add memory value 2 into operand 2 and perform multiplication
```
mul 2
010 000000010
0100 0000 0010

In hexadecimal:
0x402
```

#### Add memory value 3 into operand 2 and perform division
```
div 3
011 000000011
0110 0000 0011

In hexadecimal:
0x603
```
