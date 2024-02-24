# Block
## Info
Section = 8\*8\*8 part of the block
## Format
### Header
[uint8; header0; ]\
|&emsp;((header0 & 0b_1000_0000) != 0)&emsp;\#[bool; unknown; ]\
|&emsp;((header0 & 0b_0100_0000) != 0)&emsp;\#[bool; uneditable; makes the block not editable]\
|&emsp;((header0 & 0b_0001_0000) != 0)&emsp;\#[bool; multi_block; if the block is made of multiple blocks]\
|&emsp;((header0 & 0b_0000_0100) != 0)&emsp;\#[bool; blocks_inside; if the block has blocks inside]\
|&emsp;((header0 & 0b_0000_0010) != 0)&emsp;\#[bool; values_inside; if the block has block values inside]\
|&emsp;((header0 & 0b_0000_0001) != 0)&emsp;\#[bool; connections_inside; if the block has connections inside (also includes terminals (connections from outside to inside))]\
|&emsp;(header0 & 0b_0010_1000)&emsp;\#[uint8; [collider](https://github.com).value; what collider the block has]

[uint8; header1; ]\
if (header1 == 0x08)\
|&emsp;block_type.normal&emsp;\#[[block_type](https://github.com); block_type; ]\
else if (header1 == 0x18)\
|&emsp;[uint8; header2; ]\
|&emsp;if (header2 == 0x01)\
|&emsp;|&emsp;type is physics\
|&emsp;else if (header2 == 0x02)\
|&emsp;|&emsp;type is script\
|&emsp;else\
|&emsp;|&emsp;invalid header\
else if (header1 == 0x00)\
|&emsp;type is section (when a block is made of multiple blocks, only 1 has full header, the rest are type section)\
|&emsp;if ((header0 & 0b_0010_0000) != 0)\
|&emsp;|&emsp;[uint8; ; not needed]\
else if (header1 == 0x10)\
|&emsp;type is section (when a block is made of multiple blocks, only 1 has full header, the rest are type section)\
|&emsp;[uint8; ; not needed]\
|&emsp;if ((header0 & 0b_0010_0000) != 0)\
|&emsp;|&emsp;[uint8; ; not needed]

type != section&emsp;\#[bool; isMain; if this section is the one with full header]

if (isMain)\
|&emsp;[[string](https://github.com); name; name of the block]\
|&emsp;if ((header0 & 0b_0010_0000) != 0)\
|&emsp;|&emsp;[uint8; [collider](https://github.com).value2; additional collider value]\
|&emsp;else if (type == script))\
|&emsp;|&emsp;[uint8; ; not needed]
### Main part
if (!isMain || (isMain && multi_block))\
|&emsp;[uint16; is; id of this block]\
|&emsp;[vec3i; pos; position of this section]\
else\
|&emsp;this block is 1x1x1\
|&emsp;id is determined by order, either by other blocks that aren't 1x1x1 or by the number of build-in blocks in this format version

[[block_face](https://github.com)[8 * 8 * 8]; facesX; 3d array of +x faces]\
[[block_face](https://github.com)[8 * 8 * 8]; facesNX; 3d array of -x faces]\
[[block_face](https://github.com)[8 * 8 * 8]; facesY; 3d array of +y faces]\
[[block_face](https://github.com)[8 * 8 * 8]; facesNY; 3d array of -y faces]\
[[block_face](https://github.com)[8 * 8 * 8]; facesZ; 3d array of +z faces]\
[[block_face](https://github.com)[8 * 8 * 8]; facesNZ; 3d array of -z faces]

if (isMain)\
|&emsp;if (blocks_inside)\
|&emsp;|&emsp;[[block_data](https://github.com); blocks; size of the level and block ids]\
|&emsp;\
|&emsp;if (values_inside)\
|&emsp;|&emsp;[[array](https://github.com)<[block_val](https://github.com)>; values; values of blocks (comment text, number value...)]\
|&emsp;\
|&emsp;if (connections_inside)\
|&emsp;|&emsp;[[array](https://github.com)<[block_con](https://github.com)>; connections; connections between blocks, and between outside and inside if one of the positions is (32769, 32769, 32769)]
## Example