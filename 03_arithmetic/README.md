# 03_arithmetic examples

Two 32-bit NASM programs from each operation folder were assembled, linked, run, and stepped in GDB to inspect flags immediately after the arithmetic instruction:

- [Addition](add/README.md): `add1.asm`, `add3.asm` (ADD and ADC).
- [Subtraction](sub/README.md): `sub1.asm`, `sub3.asm` (SUB and SBB).
- [Multiplication](mul/README.md): `mul1.asm`, `mul2.asm` (MUL).
- [Division](div/README.md): `div1.asm`, `div2.asm` (DIV).

MUL defines CF and OF only.
DIV leaves arithmetic flags undefined.
See the linked reports for the defined flag values, result-dependent explanations, and GDB observations.
