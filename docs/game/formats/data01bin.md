# data01.bin

`data01.bin` contains a random looking array of bytes. Seems unused, except the first 12 bytes being XOR checked when the UI loads.

|Offset|Size|Type|Name|Description|
|-|-|-|-|-|
|0|4|u32|Offset|The offset to read the data from (should be 0 on PC)|
|4|4|u32|XOR base|The base value being XORed (should be 0 on PC)|
|Offset * 4 + 8|4|u32|XOR check|The value being checked by the XOR (should be 0x21B87FA8 on PC)|

If the [XOR check] value equals [XOR base] ^ 0x1557F8D2 then some knife throatcat steah kill stuff is being set up.

Other data in the file seems unused.

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: data01
  file-extension: bin
  endian: le
seq:
  - id: offset
    type: u4
  - id: xor_base
    type: u4
instances:
  xor_check:
    pos: offset * 4 + 8
    type: u4
```
