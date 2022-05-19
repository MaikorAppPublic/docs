# SUB

Subtract source from destination and store result in destination.

## Format 

`SUB dst, src`

## Variations

```
SUB.B (R, B) (R, R) (R, I) (I, R) (I, I) (A, I) (A, R) (A, A) (A, B) (I, A) (R, A) (I, B)
SUB.W (E, W) (E, E) (E, I) (I, E) (I, I) (A, I) (A, E) (A, A) (A, W) (I, A) (E, A) (I, W)
```

#### INC.B

| Opcode | Operands           | Cycles |
|--------|--------------------|--------|
| 32     | Register, Byte     | 2      |
| 30     | Register, Register | 3      |
| 30     | Register, Indirect | 5      |
| 30     | Indirect, Register | 7      |
| 30     | Indirect, Indirect | 9      |
| 36     | Address, Indirect  | 5      |
| 36     | Address, Register  | 3      |
| 3A     | Address, Address   | 3      |
| 38     | Address, Byte      | 2      |
| 34     | Indirect, Address  | 7      |
| 32     | Indirect, Byte     | 6      |
| 34     | Register, Address  | 3      |

#### INC.W

| Opcode | Operands                     | Cycles |
|--------|------------------------------|--------|
| 33     | Ext. Register, Word          | 4      |
| 31     | Ext. Register, Ext. Register | 6      |
| 31     | Ext. Register, Indirect      | 8      |
| 31     | Indirect, Ext. Register      | 10     |
| 31     | Indirect, Indirect           | 12     |
| 37     | Address, Indirect            | 8      |
| 37     | Address, Ext. Register       | 6      |
| 3B     | Address, Address             | 6      |
| 39     | Address, Word                | 4      |
| 35     | Indirect, Address            | 10     |
| 33     | Indirect, Word               | 8      |
| 35     | Ext. Register, Address       | 6      |

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
result = lhs - rhs
```

## Examples

```
SUB.B AL, 5       # Store result of AL - 5 in AL
SUB.W (BX), $500  # Store the result of subtracting the value at 500 from the value at the address in BX and store the result at the address in BX 
```