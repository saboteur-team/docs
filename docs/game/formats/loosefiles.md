# LooseFiles

## Detail

The [*France\looseFiles_BinPC.pack*](../filesystem.md#looseFiles) file is a very simple container of files. The idea with this could have been to bundle up a few loose files for easier reading. There are multiple loose files still in the game folder, so the reason why this file doesn't contain all of them is not known.

## Content

* Cinematics/Conversations/Conversations.cnvpack
* Cinematics/Cinematics.cinpack
* France/EditNodes/EditNodes.pack
* France.map
* France.shaders
* GameTemplates.wsd
* global.map

## Format

|Offset|Size|Type|Name|Comment|
|-|-|-|-|-|
|0|4|[Crc](../crc.md)|Unknown|Unknown [Crc](../crc.md).|
|4|4|u32|Size|The size of the file|
|8|120|string|Name|The nullterminated name of the file.|
|128|Varying|byte[]|Data|The bytes of the file|

The next entry comes after the first's data array, with the same format,
but the start the header is aligned to 0x10 byte boundary. This format has no specific file entry count value, fully reading must be while the input file is not over.

Reading a specific file can be done with reading the header, checking for the file name, then skipping the data of the file and the byte boundary and checking the next header.
