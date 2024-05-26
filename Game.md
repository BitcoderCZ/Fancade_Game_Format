# Game
## Format
|Type|Name|Description|
|:--|:--|:--|
|uint16|palette_version|from 27 (1.0) to currently 31 (1.14.5), determines how many default blocks there are|
|[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md)|name||
|[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md)|author||
|[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md)|description||
|int8|block_id_offset|how much to subtract from a custom block id to get 512|
|uint8||unknow function, 2 if block_id_offset is positive, 1 if block_id_offset is negative|
|uint16|numb_objects|number of levels + number of custom block segments|
|[level](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/level.md)[numb_objects - segments.Length]|levels||
|[segments](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block_segment.md)[numb_objects - levels.Length]|segments|custom block segments|