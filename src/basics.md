# Maikor ASM Basics

## Add two numbers

```
cpy.b ah, 5   # set AH to 5
cpy.b al, 9   # set AL to 9
add.b ah, al  # set AH to AH + AL
```

## Add a series of numbers from memory

> Assume starting at $2000 are the numbers 100,100,100,200,300,400

```
		cpy.w dx, 2000    # set DX to 2000
loop: 	cpy.b al, (dx)+   # set AL to value at address in DX, then increment DX by 1
		add.w bx, ax      # set BX to AX + BX
		cmp.b dx, 2005    # compare DX and 2005
		jne loop          # if the numbers were not equal, jump to loop
```

At the end `bx` will be set to 1200. 

Normally there's no way to add a byte to a word, but by loading the byte into a lower register (e.g. AL) and setting the higher (AH) to 0, then the extended register (AX) allows the byte to be used a word.

