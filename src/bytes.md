# Bytes

## Instructions

|     |                x0                 |                x1                 |                x2                |                x3                |                x4                 |                x5                 |                x6                 |                x7                 |                x8                |                x9                |                xA                |                   xB                    |                xC                 |                xD                 |                xE                |                   xF                    |
|-----|:---------------------------------:|:---------------------------------:|:--------------------------------:|:--------------------------------:|:---------------------------------:|:---------------------------------:|:---------------------------------:|:---------------------------------:|:--------------------------------:|:--------------------------------:|:--------------------------------:|:---------------------------------------:|:---------------------------------:|:---------------------------------:|:--------------------------------:|:---------------------------------------:|
| 0x  |                NOP                |               HALT                |           CALL<br>(A)            |         CALL<br>(E) (I)          |                RET                |               RETI                |          SWAP.B<br>(R,R)          |          SWAP.W<br>(R,R)          |         MCPY<br>(A,A,B)          |     MCPY<br>(A,E,B) (A,I,B)      |     MCPY<br>(E,A,B) (I,A,B)      | MCPY<br>(E,E,B) (I,E,B) (E,I,C) (I,I,C) |          MCPY<br>(A,A,R)          |      MCPY<br>(A,E,R) (A,I,R)      |     MCPY<br>(E,A,R) (I,A,R)      | MCPY<br>(E,E,R) (I,E,R) (E,I,R) (I,I,R) |
| 1x  | CPY.B<br>(R,R) (I,R) (R,I) (I,I)  | CPY.W<br>(E,E) (E,I) (I,E) (I,I)  |       CPY.B<br>(A,R) (A,I)       |       CPY.W<br>(A,E) (A,I)       |       CPY.B<br>(R,A) (I,A)        |       CPY.W<br>(E,A) (I,A)        |          CPY.B<br>(A,A)           |          CPY.W<br>(A,A)           |       CPY.B<br>(R,B) (I,B)       |       CPY.W<br>(E,W) (I,w)       |          CPY.B<br>(A,B)          |             CPY.W<br>(A,W)              |       CMP.B<br>(R,A) (I,A)        |       CMP.W<br>(E,A) (I,A)        |      CMPS.B<br>(R,A) (I,A)       |          CMPS.W<br>(E,A) (I,A)          |
| 2x  | ADD.B<br>(R,R) (I,R) (R,I) (I,I)  | ADD.W<br>(E,E) (E,I) (I,E) (I,I)  |       ADD.B<br>(R,B) (I,B)       |       ADD.W<br>(E,W) (I,W)       |       ADD.B<br>(R,A) (I,A)        |       ADD.W<br>(E,A) (I,A)        |       ADD.B<br>(A,R) (A,I)        |       ADD.W<br>(A,E) (A,I)        |          ADD.B<br>(A,B)          |          ADD.W<br>(A,W)          |          ADD.B<br>(A,A)          |             ADD.W<br>(A,A)              |         INC.B<br>(R) (I)          |         INC.W<br>(E) (I)          |           INC.B<br>(A)           |              INC.W<br>(A)               |
| 3x  | SUB.B<br>(R,R) (I,R) (R,I) (I,I)  | SUB.W<br>(E,E) (E,I) (I,E) (I,I)  |       SUB.B<br>(R,B) (I,B)       |       SUB.W<br>(E,W) (I,W)       |       SUB.B<br>(R,A) (I,A)        |       SUB.W<br>(E,A) (I,A)        |       SUB.B<br>(A,R) (A,I)        |       SUB.W<br>(A,E) (A,I)        |          SUB.B<br>(A,B)          |          SUB.W<br>(A,W)          |          SUB.B<br>(A,A)          |             SUB.W<br>(A,A)              |         DEC.B<br>(R) (I)          |         DEC.W<br>(E) (I)          |           DEC.B<br>(A)           |              DEC.W<br>(A)               |
| 4x  |         NOT.B<br>(R) (I)          |         NOT.W<br>(E) (I)          | OR.B<br>(R,R) (I,R) (R,I) (I,I)  | OR.W<br>(E,E) (E,I) (I,E) (I,I)  |        OR.B<br>(R,B) (I,B)        |        OR.W<br>(E,W) (I,W)        | XOR.B<br>(R,R) (I,R) (R,I) (I,I)  | XOR.W<br>(E,E) (E,I) (I,E) (I,I)  |       XOR.B<br>(R,B) (I,B)       |       XOR.W<br>(E,W) (I,W)       | AND.B<br>(R,R) (I,R) (R,I) (I,I) |    AND.W<br>(E,E) (E,I) (I,E) (I,I)     |       AND.B<br>(R,B) (I,B)        |       AND.W<br>(E,W) (I,W)        |            JRF<br>(B)            |               JRB<br>(B)                |
| 5x  |       ASL.B<br>(R,B) (I,B)        |       ASL.W<br>(E,W) (I,W)        | ASL.B<br>(R,R) (I,R) (R,I) (I,I) | ASL.W<br>(E,E) (E,I) (I,E) (I,I) |           ASL.B<br>(A)            |           ASL.W<br>(A)            |       ASR.B<br>(R,B) (I,B)        |       ASR.W<br>(E,W) (I,W)        | ASR.B<br>(R,R) (I,R) (R,I) (I,I) | ASR.W<br>(E,E) (E,I) (I,E) (I,I) |           ASR.B<br>(A)           |              ASR.W<br>(A)               |       LSR.B<br>(R,B) (I,B)        |       LSR.W<br>(E,W) (I,W)        | LSR.B<br>(R,R) (I,R) (R,I) (I,I) |    LSR.W<br>(E,E) (E,I) (I,E) (I,I)     |
| 6x  |           LSR.B<br>(A)            |           LSR.W<br>(A)            |       ROL.B<br>(R,B) (I,B)       |       ROL.W<br>(E,W) (I,W)       | ROL.B<br>(R,R) (I,R) (R,I) (I,I)  | ROL.W<br>(E,E) (E,I) (I,E) (I,I)  |           ROL.B<br>(A)            |           ROL.W<br>(A)            |       ROR.B<br>(R,B) (I,B)       |       ROR.W<br>(E,W) (I,W)       | ROR.B<br>(R,R) (I,R) (R,I) (I,I) |    ROR.W<br>(E,E) (E,I) (I,E) (I,I)     |           ROR.B<br>(A)            |           ROR.W<br>(A)            |                -                 |                    -                    |
| 7x  |         PUSH.B<br>(R) (B)         |        PUSH.W<br>(E) (W))         |           POP.B<br>(R)           |           POP.W<br>(W)           |                 -                 |                 -                 |                 -                 |                 -                 |                -                 |                -                 |                -                 |                    -                    |                 -                 |                 -                 |                -                 |                    -                    |
| 8x  | MUL.B<br>(R,R) (I,R) (R,I) (I,I)  | MUL.W<br>(E,E) (E,I) (I,E) (I,I)  |       MUL.B<br>(R,B) (I,B)       |       MUL.W<br>(E,W) (I,W)       |       MUL.B<br>(R,A) (I,A)        |       MUL.W<br>(E,A) (I,A)        |       MUL.B<br>(A,R) (A,I)        |       MUL.W<br>(A,E) (A,I)        |          MUL.B<br>(A,B)          |          MUL.W<br>(A,W)          |          MUL.B<br>(A,A)          |             MUL.W<br>(A,A)              | MULS.B<br>(R,R) (I,R) (R,I) (I,I) | MULS.W<br>(E,E) (E,I) (I,E) (I,I) |      MULS.B<br>(R,B) (I,B)       |          MULS.W<br>(E,W) (I,W)          |
| 9x  |       MULS.B<br>(R,A) (I,A)       |       MULS.W<br>(E,A) (I,A)       |      MULS.B<br>(A,R) (A,I)       |      MULS.W<br>(A,E) (A,I)       |          MULS.B<br>(A,B)          |          MULS.W<br>(A,W)          |          MULS.B<br>(A,A)          |          MULS.W<br>(A,A)          | DIV.B<br>(R,R) (I,R) (R,I) (I,I) | DIV.W<br>(E,E) (E,I) (I,E) (I,I) |       DIV.B<br>(R,B) (I,B)       |          DIV.W<br>(E,W) (I,W)           |       DIV.B<br>(R,A) (I,A)        |       DIV.W<br>(E,A) (I,A)        |       DIV.B<br>(A,R) (A,I)       |          DIV.W<br>(A,E) (A,I)           |
| Ax  |          DIV.B<br>(A,B)           |          DIV.W<br>(A,W)           |          DIV.B<br>(A,A)          |          DIV.W<br>(A,A)          | DIVS.B<br>(R,R) (I,R) (R,I) (I,I) | DIVS.W<br>(E,E) (E,I) (I,E) (I,I) |       DIVS.B<br>(R,B) (I,B)       |       DIVS.W<br>(E,W) (I,W)       |      DIVS.B<br>(R,A) (I,A)       |      DIVS.W<br>(E,A) (I,A)       |      DIVS.B<br>(A,R) (A,I)       |          DIVS.W<br>(A,E) (A,I)          |          DIVS.B<br>(A,B)          |          DIVS.W<br>(A,W)          |         DIVS.B<br>(A,A)          |             DIVS.W<br>(A,A)             |
| Bx  |            JMP<br>(A)             |          JMP<br>(E) (I)           |            JE<br>(A)             |          JE<br>(E) (I)           |            JNE<br>(A)             |          JNE<br>(E) (I)           |             JL<br>(A)             |           JL<br>(E) (I)           |            JG<br>(A)             |          JG<br>(E) (I)           |            JLE<br>(A)            |             JLE<br>(E) (I)              |            JGE<br>(A)             |          JGE<br>(E) (I)           |                -                 |                    -                    |
| Cx  |       CMP.B<br>(R,B) (I,B)        |       CMP.W<br>(E,W) (I,W)        | CMP.B<br>(R,R) (I,R) (R,I) (I,I) | CMP.W<br>(E,E) (E,I) (I,E) (I,I) |       CMPS.B<br>(R,B) (I,B)       |       CMPS.W<br>(E,W) (I,W)       | CMPS.B<br>(R,R) (I,R) (R,I) (I,I) | CMPS.W<br>(E,E) (E,I) (I,E) (I,I) |  JBC<br>(R,R) (I,R) (R,I) (I,I)  |  JBS<br>(R,R) (I,R) (R,I) (I,I)  |        JBC<br>(A,R) (A,I)        |           JBS<br>(A,R) (A,I)            |        JBC<br>(R,B) (I,B)         |        JBS<br>(R,B) (I,B)         |           JBC<br>(A,B)           |              JBS<br>(A,B)               |
| Dx  |                 -                 |                 -                 |                -                 |                -                 |                 -                 |                 -                 |                 -                 |                 -                 |                -                 |                -                 |                -                 |                    -                    |                 -                 |                 -                 |                -                 |                    -                    |                                   |                                   |                                 |                                 |                       |                       |                                  |                                  |                      |                         |                         |                                         |                      |                         |                         |     |
| Ex  | ADDC.B<br>(R,R) (I,R) (R,I) (I,I) | ADDC.W<br>(E,E) (E,I) (I,E) (I,I) |      ADDC.B<br>(R,B) (I,B)       |      ADDC.W<br>(E,W) (I,W)       |       ADDC.B<br>(R,A) (I,A)       |       ADDC.W<br>(E,A) (I,A)       |       ADDC.B<br>(A,R) (A,I)       |       ADDC.W<br>(A,E) (A,I)       |         ADDC.B<br>(A,B)          |         ADDC.W<br>(A,W)          |         ADDC.B<br>(A,A)          |             ADDC.W<br>(A,A)             | SUBC.B<br>(R,R) (I,R) (R,I) (I,I) | SUBC.W<br>(E,E) (E,I) (I,E) (I,I) |      SUBC.B<br>(R,B) (I,B)       |          SUBC.W<br>(E,W) (I,W)          |
| Fx  |       SUBC.B<br>(R,A) (I,A)       |       SUBC.W<br>(E,A) (I,A)       |      SUBC.B<br>(A,R) (A,I)       |      SUBC.W<br>(A,E) (A,I)       |          SUBC.B<br>(A,B)          |          SUBC.W<br>(A,W)          |          SUBC.B<br>(A,A)          |          SUBC.W<br>(A,A)          |                -                 |                -                 |                -                 |                    -                    |                 -                 |                 -                 |              EHALT               |                  SLEEP                  |

