# Game
## Format
[uint16; format_version; ;]\
[[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md); game_name; ;]\
[[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md); game_author; ;]\
[[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md); game_description; ;]\
[uint8 ; ; unknown;]\
[uint8 ; ; unknown, 0x02;]\
[uint8; levels_and_blocks; number of levels + numbe of custom blocks]\
[uint8; ; unknown;]\
[([level](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/level.md) or [block](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block.md))[levels_and_blocks]; ; array of levels and/or blocks]
## Example