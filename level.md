# Level
## Format
[uint8; header_0; ]\
[uint8; header_1; 0x18 or 0x19 (has non default background color)]\
[uint8; header_2; always 0x03]\
[[string](https://github.com); name; name of the level]\
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
|&emsp;[[array](https://github.com)<[block_val](https://github.com)>; values; values of blocks (comment text, number value...)]\
else\
|&emsp;the level doesn't have any block values

if ((header_0 & 0b_0000_0001) != 0)\
|&emsp;[[array](https://github.com)<[block_con](https://github.com)>; connections; connections between blocks]\
else\
|&emsp;the level doesn't have any connections
## Example
