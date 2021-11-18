# Megapack / Kilopack

## Detail

The megapack file is just an archive file for storing different kind of assets. A megapack (or kilopack) stores pack files inside them. Different megapacks store different kind and amount of data.

The data stored in megapacks can be:

* Models
    * Meshes
    * Physics data
    * Textures
    * TODO: more

The megapack file format is a simple one: all the pack files are packed together inside a big file with a header specifying (for each file) the name, where they start and how big they are.

## Formats

### Entry Header

|Offset|Size|Type|Name|Description|
|-|-|-|-|-|
|0|4|[Crc](../crc.md)|Id|File name's Crc|
|4|4|[Crc](../crc.md)|Path|File path's Crc|
|8|4|u32|Size|File size|
|12|8|u64|Offset|File offset inside the megapack|

### File

|Offset|Size|Type|Name|Description|
|-|-|-|-|-|
|0|4|FourCC|Magic|The file's magic number "MP00"|
|4|4|u32|File count|The number of embedded pack files|
|8|20|[Entry header](#entry-header)[]|File entries|The header entries for the pack files|
|8 + 20*Count|8|[[Crc](../crc.md), [Crc](../crc.md)]|Unk ids|Unknown array containing [Crc](../crc.md) pairs|
|8 + 28*Count|Varying|byte[]|File data|Offset is padded to 0x800 byte boundary|

[Kaitai](http://kaitai.io/) structure definition:

```yaml
meta:
  id: megapack
  file-extension:
    - megapack
    - kilopack
  endian: le
seq:
  - id: magic
    contents: "00PM"
  - id: file_entry_count
    type: u4
  - id: file_entries
    type: file_entry
    repeat: expr
    repeat-expr: file_entry_count
  - id: crc_pairs
    type: crc_pair
    repeat: expr
    repeat-expr: file_entry_count
types:
  file_entry:
    seq:
      - id: crc
        type: u4
      - id: unk_crc
        type: u4
      - id: size
        type: u4
      - id: offset
        type: u8
    instances:
      data:
        pos: offset
        size: size
  crc_pair:
    seq:
      - id: crc1
        type: u4
      - id: crc2
        type: u4
```
