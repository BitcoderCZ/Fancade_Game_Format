# Block face
### Format
[uint8; value; ]\
|&emsp;(value & 0b_0011_1111)&emsp;\#[uint8; color; color of this face, 0 if there isn't a face]\
|&emsp;(value & 0b_1100_0000)&emsp;\#[uint8; attribs; if this face is sticky/has "lego"]