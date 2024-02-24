# Fancade Game Format
value - [value type; value name or variable to assign to (e.g. [collider](https://github.com).value); info]\
variable - (optional expression to assign to the variable) \#[variable type; variable name; info]\
## File Format
[uint8; ; ]\
[uint8; ; ]\
[uint8; type; ]\
if (type == 0x01)\
|&emsp;Text format, didn't really look into this, because basically any game that isn't blank is gonna be compressed\
else\
|&emsp;GZip compressed, decompression only seems to work with GZipStream from .NET framework (maybe .NET), specifically ZLib, managed doesn't work. This is because the gzip header is missing, so adding it should make this work with other decompressors\
|&emsp;When writing, do it like this:\
|&emsp;[uint8; header0; 0x78]\
|&emsp;[uint8; header1; 0x01]\
|&emsp;Compressed bytes from index 10, length: compressedBytes.length - 18