# Instructions

> Also called commands, operations and ops

## Arguments

> Also called args and params, operands

|Key|Name|Examples|
|---|---|---|
|`R`|Register|`AL`, `CH`|
|`E`|Extended Register|`BX`, `CX`|
|`I`|Indirect Register|`(AX)`, `(BX)`|
|`B`|Byte|`45`, `xF1`|
|`W`|Word|`451`, `x3A0`|
|`A`|Address|`$1102`,`$xFF12`|

### PPID

> Pre/Post Inc/Dec

PPID allowed you to increment decrement a register before or after using that register in an op.

Registers are changed by 1 and extended/indirect registers are changed by 2.

For example, with
```
CPY.W AX 1000
INC.B -(AX)
```
- `AX` is set to 1000
- `AX` is set to 998
- The value at `$998` is incremented 

and with
```
CPY.B AL 5
CPY.B AH AL-
```
- `AL` is set to 5
- `AH` is set to 5
- `AL` is set to 4

PPID works on any `R`, `E`, or `I` args in any instruction.


## List

|Name|Size variants|Args|Cycles|
|----|---|---|---|
|[INC](./ops/inc.md)|`B`, `W`|`(R)`, `(E)`, `(I)`, `(A)`|2-8|
|[SWAP](./ops/swap.md)|`B`, `W`|`(R,R)`, `(R,I)`, `(I,R)`, `(I,I)`, `(E,E)`, `(E,I)`, `(I,E)`|1-16|
|[ADD](./ops/add.md)|`B`, `W`|`(R,B)`, `(R,R)`, `(R,I)`, `(I,R)`, `(I,I)`, `(R,A)`, `(I,A)`, `(A,I)`, `(A,R)`, `(A,B)`, `(E,W)`, `(E,E)`, `(E,I)`, `(I,E)`, `(A,E)`, `(A,A)`, `(A,W)`, `(E,A)`, `(I,B)`, `(I,W)`|2-12|