# Block Data
## Format
[vec3i; size; the dimentions of the block data/level]\
[uint16[size.x, size.y, size.z]; blocks; ids of the blocks, 1 -> (1, 0, 0), size.x -> (0, 1, 0), size.x * size.y -> (0, 0, 1)]
## Example