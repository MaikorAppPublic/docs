# DEC

Decreases value in register or value at memory address in pointer by 1.

## Format 

`DEC value`

## Variations

```
DEC.B (R) (I) (A)
DEC.W (E) (I) (A)
```

#### DEC.B

| Opcode | Operands | Cycles |
|--------|----------|--------|
| 2C     | Register | 2      |
| 2C     | Indirect | 6      |
| 2E     | Address  | 2      |

#### DEC.W

| Opcode | Operands      | Cycles |
|--------|---------------|--------|
| 2D     | Ext. Register | 4      |
| 2D     | Indirect      | 8      |
| 2F     | Address       | 4      |

## Flags

No changes

## Code equivalent

```
value++
```

## Examples

```
DEC.B AL      # Decrease AL by 1
DEC.B $6003   # Decrease value at 6003 by 1
DEC.B (AX)    # Decrease value at address in AX by 1
DEC.W AX      # Decrease AX by 1
DEC.W $6700   # Decrease value at [6700,6701] by 1
```