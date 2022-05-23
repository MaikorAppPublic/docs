# Graphics

Maikor uses a tile/sprite based system, tiles are 8x8 pixels and can have up to 16 colors. 
It has 3 background layers, each one stores 44x30 tiles (although only 30x20 can be seen at once) and can show up to 256 sprites on screen at once.

Tile data is stored in the 4 atlas banks, each one can store up to 250 tiles. As each pixel can only be 1 of 16 colors, the pixels are stored 2 per byte. So, tiles take up 32 bytes in the atlas.

Although a sprite may only use 16 colors, it has choice of up to 4 palettes to use for color.
Sprites are controlled via the sprite table which sets their position, palette, etc.

Palettes store their colors as red, green, blue x 16 bytes.

## Memory

### Atlases

| Atlas | Dec | Hex | ASM | 
|----|----|----|----|
|1|`38929`|`x9811`|`ATLAS1`|
|2|`42929`|`x9811`|`ATLAS2`|
|3|`46929`|`x9811`|`ATLAS3`|
|4|`50929`|`x9811`|`ATLAS4`|

Each atlas stores 250 8x8 tiles, the tiles are packed by row and pixels are packed 2 per byte:


```
At $38929:

Pixel 1 of Tile 1           
|             Pixel 9 of Tile 1
|             |			
00 00  00 00  00 00  00 00  00 00  00 00
 |
 | 
 Pixel 2 of Tile 1
```

or put another away:

```
38929 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 # Tile 1, rows 1 - 4
38945 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 # Tile 1, rows 5 - 8
38961 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 # Tile 2, rows 1 - 4
38977 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 # Tile 2, rows 5 - 8
```

So for atlas 1, tile 0 is at 38929 and then tile 1 is at 38961, and so on.

### Palettes

| Atlas | Dec | Hex | ASM | 
|----|----|----|----|
|1|`54929`|`xD691`|`PALETTE1`|
|2|``|`x`|`PALETTE2`|
|3|`55049`|`x`|`PALETTE3`|
|4|``|`x`|`PALETTE4`|

```
At $54929:
Red value for color 1     Blue value for color 3
||                        ||
00 00 00  00 00 00  00 00 00
   || 
   Green value for color 1 
```

or put another way:
```
54929 00 00 00 # Palette 1, color 1
54932 00 00 00 # Palette 1, color 2
54935 00 00 00 # Palette 1, color 3
...
55049 00 00 00 # Palette 3, color 1
```

### Sprites

Each sprite is controlled by 5 bytes:

|Byte|Description|
|----|----|
|0|X Pixel|
|1|Y Pixel|
|2|Tile ID|
|3|Options 1|
|4|Options 2|

**Options 1**

|Bit|Length|Name|Description
|----|----|----|----|
|0|1|FLIP_V|If set, sprite is drawn vertically flipped|
|1|1|FLIP_H|If set, sprite is drawn horizontally flipped|
|2|1|HALF_ALPHA|If set, sprite is drawn partially transparent|
|3|1|ROTATED|If set, sprite is drawn rotated by 90 degrees|
|7|1|ENABLED|If set, sprite is drawn, otherwise it is skipped|

**Options 2**

|Bit|Length|Name|Description
|----|----|----|----|
|0|1|LARGE|If set, sprite is drawn using 4 tiles starting at Tile ID|
|1|2|ORDER|Order to draw sprite compared to background and other sprites, 0 is on top (values: 0 - 3)|
|3|2|ATLAS|ID of atlas to use (values: 0 - 3)|
|6|2|PALETTE|ID of palette to use (values: 0 - 3)|

Sprite data is stored at `55121` `xD751` `SPRITE_TABLE`, sprite 0 is at 55121, sprite 1 is at 55156, etc
