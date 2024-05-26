# Block segment
## Info
Segment = 8\*8\*8 part of the block
## Format
### Header
|Type|Name|Description|
|:--|:--|:--|
|[Header0](#header0) and [Collider](#collider)|header0, collider|header and collider in 1 byte|
|uint8|header1||

#### Block type
if header1 == 0x00 {
|Name|Value|
|:--|:--|
|block_type|[BlockType](#block-type).NonMainSegment|

|Type|Description|Condition|
|:--|:--|:--|
|uint8|not neeeded|(collider & 0b_0010_0000) != 0|

}

if header1 == 0x08 {
|Name|Value|
|:--|:--|
|block_type|[BlockType](#block-type).Normal|

}

if header1 == 0x10 {
|Name|Value|
|:--|:--|
|block_type|[BlockType](#block-type).NonMainSegment|

|Type|Description|Condition|
|:--|:--|:--|
|uint8|not neeeded||
|uint8|not neeeded|(collider & 0b_0010_0000) != 0|

}

if header1 == 0x18 {
|Type|Name|
|:--|:--|
|uint8|header2|

|Name|Value|Condition|
|:--|:--|:--|
|block_type|[BlockType](#block-type).Physics|header2 == 0x01|
|block_type|[BlockType](#block-type).Script|header2 == 0x02|

}
#### Rest of header
|Name|Value|
|:--|:--|
|isMain|block_type != NonMainSegment|

if isMain {
|Type|Name|Description|Condition|
|:--|:--|:--|:--|
|[string](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/string.md)|name|name of this custom block||
|uint8|collider.byte2|additional byte deciding if the collider is none or sphere|(collider & 0b_0010_0000) != 0|
|uint8||not needed|block_type == Script|

}
### Data
|Type|Name|Description|Condition|
|:--|:--|:--|:--|
|uint16|id|id of this block, if condition is false, the id is determined by the order this segment is loaded in, [id of the first segment](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/README.md#blocks-added)|!isMain \|\| (isMain && header0 has-flag MultiSegment)|
|[vec3i](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/vec3i.md)|pos|position of this segment relative to main segment|!isMain \|\| (isMain && header0 has-flag MultiSegment)|
|[block_face](#block-face)[8 * 8 * 8]|facesX|3d array of +x faces||
|[block_face](#block-face)[8 * 8 * 8]|facesNX|3d array of -x faces||
|[block_face](#block-face)[8 * 8 * 8]|facesY|3d array of +y faces||
|[block_face](#block-face)[8 * 8 * 8]|facesNY|3d array of -y faces||
|[block_face](#block-face)[8 * 8 * 8]|facesZ|3d array of +z faces||
|[block_face](#block-face)[8 * 8 * 8]|facesNZ|3d array of -z faces||
|[block_data](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block_data.md)|blocks|size of the level and block ids|isMain && header0 has-flag BlocksInside|
|[array](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/array.md)<[block_val](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block_val.md)>|values|values of blocks (comment-text, number-value...)|isMain && header0 has-flag ValuesInside|
|[array](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/array.md)<[block_con](https://github.com/BitcoderCZ/Fancade_Game_Format/blob/main/block_con.md)>|connections|connections between blocks (and outside this custom block if pos is (32769, 32769, 32769))|isMain && header0 has-flag ConnectionsInside|
## Types
### Header0
flags enum Header0 : uint8
|Name|Value|Description|
|:--|:--|:--|
|ConnectionsInside|0b_0000_0001|if the block has connections inside it (also includes connections from outside to inside)|
|ValuesInside|0b_0000_0010|if this block contains block values inside it|
|BlocksInside|0b_0000_0100|if this block contains blocks inside it|
|MultiSegment|0b_0001_0000|if this block is made from multiple sections|
|Uneditable|0b_0100_0000||
|Unknown|0b_1000_0000||
### Collider
enum Collider : uint8
|Name|Value|Condition|
|:--|:--|:--|
|Box|0b_0000_1000||
|None|0b_0010_1000|byte2 == 0x00|
|Sphere|0b_0010_1000|byte2 == 0x02|
### Block type
enum BlockType
|Name|
|:--|
|Normal|
|Physics|
|Script|
|NonMainSegment|
### Block face
uint8
|Bits|Name|Description|
|:--|:--|:--|
|1-6|color|color of this face (0b_0011_1111)|
|7-8|attribs|if this face is sticky/has "lego" (0b_1100_0000)|