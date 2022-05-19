# SWAP

Swap values in registers or values at memory addresses in pointers.

## Format 

`SWAP lhs, rhs`

## Variations

```
SWAP.B (RR) (RI) (IR) (II)
SWAP.W (EE) (EI) (IE) (II)
```

#### SWAP.B

| Opcode | Operands           | Cycles |
|--------|--------------------|--------|
| 06     | Register, Register | 1      |
| 06     | Register, Indirect | 8      |
| 06     | Indirect, Register | 8      |
| 06     | Indirect, Indirect | 12     |

#### INC.W

| Opcode | Operands                     | Cycles |
|--------|------------------------------|--------|
| 07     | Ext. Register, Ext. Register | 1      |
| 07     | Ext. Register, Indirect      | 12     |
| 07     | Indirect, Ext. Register      | 12     |
| 07     | Ext. Register, Ext. Register | 16     |

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
SWAP.B AL, AH    # Swap values in AL and AH
SWAP.W AX, BX    # Swap values in AX and BX
SWAP.B (AX), DH  # Swap values in DH and at memory address in AX
```