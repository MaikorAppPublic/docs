# Memory

## Interrupt Addresses

| Name               | Description                                      | Control Bit | Int  | Hex | ASM Constant    |
|--------------------|--------------------------------------------------|-------------|------|-----|-----------------|
| Input              | Called when value at [Input](#input) changes     | 0           | 1280 | 500 | IRQ_INPUT       |
| Line Drawn         | Called after a line has been drawn               | 1           | 1344 | 540 | IRQ_LINE_DRAW   |
| Screen Drawn       | Called after the screen has finished being drawn | 2           | 1408 | 580 | IRQ_SCREEN_DRAW |
| Timer              | Called after a timer overflows                   | 3           | 1472 | 5C0 | IRQ_TIMER       |
| Controller Changed | Called after the controller type changed         | 4           | 1536 | 600 | IRQ_CONTROLLER  |

Also see [Interrupt control](#interrupt-control)

## Addresses

| Name                                                | Description                                                            | Int   | Hex  | ASM Constant     | Length |
|-----------------------------------------------------|------------------------------------------------------------------------|:------|:-----|------------------|:-------|
| [Code](#code)                                       | Main game code                                                         | 0     | 0    | `MAIN_CODE`      | 9000   |
| [Banked Code 1](#banked-code-1)                     | Switchable game code, controlled via [Code Bank 1 ID](#code-bank-1-id) | 9000  | 2328 | `CODE_BANK_1`    | 4200   |
| [Banked Code 2](#banked-code-2)                     | Switchable game code, controlled via [Code Bank 2 ID](#code-bank-2-id) | 13200 | 3390 | `CODE_BANK_2`    | 4200   |
| [RAM](#ram)                                         | Main RAM                                                               | 17400 | 43F8 | `RAM`            | 9000   |
| [Banked RAM 1](#banked-ram-1)                       | Switchable RAM, controlled via [RAM Bank 1 ID](#ram-bank-1-id)         | 26400 | 6720 | `RAM_BANK_1`     | 4200   |
| [Banked RAM 2](#banked-ram-2)                       | Switchable RAM, controlled via [RAM Bank 2 ID](#ram-bank-2-id)         | 30600 | 7788 | `RAM_BANK_2`     | 4200   |
| [Input](#input)                                     | 12 bits in 2 bytes to check if buttons are pressed                     | 34800 | 87F0 | `INPUT`          | 2      |
| [Sound](#sound)                                     | Sound control bytes                                                    | 34802 | 87F2 | `SOUND`          | 30     |
| [Save Bank ID](#save-bank-id)                       | Controls which save data bank is loaded at [Save Bank](#save-bank)     | 34832 | 8810 | `SAVE_BANK_ID`   | 1      |
| [Save Bank](#save-bank)                             | Switchable save data, also see [Save Control](#save-control)           | 34833 | 8811 | `SAVE_BANK`      | 4096   |
| [Atlas 1](#atlas-1)                                 | Atlas Bank 1, controlled by [Atlas 1 Bank ID](#atlas-1-bank-id)        | 38929 | 9811 | `ATLAS1`         | 4000   |
| [Atlas 2](#atlas-2)                                 | Atlas Bank 2, controlled by [Atlas 2 Bank ID](#atlas-2-bank-id)        | 42929 | A7B1 | `ATLAS2`         | 4000   |
| [Atlas 3](#atlas-3)                                 | Atlas Bank 3, controlled by [Atlas 3 Bank ID](#atlas-3-bank-id)        | 46929 | B751 | `ATLAS3`         | 4000   |
| [Atlas 4](#atlas-4)                                 | Atlas Bank 4, controlled by [Atlas 4 Bank ID](#atlas-4-bank-id)        | 50929 | C6F1 | `ATLAS4`         | 4000   |
| [Palettes](#palettes)                               | 4 palettes, each made of 15 colors (3 bytes)                           | 54929 | D691 | `PALETTES`       | 180    |
| [Sprite Table](#sprite-table)                       | Table of 255 sprites, made of 5 bytes each                             | 55121 | D751 | `SPRITE_TABLE`   | 1275   |
| [Layer Headers](#layer-headers)                     | Headers for the 3 background layers                                    | 56396 | DC4C | `LAYER_HEADERS`  | 9      |
| [Layer Contents](#layer-contents)                   | Contents for the 3 background layers                                   | 56405 | DC55 | `LAYER_CONTENTS` | 7920   |
| [Code Bank 1 ID](#code-bank-1-id)                   | Controls which code bank is loaded at [Banked Code 1](#code-bank-1-id) | 64325 | FB45 | `CODE_BANK_1_ID` | 1      |
| [RAM Bank 1 ID](#ram-bank-1-id)                     | Controls which RAM bank is loaded at [Banked RAM 2](#ram-bank-1-id)    | 64326 | FB46 | `RAM_BANK_1_ID`  | 1      |
| [Atlas 1 Bank ID](#atlas-1-bank-id)                 | Controls which atlas bank is loaded at [Atlas 1](#atlas-1)             | 64327 | FB47 | `ATLAS1_BANK_ID` | 1      |
| [Atlas 2 Bank ID](#atlas-2-bank-id)                 | Controls which atlas bank is loaded at [Atlas 2](#atlas-2)             | 64328 | FB48 | `ATLAS2_BANK_ID` | 1      |
| [Atlas 3 Bank ID](#atlas-3-bank-id)                 | Controls which atlas bank is loaded at [Atlas 3](#atlas-3)             | 64329 | FB49 | `ATLAS3_BANK_ID` | 1      |
| [Atlas 4 Bank ID](#atlas-4-bank-id)                 | Controls which atlas bank is loaded at [Atlas 4](#atlas-4)             | 64330 | FB4A | `ATLAS4_BANK_ID` | 1      |
| [SP](#sp)                                           | Stack Pointer                                                          | 64331 | FB4B | `SP`             | 2      |
| [FP](#fp)                                           | Frame Pointer                                                          | 64333 | FB4D | `FP`             | 2      |
| [Timer Control](#timer-control)                     | Control bytes for timers                                               | 64335 | FB4F | `TIMER_CONTROL`  | 2      |
| [Timer 1](#timer-1)                                 | Value of timer 1                                                       | 64337 | FB51 | `TIMER1`         | 1      |
| [Timer 2](#timer-2)                                 | Value of timer 2                                                       | 64338 | FB52 | `TIMER2`         | 1      |
| [Timer 3](#timer-3)                                 | Value of timer 3                                                       | 64339 | FB53 | `TIMER3`         | 1      |
| [Timer 4](#timer-4)                                 | Value of timer 4                                                       | 64340 | FB54 | `TIMER4`         | 1      |
| [VLine](#vline)                                     | Next line to be drawn                                                  | 64351 | FB5F | `VLINE`          | 1      |
| [Controller Type](#controller-type)                 | Active controller type ID                                              | 64352 | FB60 | `INPUT_TYPE`     | 1      |
| [Controller Graphics](#controller-graphics)         | Graphics for controller buttons                                        | 64353 | FB61 | `INPUT_GRAPHICS` | 88     |
| [Controller Palette](#controller-palette)           | Palette used when drawing controller buttons                           | 64441 | FBB9 | `INPUT_PALETTE`  | 12     |
| [Controller Sprite Table](#controller-sprite-table) | Sprite table for controller buttons                                    | 64453 | FBC5 | `INPUT_TABLE`    | 27     |
| [Interrupt Control](#interrupt-control)             | Control byte for interrupts                                            | 64480 | FBE0 | `IRQ_CONTROL`    | 1      |
| [Save Control](#save-control)                       | Control byte for save data                                             | 64481 | FBE1 | `SAVE_CONTROL`   | 1      |
| [Date time](#date-time)                             | Date time in bytes                                                     | 64482 | FBE2 | `DATETIME`       | 6      |
| [Rand](#rand)                                       | Regularly changing random value                                        | 64488 | FBE8 | `RAND`           | 1      |
| [Wave Table](#wave_table)                           | Sound wave table                           				                        | 64489 | FBE9 | `WAVE_TABLE`     | 16     |
| [Code Bank 2 ID](#code-bank-2-id)                   | Controls which code bank is loaded at [Banked Code 2](#code-bank-2-id) | 64505 | FBF9 | `CODE_BANK_2_ID` | 1      |
| [RAM Bank 2 ID](#ram-bank-2-id)                     | Controls which RAM bank is loaded at [Banked RAM 2](#ram-bank-2-id)    | 64506 | FBFA | `RAM_BANK_2_ID`  | 1      |
| [Stack](#stack)                                     | The Stack                                                              | 64536 | FC18 | `STACK`          | 1000   |

## Code

`0` `x0` `MAIN_CODE` 9000 bytes

Interrupts call in this section, at these addresses:

| Called when..                           | ASM               | Address |
|-----------------------------------------|-------------------|---------|
| a button is pressed/released            | `IRQ_INPUT`       | `$x200` |
| after screen drawn                      | `IRQ_SCREEN_DRAW` | `$x240` |
| when a timer overflows                  | `IRQ_TIMER`       | `$x260` |
| controller changes                      | `IRQ_CONTROLLER`  | `$x280` |
| date time changes by more than 1 second | `IRQ_DATETIME`    | `$x2A0` |


## Banked Code 1

`9000` `x2328` `CODE_BANK_1` 4200 bytes

Controlled with [Code Bank 1 ID](#code-bank-1-id)

## Banked Code 2

`13200` `x3390` `CODE_BANK_2` 4200 bytes

Controlled with [Code Bank 2 ID](#code-bank-2-id)

## RAM

`17400` `x43F8` `RAM` 9000 bytes

## Banked RAM 1

`26400` `x6720` `RAM_BANK_1` 4200 bytes

Controlled with [RAM Bank 1 ID](#ram-bank-1-id)

## Banked RAM 2

`30600` `x7788` `RAM_BANK_2` 4200 bytes

Controlled with [RAM Bank 2 ID](#ram-bank-2-id)

## Input

`$34800` `$x87F0` `INPUT` `2 bytes`
`$34800` `$x87F0` `DIR_INPUT` `1 byte`
`$34801` `$x87F1` `ACTION_INPUT` `1 byte`

Bits are set to true when the button is pressed, and cleared when it's released.
This has to be polled, to get an interrupt set the input bit in [Interrupt control](#interrupt-control) and code at [Interrupts](#interrupt-addresses).

#### Byte 0

| Bit | Name  |
|-----|-------|
| 7   | Up    |
| 6   | Down  |
| 5   | Left  |
| 4   | Right |

#### Byte 1

| Bit | Name  |
|-----|-------|
| 7   | A     |
| 6   | B     |
| 5   | START |
| 4   | L     |
| 3   | R     |
| 2   | X     |
| 1   | Y     |

## Sound

`34802` `x87F2` `SOUND` 30 bytes

Maikor is mostly compatible with the Gameboy sound system.

**Square 1**

| Name    | Address | Format      | Description                                            | Gameboy reg |
|---------|---------|-------------|--------------------------------------------------------|-------------|
| `SQ1_0` | `87F2`  | `-PPP NSSS` | Sweep **p**eriod, **N**egate, **S**hift                | NR10        |
| `SQ1_1` | `87F3`  | `DDLL LLLL` | **D**uty, **L**ength load                              | NR11        |
| `SQ1_2` | `87F4`  | `VVVV APPP` | Starting **V**olume, Envelope **a**dd mode, **p**eriod | NR12        |
| `SQ1_3` | `87F5`  | `FFFF FFFF` | **F**requency LSB                                      | NR13        |
| `SQ1_4` | `87F6`  | `TL-- -FFF` | **T**rigger, **L**ength enable, **F**requency MSB      | NR14        |

**Square 2**

| Name    | Address | Format      | Description                                            | Gameboy reg |
|---------|---------|-------------|--------------------------------------------------------|-------------|
| `SQ2_1` | `87F8`  | `DDLL LLLL` | **D**uty, **L**ength load                              | NR21        |
| `SQ2_2` | `87F9`  | `VVVV APPP` | Starting **V**olume, Envelope **a**dd mode, **p**eriod | NR22        |
| `SQ2_3` | `87FA`  | `FFFF FFFF` | **F**requency LSB                                      | NR23        |
| `SQ2_4` | `87FB`  | `TL-- -FFF` | **T**rigger, **L**ength enable, **F**requency MSB      | NR24        |


**Wave**

| Name   | Address | Format      | Description | Gameboy reg |
|--------|---------|-------------|-------------|-------------|
| `WC_0` | `87FC`  | `E--- ----` | **E**nable  | NR30        |

**Noise**

| Name   | Address | Format      | Description     | Gameboy reg |
|--------|---------|-------------|-----------------|-------------|
| `NC_0` | `8802`  | `--LL LLLL` | **L**ength load | NR41        |

**Control**

| Name    | Address | Format      | Description                       | Gameboy reg |
|---------|---------|-------------|-----------------------------------|-------------|
| `SND_V` | `8806`  | `-LLL -RRR` | **L**eft volume, **R**ight volume | NR50        |
| `SND_B` | `8807`  | `LLLL RRRR` | **L**eft balance, **R** balance   | NR51        |
| `SND_P` | `8808`  | `P--- ????` | **P**ower                         | NR52        |



## Save Bank ID

`34832` `x8810` `SAVE_BANK_ID` 1 byte

Controls which save data bank is loaded at [Save Bank](#save-bank). Changing this value immediately loads the data.

Valid values are 0-15.

## Save Bank

`34833` `x8811` `SAVE_BANK` 4096 bytes

Save data for the game. Games can use all bytes in all banks however they want.

See [Save Control](#save-control)

## Atlas 1

`38929` `x9811` `ATLAS1` 4000 bytes

## Atlas 2

`42929` `xB751` `ATLAS2` 4000 bytes

## Atlas 3

`46929` `x9811` `ATLAS3` 4000 bytes

## Atlas 4

`50929` `xB751` `ATLAS4` 4000 bytes


## Palettes

`54929` `xD691` `PALETTES` 192 bytes

`54929` `xD691` 48 bytes Palette 1
`54989` `xD6CD` 48 bytes Palette 2
`55049` `xD709` 48 bytes Palette 3
`55049` `xD709` 48 bytes Palette 3

Each palette is made of 16 3 byte RGB colors.

## Sprite Table

`55121` `xD751` `SPRITE_TABLE` 1275 bytes

255 

## Layer Headers

`56396` `xDC4C` `LAYER_HEADERS` 9 bytes

## Layer Contents

`56405` `xDC55` `LAYER_CONTENTS` 7920 bytes

## Code Bank 1 ID

`64325` `xFB45` `CODE_BANK_1_ID` 1 byte

Controls which code bank is loaded at [Code bank 1](#code-bank-1). Changing this value immediately loads the code; this is done by copying data from the bank into main memory, it takes several milliseconds.

Valid values are the number of code banks included in the game.

## RAM Bank 1 ID

`64326` `xFB46` `RAM_BANK_1_ID` 1 byte

Controls which RAM bank is loaded at [RAM bank 1](#ram-bank-1). Changing this value immediately loads the data; this is done by copying data from the bank into main memory, it takes several milliseconds.

Valid values are the number of RAM banks requested by the game.

## Atlas 1 Bank ID

`64327` `xFB47` `ATLAS1_BANK_ID` 1 byte

Controls which atlas bank is loaded at [Atlas 1](#atlas-1). Changing this value immediately loads the data.

Valid values are the number of atlas banks included in the game.

## Atlas 2 Bank ID

`64328` `xFB48` `ATLAS2_BANK_ID` 1 byte

Controls which atlas bank is loaded at [Atlas 2](#atlas-2). Changing this value immediately loads the data.

Valid values are the number of atlas banks included in the game.

## SP

`64329` `xFB49` `SP` 2 bytes

Points to the end of the [Stack](#stack)

## FP

`64331` `xFB4B` `FP` 2 bytes

Points to the start of the current in the [Stack](#stack)

## Timer Control

`64333` `xFB4D` `TIMER_CONTROL` 2 bytes

## Timer 1

`64335` `xFB4F` `TIMER1` 1 byte

## Timer 2

`64336` `xFB50` `TIMER2` 1 byte

## Timer 3

`64337` `xFB51` `TIMER3` 1 byte

## Timer 4

`64338` `xFB52` `TIMER4` 1 byte

## VLine

`64349` `xFB5D` `VLINE` 1 byte

Line (0-159) on the screen that be drawn next. It is automatically updated by the host before it calls `IRQ_LINE_DRAW`.

## Controller Type

`64350` `xFB5E` `INPUT_TYPE` 1 byte

ID of current active controller type.

This is set automatically by the host. Updating it will cause the controller graphics to load.

| Name        | Value | Description                                         |
|-------------|-------|-----------------------------------------------------|
| Unknown     | 0     | Default value, graphics should match Maikor buttons |
| XBOX        | 1     | XBox controller                                     |
| Playstation | 2     | Playstation 4/5 controller                          |
| Switch      | 3     | Switch Pro controller                               |
| Screen      | 4     | Touch screen controls                               |
| Keyboard 1  | 5     | WASD+IOKL keys                                      |
| Keyboard 2  | 6     | UDLR+QWAS keys                                      |
| Keyboard 3  | 7     | ?+? keys                                            |
| Keyboard 4  | 8     | ?+? keys                                            |

## Controller Graphics

`64351` `xFB5F` `INPUT_GRAPHICS` 88 bytes

## Controller Palette

`64439` `xFBB7` `INPUT_PALETTE` 12 bytes

## Controller Sprite Table

`64451` `xFBC3` `INPUT_TABLE` 24 bytes

## Interrupt Control

`64475` `xFBDB` `IRQ_CONTROL` 1 byte

Control byte for interrupts, if a bit is set then that interrupt can be called.

| Name               | Bit | Default | Description                                                        |
|--------------------|-----|---------|--------------------------------------------------------------------|
| Input              | 0   | 1       | Call `IRQ_INPUT` when [Input](#input) changes                      |
| Line Drawn         | 1   | 0       | Call `IRQ_LINE_DRAW` when a line has been drawn to the screen      |
| Screen Drawn       | 2   | 0       | Call `IRQ_SCREEN_DRAW` when last last has been drawn to the screen |
| Timer              | 3   | 0       | Call `IRQ_TIMER` when any timer overflows                          |
| Controller Changed | 4   | 0       | Call `IRQ_CONTROLLER` when the controller type changes             |

## Save Control

`64476` `xFBDC` `SAVE_CONTROL` 1 byte

| Name      | Bit | Default | Description                                                                                                                                                                                                                      |
|-----------|-----|---------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Auto save | 4   | 0       | When set, any value written to [Save Bank](#save-bank) is also written to disk                                                                                                                                                   |
| Write     | 0   | 0       | When set, the host will write [Save Bank](#save-bank) to disk and then clear the bit. If it remains set then the save fail, and may be retried (although most likely the issue will be permissions, etc and retrying won't help) |

## Date time

`64477` `xFBDD` `DATETIME` 6 bytes

This updates during each second and so may be up to 1 second off.

| Name   | Byte | Range | Description                |
|--------|------|-------|----------------------------|
| Year   | 0    | 0-255 | Covers years 2000-2255     |
| Month  | 1    | 1-12  | January = 1, December = 12 |
| Day    | 2    | 1-31  | Day of month               |
| Hour   | 3    | 0-23  | Hour of day                |
| Minute | 4    | 0-59  | Minute of hour             |
| Second | 5    | 0-59  | Second of minute           |

## Rand

`64483` `xFBE3` `RAND` 1 byte

This byte contains a random value that updates regularly. It should not be used for secure/cryptographic purposes.

## Code Bank 2 ID

`64325` `xFB45` `CODE_BANK_2_ID` 1 byte

Controls which code bank is loaded at [Code bank 2](#code-bank-2). Changing this value immediately loads the code; this is done by copying data from the bank into main memory, it takes several milliseconds.

Valid values are the number of code banks included in the game.

## RAM Bank 2 ID

`64326` `xFB46` `RAM_BANK_2_ID` 1 byte

Controls which RAM bank is loaded at [RAM bank 2](#ram-bank-2). Changing this value immediately loads the data; this is done by copying data from the bank into main memory, it takes several milliseconds.

Valid values are the number of RAM banks requested by the game.

## Stack

`64635` `xFC71` `STACK` 900 bytes

The stack grows upwards from xFC71 to xFFFF.

## Reserved

`64327` `xFB47` `-` 10 bytes
`64465` `xFBE4` `-` 151 bytes

Do not change or rely on values in this space.