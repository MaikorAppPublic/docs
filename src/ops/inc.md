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

|Operands|Cycles|
|--------|------|
|Register|2|
|Indirect|6|
|Address|2|

#### INC.W

|Operands|Cycles|
|--------|------|
|Ext. Register|4|
|Indirect|8|
|Address|4|

## Flags

No changes

## Code equivalent

```
var++
```

## Examples

```
INC.B AL      # Increase AL by 1
INC.B $6003   # Increase value at 6003 by 1
INC.B (AX)    # Increase value at address in AX by 1
INC.W AX      # Increase AX by 1
INC.W $6700   # Increase value at [6700,6701] by 1
```