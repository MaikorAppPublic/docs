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

|Operands|Cycles|
|--------|------|
|Register, Byte|2|
|Register, Register|3|
|Register, Indirect|5|
|Indirect, Register|7|
|Indirect, Indirect|9|
|Address, Indirect|5|
|Address, Register|3|
|Address, Address|3|
|Address, Byte|2|
|Indirect, Address|7|
|Indirect, Byte|6|
|Register, Address|3|

#### INC.W

|Operands|Cycles|
|--------|------|
|Ext. Register, Word|4|
|Ext. Register, Ext. Register|6|
|Ext. Register, Indirect|8|
|Indirect, Ext. Register|10|
|Indirect, Indirect|12|
|Address, Indirect|8|
|Address, Ext. Register|6|
|Address, Address|6|
|Address, Word|4|
|Indirect, Address|10|
|Indirect, Word|8|
|Ext. Register, Address|6|

## Flags

|Flag|Update condition|
|---|---|
|Zero|Set if result is 0, otherwise cleared|
|Signed|Matches first bit of result|
|Carry|Set if result is greater 255 for `.B` or 65535 for `.W`, otherwise cleared|
|Less than|Always cleared|
|Greater than|Always cleared|
|Overflow|Set if the dst and result first bit are different, otherwise cleared|
|Interrupts|-|

## Code equivalent

```
result = lhs + rhs
```

## Examples

```
ADD.B AL 5    # Store result of AL + 5 in AL
```