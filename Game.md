# Game
### Format
[uint16; format_version; ;]\
[[string](https://github.com); game_name; ;]\
[[string](https://github.com); game_author; ;]\
[[string](https://github.com); game_description; ;]\
[uint8 ; ; unknown;]\
[uint8 ; ; unknown, 0x02;]\
[uint8; levels_and_blocks; number of levels + numbe of custom blocks]\
[uint8; ; unknown;]\
[([level](https://github.com) or [block](https://github.com))[levels_and_blocks]; ; array of levels and/or blocks]
### Example