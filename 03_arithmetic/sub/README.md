# Subtraction flags

[sub1.asm](sub1.asm)
`sub al, [num2]` | `50 - 80 = -30`, wrapped to `AL=0xe2`
CF=1 (unsigned borrow), SF=1 (sign bit set), PF=1 (four 1 bits in low byte).
ZF=0 (nonzero), AF=0 (no borrow from bit 4), OF=0 (signed -30 fits in a byte). 
GDB: `0x287`.

[sub3.asm](sub3.asm)
`sub ax, [num2]` | `0 - 1 = -1`, `AX=0xffff`
CF=1 (borrow), AF=1 (low nibble borrows), SF=1, PF=1 (low byte `0xff` has eight 1 bits).
ZF=0; OF=0 (signed -1 fits). GDB: `0x297`. 

[sub3.asm](sub3.asm)
`sbb ax, 0` | `0xffff - 0 - CF(1) = 0xfffe`
SF=1 (negative signed result).
CF=0 and AF=0 (no borrow is needed from `0xffff`)
PF=0 (low byte `0xfe` has seven 1 bits)
ZF=0 and OF=0.
GDB: `0x282`.