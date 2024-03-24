# Connection
## Format
[[vec3i](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/vec3i.md); from; position of the first block or to outside of this block if (32769, 32769, 32769)]\
[[vec3i](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/vec3i.md); to; position of the second block]\
[[vec3i](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/vec3i.md); from_sub; position of the first terminal in sub block space (8 sub blocks per block), relative to the block]\
[[vec3i](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/vec3i.md); to_sub; position of the second terminal in sub block space (8 sub blocks per block), relative to the block]
## Example
from: (0, 0, 0)\
to: (3, 0, 0)\
from_sub: (14, 1, 11)\
to_sub: (0, 1, 11)
```
000000: 00 00 00 00 00 00 03 00 00 00 00 00 0E 00 01 00 | ................ |
000010: 0B 00 00 00 01 00 0B 00                         | ........         |
```