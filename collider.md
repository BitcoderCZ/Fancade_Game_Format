# Collider
### Format
\#[uint8; value; block.header0 & 0b_0010_1000]\
\#[uint8; value2; determines if collider is none or sphere]\

if (value == 0x08)\
|&emsp;collider is box\
else if (value == 0x28)\
|&emsp;if (value2 == 0x00)\
|&emsp;|&emsp;collider is none\
|&emsp;else if (value2 == 0x02\
|&emsp;|&emsp;collider is sphere\
|&emsp;else\
|&emsp;|&emsp;invalid collider\
else\
|&emsp;invalid collider
### Example