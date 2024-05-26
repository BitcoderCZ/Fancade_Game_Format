# Block Data
## Format
|Type|Name|Description|
|:--|:--|:--|
|[vec3i](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/vec3i.md)|size|the dimentions of the block data/level|
|uint16[size.x, size.y, size.z]|blocks|ids of the blocks, 1 -> (1, 0, 0), size.x -> (0, 1, 0), size.x * size.y -> (0, 0, 1)|