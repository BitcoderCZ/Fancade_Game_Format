# Block Value
## Format
[uint8; index; in case the block has multiple values]\
[uint8; type; type of the value]\
[vec3i; pos; position of the block this value belongs to]\
if (type == 1)\
|&emsp;[uint8; value; the value is a byte]\
else if (type == 2)\
|&emsp;[uint16; value; the value is a ushort]\
else if (type == 4)\
|&emsp;[float; value; the value is a float]\
else if (type == 5)\
|&emsp;[vec3f; value; the value is a vector or rotation]\
else\
|&emsp;[[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md); value; the value is a string or name of a block terminal]
## Example
index: 0\
type: 5\
pos: (0, 0, 0)\
value: (90f, 0f, 0f)
```
000000: 00 05 00 00 00 00 00 00 00 00 B4 42 00 00 00 00 | ...........B.... |
000010: 00 00 00 00                                     | ....             |
```