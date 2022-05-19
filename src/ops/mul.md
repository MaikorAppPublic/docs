# MUL

Multiply values from destination and source together and store result in destination.

## Format 

`MUL dst, src`

## Variations

```
MUL.B (R, B) (R, R) (R, I) (I, R) (I, I) (A, I) (A, R) (A, A) (A, B) (I, A) (R, A) (I, B)
MUL.W (E, W) (E, E) (E, I) (I, E) (I, I) (A, I) (A, E) (A, A) (A, W) (I, A) (E, A) (I, W)
```

#### INC.B

| Opcode | Operands           | Cycles |
|--------|--------------------|--------|
| 82     | Register, Byte     | 2      |
| 80     | Register, Register | 3      |
| 80     | Register, Indirect | 5      |
| 80     | Indirect, Register | 7      |
| 80     | Indirect, Indirect | 9      |
| 86     | Address, Indirect  | 5      |
| 86     | Address, Register  | 3      |
| 8A     | Address, Address   | 3      |
| 88     | Address, Byte      | 2      |
| 84     | Indirect, Address  | 7      |
| 82     | Indirect, Byte     | 6      |
| 84     | Register, Address  | 3      |

#### INC.W

| Opcode | Operands                     | Cycles |
|--------|------------------------------|--------|
| 83     | Ext. Register, Word          | 4      |
| 81     | Ext. Register, Ext. Register | 6      |
| 81     | Ext. Register, Indirect      | 8      |
| 81     | Indirect, Ext. Register      | 10     |
| 81     | Indirect, Indirect           | 12     |
| 87     | Address, Indirect            | 8      |
| 87     | Address, Ext. Register       | 6      |
| 8B     | Address, Address             | 6      |
| 89     | Address, Word                | 4      |
| 85     | Indirect, Address            | 10     |
| 83     | Indirect, Word               | 8      |
| 85     | Ext. Register, Address       | 6      |

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
result = lhs * rhs
```

## Examples

```
MUL.B AL, 5       # Store result of AL * 5 in AL
MUL.W (BX), $500  # Store the result of multiplying the values at the address in BX and at 500 at the address stored in BX 
```