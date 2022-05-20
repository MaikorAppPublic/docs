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

| Opcode | Operands           | Cycles | Size  | Byte order                                          |
|--------|--------------------|--------|-------|-----------------------------------------------------|
| 06     | Register, Register | 1      | 2     | lhs(1) rhs(1)                                       |
| 06     | Register, Indirect | 8      | 2 - 4 | lhs(1) rhs(1)  \<rhs offset>(1-2)                   |
| 06     | Indirect, Register | 8      | 2 - 4 | lhs(1) rhs(1) \<lhs offset>(1-2)                    |
| 06     | Indirect, Indirect | 12     | 2 - 6 | lhs(1) rhs(1) \<lhs offset>(1-2) \<rhs offset>(1-2) |

#### INC.W

| Opcode | Operands                     | Cycles | Size  | Byte order                                          |
|--------|------------------------------|--------|-------|-----------------------------------------------------|
| 07     | Ext. Register, Ext. Register | 1      | 2     | lhs(1) rhs(1)                                       |
| 07     | Ext. Register, Indirect      | 12     | 2 - 4 | lhs(1) rhs(1)  \<rhs offset>(1-2)                   |
| 07     | Indirect, Ext. Register      | 12     | 2 - 4 | lhs(1) rhs(1) \<lhs offset>(1-2)                    |
| 07     | Ext. Register, Ext. Register | 16     | 2 - 6 | lhs(1) rhs(1) \<lhs offset>(1-2) \<rhs offset>(1-2) |

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