# Addition flags

[add1.asm](add1.asm)
`120 + 10 = 130` (`AL=0x82`) | 
SF=1 and OF=1 (two positive signed bytes produce a negative signed byte)
AF=1 (carry from bit 3)
PF=1 (even parity in `0x82`). 
CF=0 (no carry past bit 7), ZF=0 (nonzero). 

[add3.asm](add3.asm) 
`0xffff + 1 = 0x0000` (`AX`, with a carry out): CF=1, ZF=1, PF=1, AF=1; SF=0 and OF=0. 
The following `adc ax, 0` consumes CF to produce `AX=1` and sets CF=0, ZF=0, PF=0, AF=0, SF=0, OF=0. 

For `add3.asm`, the 16-bit sum wraps to zero: CF records the carry past bit 15, AF the carry past bit 3, and PF the eight zero bits in the low byte. There is no signed overflow because `0xffff` represents -1. After `adc`, the low byte is 1 (odd parity), and no carry or overflow occurs. GDB showed `0xa96` after `add1.asm`'s ADD, and `0x257` after `add3.asm`'s ADD followed by `0x202` after ADC.