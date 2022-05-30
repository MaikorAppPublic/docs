# DIV

> Divide

Divide destination by source and store result in destination.

## Format 

`DIV dst, src`

## Variations

```
DIV.B (R, B) (R, R) (R, I) (I, R) (I, I) (A, I) (A, R) (A, A) (A, B) (I, A) (R, A) (I, B)
DIV.W (E, W) (E, E) (E, I) (I, E) (I, I) (A, I) (A, E) (A, A) (A, W) (I, A) (E, A) (I, W)
```

#### INC.B

| Opcode | Operands           | Cycles |
|--------|--------------------|--------|
| 9A     | Register, Byte     | 2      |
| 98     | Register, Register | 3      |
| 98     | Register, Indirect | 5      |
| 98     | Indirect, Register | 7      |
| 98     | Indirect, Indirect | 9      |
| 9E     | Address, Indirect  | 5      |
| 9E     | Address, Register  | 3      |
| A2     | Address, Address   | 3      |
| A0     | Address, Byte      | 2      |
| 9C     | Indirect, Address  | 7      |
| 9A     | Indirect, Byte     | 6      |
| 9C     | Register, Address  | 3      |

#### INC.W

| Opcode | Operands                     | Cycles |
|--------|------------------------------|--------|
| 9B     | Ext. Register, Word          | 4      |
| 99     | Ext. Register, Ext. Register | 6      |
| 99     | Ext. Register, Indirect      | 8      |
| 99     | Indirect, Ext. Register      | 10     |
| 99     | Indirect, Indirect           | 12     |
| 9F     | Address, Indirect            | 8      |
| 9F     | Address, Ext. Register       | 6      |
| A3     | Address, Address             | 6      |
| A1     | Address, Word                | 4      |
| 9D     | Indirect, Address            | 10     |
| 9B     | Indirect, Word               | 8      |
| 9D     | Ext. Register, Address       | 6      |

## Flags

| Flag         | Update condition                                                           |
|--------------|----------------------------------------------------------------------------|
| Zero         | Set if result is 0, otherwise cleared                                      |
| Signed       | Matches first bit of result                                                |
| Carry        | Set if result is greater 255 for `.B` or 65535 for `.W`, otherwise cleared |
| Less than    | Always cleared                                                             |
| Greater than | Always cleared                                                             |
| Overflow     | Set if the dst and result first bit are different, otherwise cleared       |
| Interrupts   | -                                                                          |

## Code equivalent

```
result = lhs / rhs
```

## Examples

```
DIV.B AL, 5       # Store result of AL / 5 in AL
DIV.W (BX), $500  # Store the result of dividing the value at 500 from the value at the address in BX and store the result at the address in BX 
```