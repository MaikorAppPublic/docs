# ADD

Add values from destination and source together and store result in destination.

## Format 

`ADD dst, src`

## Variations

```
ADD.B (R, B) (R, R) (R, I) (I, R) (I, I) (A, I) (A, R) (A, A) (A, B) (I, A) (R, A) (I, B)
ADD.W (E, W) (E, E) (E, I) (I, E) (I, I) (A, I) (A, E) (A, A) (A, W) (I, A) (E, A) (I, W)
```

#### INC.B

| Opcode | Operands           | Cycles | Size  | Byte order                                  |
|--------|--------------------|--------|-------|---------------------------------------------|
| 22     | Register, Byte     | 2      | 2     | reg(1) byte(1)                              |
| 20     | Register, Register | 3      | 2     | reg(1) reg(1)                               |
| 20     | Register, Indirect | 5      | 2 - 4 | reg(1) reg(1) \<offset>(1-2)                |
| 20     | Indirect, Register | 7      | 2 - 4 | reg(1) reg(1) \<offset>(1-2)                |
| 20     | Indirect, Indirect | 9      | 2 - 6 | reg(1) reg(1) \<offset>(1-2) \<offset>(1-2) |
| 26     | Address, Indirect  | 5      | 3 - 5 | addr(2) reg(1) \<offset>(1-2)               |
| 26     | Address, Register  | 3      | 3     | addr(2) reg(1)                              |
| 2A     | Address, Address   | 3      | 4     | addr(2) addr(2)                             |
| 28     | Address, Byte      | 2      | 3     | addr(2) byte(1)                             |
| 24     | Indirect, Address  | 7      | 3-5   | reg(1) addr(2) \<offset>(1-2)               |
| 22     | Indirect, Byte     | 6      | 2-4   | reg(1) byte(1) \<offset>(1-2)               |
| 24     | Register, Address  | 3      | 3     | reg(1) addr(2)                              |

#### INC.W

| Opcode | Operands                     | Cycles | Size  | Byte order                                  |
|--------|------------------------------|--------|-------|---------------------------------------------|
| 23     | Ext. Register, Word          | 4      | 3     | reg(1) word(2)                              |
| 21     | Ext. Register, Ext. Register | 6      | 2     | reg(1) reg(1)                               |
| 21     | Ext. Register, Indirect      | 8      | 2 - 4 | reg(1) reg(1) \<offset>(1-2)                |
| 21     | Indirect, Ext. Register      | 10     | 2 - 4 | reg(1) reg(1) \<offset>(1-2)                |
| 21     | Indirect, Indirect           | 12     | 2 - 6 | reg(1) reg(1) \<offset>(1-2) \<offset>(1-2) |
| 27     | Address, Indirect            | 8      | 3 - 5 | addr(2) reg(1) \<offset>(1-2)               |
| 27     | Address, Ext. Register       | 6      | 3     | addr(2) reg(1)                              |
| 2B     | Address, Address             | 6      | 4     | addr(2) addr(2)                             |
| 29     | Address, Word                | 4      | 4     | addr(2) word(2)                             |
| 25     | Indirect, Address            | 10     | 3-5   | reg(1) addr(2) \<offset>(1-2)               |
| 23     | Indirect, Word               | 8      | 3-5   | reg(1) word(2) \<offset>(1-2)               |
| 25     | Ext. Register, Address       | 6      | 3     | reg(1) addr(2)                              |

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
result = lhs + rhs
```

## Examples

```
ADD.B AL, 5       # Store result of AL + 5 in AL
ADD.W (BX), $500  # Store the result of adding the values at the address in BX and at 500 at the address stored in BX 
```