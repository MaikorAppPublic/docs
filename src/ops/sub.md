# SUB

> Subtract

Subtract source from destination and store result in destination.

## Format 

`SUB dst, src`

## Variations

```
SUB.B (R, B) (R, R) (R, I) (I, R) (I, I) (A, I) (A, R) (A, A) (A, B) (I, A) (R, A) (I, B)
SUB.W (E, W) (E, E) (E, I) (I, E) (I, I) (A, I) (A, E) (A, A) (A, W) (I, A) (E, A) (I, W)
```

#### INC.B

| Opcode | Operands           | Cycles | Size  | Byte order                                  |
|--------|--------------------|--------|-------|---------------------------------------------|
| 32     | Register, Byte     | 2      | 2     | reg(1) byte(1)                              |
| 30     | Register, Register | 3      | 2     | reg(1) reg(1)                               |
| 30     | Register, Indirect | 5      | 2 - 4 | reg(1) reg(1) \<offset>(1-2)                |
| 30     | Indirect, Register | 7      | 2 - 4 | reg(1) reg(1) \<offset>(1-2)                |
| 30     | Indirect, Indirect | 9      | 2 - 6 | reg(1) reg(1) \<offset>(1-2) \<offset>(1-2) |
| 36     | Address, Indirect  | 5      | 3 - 5 | addr(2) reg(1) \<offset>(1-2)               |
| 36     | Address, Register  | 3      | 3     | addr(2) reg(1)                              |
| 3A     | Address, Address   | 3      | 4     | addr(2) addr(2)                             |
| 38     | Address, Byte      | 2      | 3     | addr(2) byte(1)                             |
| 34     | Indirect, Address  | 7      | 3-5   | reg(1) addr(2) \<offset>(1-2)               |
| 32     | Indirect, Byte     | 6      | 2-4   | reg(1) byte(1) \<offset>(1-2)               |
| 34     | Register, Address  | 3      | 3     | reg(1) addr(2)                              |

#### INC.W

| Opcode | Operands                     | Cycles | Size  | Byte order                                  |
|--------|------------------------------|--------|-------|---------------------------------------------|
| 33     | Ext. Register, Word          | 4      | 3     | reg(1) word(2)                              |
| 31     | Ext. Register, Ext. Register | 6      | 2     | reg(1) reg(1)                               |
| 31     | Ext. Register, Indirect      | 8      | 2 - 4 | reg(1) reg(1) \<offset>(1-2)                |
| 31     | Indirect, Ext. Register      | 10     | 2 - 4 | reg(1) reg(1) \<offset>(1-2)                |
| 31     | Indirect, Indirect           | 12     | 2 - 6 | reg(1) reg(1) \<offset>(1-2) \<offset>(1-2) |
| 37     | Address, Indirect            | 8      | 3 - 5 | addr(2) reg(1) \<offset>(1-2)               |
| 37     | Address, Ext. Register       | 6      | 3     | addr(2) reg(1)                              |
| 3B     | Address, Address             | 6      | 4     | addr(2) addr(2)                             |
| 39     | Address, Word                | 4      | 4     | addr(2) word(2)                             |
| 35     | Indirect, Address            | 10     | 3-5   | reg(1) addr(2) \<offset>(1-2)               |
| 33     | Indirect, Word               | 8      | 3-5   | reg(1) word(2) \<offset>(1-2)               |
| 35     | Ext. Register, Address       | 6      | 3     | reg(1) addr(2)                              |

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