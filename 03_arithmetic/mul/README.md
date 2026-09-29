# Unsigned multiplication flags

[mul1.asm](mul1.asm): `mul byte [num2]` | `25 * 10 = 250 = 0x00fa` in AX; high byte AH=0 | CF=0, OF=0: the product fits in AL. GDB displayed `0x202`.

[mul2.asm](mul2.asm):
`mul word [num2]` | `3000 * 200 = 600000 = 0x000927c0` 
in DX:AX (`DX=9`, `AX=0x27c0`)
CF=1, OF=1: the high half DX is nonzero, so the product does not fit in AX alone. GDB displayed `0xa03`.

MUL defines only CF and OF. SF, ZF, AF, and PF are **undefined** after MUL: GDB may display bit values for them, but those values must not be interpreted as facts about the product. 
IF is inherited and unaffected.