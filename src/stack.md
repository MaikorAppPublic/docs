# Stack

The stack is made of frames, a frame is created after each CALL.

The stack starts at `64635` `xFC71` `STACK` and grows upwards to xFFFF.

The VM will fail if:
- SP (`64329` `xFB49` `SP`) is xFFFE and any PUSH or CALL occurs
- FP (`64331` `xFB4B` `FP`) is xFC71 and any POP occurs
- SP (`64329` `xFB49` `SP`) is xFC71 and any RET occurs

Except on the first call, FP will be set to the old SP value. SP always points to next byte to be written in the stack.

The first 4 bytes of each frame (except the first), will be the old FP and the address of the instruction after the CALL.

With the program 
```
0000 CALL $x1000
0256 RET
1000 PUSH.B 15
1002 CALL $x256
1005 RET
```

Initial:

| Address | Value |
|----|----|
| PC | `0000` |
| FP | `0000` |
| SP | `FC71` |
| Stack | `-` |

After `CALL $x1000`:

| Address | Value |
|----|----|
| PC | `1000` |
| FP | `FC71` |
| SP | `FC75` |
| Stack | `00 00 00 03` |

After `PUSH.B 15`:

| Address | Value |
|----|----|
| PC | `1002` |
| FP | `FC71` |
| SP | `FC76` |
| Stack | `00 00 00 03 15` |

After `CALL $x256`:

| Address | Value |
|----|----|
| PC | `256` |
| FP | `FC76` |
| SP | `FC7A` |
| Stack | `00 00 00 03 15 FC 71 10 05` |

After `RET` (at 256):

| Address | Value |
|----|----|
| PC | `1005` |
| FP | `FC71` |
| SP | `FC76` |
| Stack | `00 00 00 03 15` |

After `RET` (at 1005):

| Address | Value |
|----|----|
| PC | `0003` |
| FP | `0000` |
| SP | `FC71` |
| Stack | `-` |