## Registers

| Name | Value | Hex | Offset | Size |
|------|-------|-----|--------|------|
| AH   | 0     | 00  | 0      | 1    |
| AL   | 1     | 01  | 1      | 1    |
| BH   | 2     | 02  | 2      | 1    |
| BL   | 3     | 03  | 3      | 1    |
| CH   | 4     | 04  | 4      | 1    |
| CL   | 5     | 05  | 5      | 1    |
| DH   | 6     | 06  | 6      | 1    |
| DL   | 7     | 07  | 7      | 1    |
| FLG  | 8     | 08  | 8      | 1    |
| AX   | 9     | 09  | 0      | 2    |
| BX   | 10    | 0A  | 2      | 2    |
| CX   | 11    | 0B  | 4      | 2    |
| dX   | 12    | 0C  | 6      | 2    |

## PPID

| Value | Hex | Indirect | Pre | Post | Inc | Dec |
|-------|-----|----------|-----|------|-----|-----|
| 0     | 00  | -        | -   | -    | -   | -   |
| 128   | 80  | x        | -   | -    | -   | -   |
| 64    | 40  | -        | -   | x    | x   | -   |
| 80    | 50  | -        | -   | x    | -   | x   |
| 96    | 60  | -        | x   | -    | x   | -   |
| 112   | 70  | -        | x   | -    | -   | x   |
| 129   | C0  | x        | -   | x    | x   | -   |
| 208   | D0  | x        | -   | x    | -   | x   |
| 224   | E0  | x        | x   | -    | x   | -   |
| 240   | F0  | x        | x   | -    | -   | x   |

## Byte Order

Each instruction must be written in the following order:

`OP ARG1 ARG2.. ARG1_OFFSET ARG2_OFFSET..`

For example:

| Instruction          | Order                      | Bytes               |
|----------------------|----------------------------|---------------------|
| `INC.B AL`           | `OP ARG1`                  | `2C 01`             |
| `ADD.W $200 (AX+10)` | `OP ARG1 ARG2 ARG2_OFFSET` | `27 00 C8 B9 00 0A` |