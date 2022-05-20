# INC

Increases value in register or value at memory address in pointer by 1.

## Format 

`INC value`

## Variations

```
INC.B (R) (I) (A)
INC.W (E) (I) (A)
```

#### INC.B

| Opcode | Operands | Cycles | Size  | Byte order            |
|--------|----------|--------|-------|-----------------------|
| 2C     | Register | 2      | 1     | reg(1)                |
| 2C     | Indirect | 6      | 1 - 3 | reg(1) \<offset>(1-2) |
| 2E     | Address  | 2      | 2     | addr(2)               |

#### INC.W

| Opcode | Operands      | Cycles | Size  | Byte order            |
|--------|---------------|--------|-------|-----------------------|
| 2D     | Ext. Register | 4      | 1     | reg(1)                |
| 2D     | Indirect      | 8      | 1 - 3 | reg(1) \<offset>(1-2) |
| 2F     | Address       | 4      | 2     | addr(2)               |

## Flags

No changes

## Code equivalent

```
value++
```

## Examples

```
INC.B AL      # Increase AL by 1
INC.B $6003   # Increase value at 6003 by 1
INC.B (AX)    # Increase value at address in AX by 1
INC.W AX      # Increase AX by 1
INC.W $6700   # Increase value at [6700,6701] by 1
```