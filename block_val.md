# Block Value
## Format
|Type|Name|Description|Condition|
|:--|:--|:--|:--|
|uint8|index|in case the block has multiple values|
|uint8|type|type of the value|
|[vec3i](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/vec3i.md)|pos|position of the main segment of the block this value belongs to|
|uint8|value||type == 1|
|uint16|value||type == 2|
|float|value||type == 4|
|vec3f|value|vector or rotation|type == 5|
|[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md)|value|for terminals names, type describes the terminal type and if it is in/out|else|
## Example
index: 0\
type: 5\
pos: (0, 0, 0)\
value: (90.0, 0.0, 0.0)
```
000000: 00 05 00 00 00 00 00 00 00 00 B4 42 00 00 00 00 | ...........B.... |
000010: 00 00 00 00                                     | ....             |
```