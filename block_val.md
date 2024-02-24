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
|&emsp;[[string](https://github.com); value; the value is a string or name of a block terminal]
## Example