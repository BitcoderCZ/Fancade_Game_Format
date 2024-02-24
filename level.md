# Level
## Format
[uint8; header_0; ]\
[uint8; header_1; 0x18 or 0x19 (has non default background color)]\
[uint8; header_2; always 0x03]\
[[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md); name; name of the level]\
if ((header_1 & 0b_0000_0001)) != 0\
|&emsp;[uint8; bc; background color of the level]\
else\
|&emsp;26&emsp;\#[uint8; bc; background color of the level]

if ((header_0 & 0b_0010_0000) != 0)\
|&emsp;[uint8; ; unknown]

if ((header_0 & 0b_0000_0100) != 0)\
|&emsp;[[block_data](https://github.com); blocks; size of the level and block ids]\
else\
|&emsp;the level is empty

if ((header_0 & 0b_0000_0010) != 0)\
|&emsp;[[array](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/array.md)<[block_val](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block_val.md)>; values; values of blocks (comment text, number value...)]\
else\
|&emsp;the level doesn't have any block values

if ((header_0 & 0b_0000_0001) != 0)\
|&emsp;[[array](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/array.md)<[block_con](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block_con.md)>; connections; connections between blocks]\
else\
|&emsp;the level doesn't have any connections
## Example
Tutorial/1. Top Down View\
name: "Top Down View"\
bc: 1
```
000000: 07 19 03 0D 54 6F 70 20 44 6F 77 6E 20 56 69 65 | ....Top Down Vie |
000010: 77 01 11 00 01 00 05 00 2A 00 2B 00 00 00 0C 01 | w.......*.+..... |
000020: 0D 01 00 00 2A 00 2B 00 00 00 00 00 00 00 00 00 | ....*.+......... |
000030: 81 01 00 00 81 01 81 01 81 01 2C 00 2D 00 00 00 | ..........,.-... |
000040: 0E 01 0F 01 00 00 2C 00 2D 00 00 00 12 01 13 01 | ......,.-....... |
000050: 00 00 81 01 00 00 00 00 00 00 81 01 00 00 00 00 | ................ |
000060: 00 00 10 01 11 01 00 00 00 00 00 00 00 00 14 01 | ................ |
000070: 15 01 00 00 81 01 81 01 00 00 81 01 81 01 0F 00 | ................ |
000080: 00 00 00 00 00 00 00 00 00 00 0F 00 00 00 00 00 | ................ |
000090: 00 00 00 00 00 00 81 01 00 00 00 00 00 00 81 01 | ................ |
0000A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 | ................ |
0000B0: 00 00 00 00 00 00 00 00 81 01 81 01 81 01 00 00 | ................ |
0000C0: 81 01 04 00 00 05 00 00 00 00 00 00 00 00 B4 42 | ...............B |
0000D0: 00 00 00 00 00 00 00 00 00 06 00 00 00 00 03 00 | ................ |
0000E0: 0D 54 6F 70 20 44 6F 77 6E 20 56 69 65 77 00 05 | .Top Down View.. |
0000F0: 06 00 00 00 00 00 00 00 34 42 00 00 61 43 00 00 | ........4B..aC.. |
000100: 00 00 00 06 06 00 00 00 03 00 0F 54 6F 70 20 52 | ...........Top R |
000110: 69 67 68 74 20 4C 69 67 68 74 02 00 00 00 00 00 | ight Light...... |
000120: 00 00 03 00 00 00 00 00 0E 00 01 00 0B 00 00 00 | ................ |
000130: 01 00 0B 00 06 00 00 00 00 00 09 00 00 00 01 00 | ................ |
000140: 0E 00 01 00 0B 00 00 00 01 00 03 00             | ............     |
```