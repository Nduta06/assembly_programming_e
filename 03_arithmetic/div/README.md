# Unsigned division flags

[div1.asm](div1.asm)
`div bl`
 `AX=100` divided by `BL=7`; quotient `AL=14`, remainder `AH=2` (`AX=0x020e`).
 CF, OF, SF, ZF, AF, PF are **undefined**; no set/clear status can be attributed to the quotient or remainder. GDB happened to display `0x212`.

[div2.asm](div2.asm):
`div bx`
`DX:AX=50000` divided by `BX=300`; quotient `AX=166`, remainder `DX=200`.
CF, OF, SF, ZF, AF, PF are **undefined**; no set/clear status can be attributed to the quotient or remainder. GDB happened to display `0x212`. 

DIV does not define arithmetic flags based on its result. The displayed AF bit in these runs is not evidence that division sets AF; IF is inherited and unaffected.
The later `xor ebx, ebx` *does* define flags: its zero result sets ZF=1 and PF=1, clears CF=0, OF=0, SF=0, and leaves AF undefined. Those statuses belong to XOR, not DIV.