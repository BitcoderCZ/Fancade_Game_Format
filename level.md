# Level
## Format
### Header
|Type|Name|Description|Condition|
|:--|:--|:--|:--|
|[Header0](#header0)|header0|||
|[Header1](#header1)|header1|||
|uint8|header2|0x03||
|[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md)|name|name of this level||
|uint8|bg_col|background color of this level|header1 has-flag NonDefaultBGColor|
### Data
|Type|Name|Description|Condition|
|:--|:--|:--|:--|
|uint8||unknown|header0 has-flag Unknown|
|[block_data](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block_data.md)|blocks|size of the level and block ids|header0 has-flag HasBlocks|
|[array](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/array.md)<[block_val](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block_val.md)>|values|values of blocks (comment-text, number-value...)|header0 has-flag HasBlockValues|
|[array](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/array.md)<[block_con](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block_con.md)>|connections|connections between blocks|header0 has-flag HasConnections|
## Types
### Header0
flags enum Header0 : uint8
|Name|Value|
|:--|:--|
|HasConnections|0b_0000_0001|
|HasBlockValues|0b_0000_0010|
|HasBlocks|0b_0000_0100|
|Unknown|0b_0010_0000|
### Header1
flags enum Header1 : uint8
|Name|Value|
|:--|:--|
|{Base}|0x18|
|NonDefaulBGtColor|0x01|
