# ADD

Add values from destination and source together and store result in destination.

## Format 

`ADD dst src`

## Variations

```
ADD.B (R, B) (R, R) (R, I) (I, R) (I, I) (A, I) (A, R) (A, A) (A, B) (I, A) (R, A) (I, B)
ADD.W (E, W) (E, E) (E, I) (I, E) (I, I) (A, I) (A, E) (A, A) (A, W) (I, A) (E, A) (I, W)
```

#### INC.B

| Opcode | Operands           | Cycles |
|--------|--------------------|--------|
| 22     | Register, Byte     | 2      |
| 20     | Register, Register | 3      |
| 20     | Register, Indirect | 5      |
| 20     | Indirect, Register | 7      |
| 20     | Indirect, Indirect | 9      |
| 26     | Address, Indirect  | 5      |
| 26     | Address, Register  | 3      |
| 2A     | Address, Address   | 3      |
| 28     | Address, Byte      | 2      |
| 24     | Indirect, Address  | 7      |
| 22     | Indirect, Byte     | 6      |
| 24     | Register, Address  | 3      |

#### INC.W

| Opcode | Operands                     | Cycles |
|--------|------------------------------|--------|
| 23     | Ext. Register, Word          | 4      |
| 21     | Ext. Register, Ext. Register | 6      |
| 21     | Ext. Register, Indirect      | 8      |
| 21     | Indirect, Ext. Register      | 10     |
| 21     | Indirect, Indirect           | 12     |
| 27     | Address, Indirect            | 8      |
| 27     | Address, Ext. Register       | 6      |
| 2B     | Address, Address             | 6      |
| 29     | Address, Word                | 4      |
| 25     | Indirect, Address            | 10     |
| 23     | Indirect, Word               | 8      |
| 25     | Ext. Register, Address       | 6      |

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
ADD.B AL 5       # Store result of AL + 5 in AL
ADD.W (BX) $500  # Store the result of adding the values at the address in BX and at 500 at the address stored in BX 
```