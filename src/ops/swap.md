# SWAP

Swap values in registers or values at memory addresses in pointers.

## Format 

`SWAP lhs rhs`

## Variations

```
SWAP.B (RR) (RI) (IR) (II)
SWAP.W (EE) (EI) (IE) (II)
```

#### SWAP.B

|Operands|Cycles|
|--------|------|
|Register, Register|1|
|Register, Indirect|8|
|Indirect, Register|8|
|Indirect, Indirect|12|

#### INC.W

|Operands|Cycles|
|--------|------|
|Ext. Register, Ext. Register|1|
|Ext. Register, Indirect|12|
|Indirect, Ext. Register|12|
|Ext. Register, Ext. Register|16|

## Flags

No changes

## Code equivalent

```
temp = lhs
lhs = rhs
rhs = temp
```

## Examples

```
SWAP.B AL AH    # Swap values in AL and AH
SWAP.W AX BX    # Swap values in AX and BX
SWAP.B (AX) DH  # Swap values in DH and at memory address in AX
```