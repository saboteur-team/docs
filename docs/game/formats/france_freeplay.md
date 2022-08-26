# France.freeplay

`France.freeplay` contains freeplay nodes on the map.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_freeplay
  file-extension: freeplay
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "40PF"
  - id: count
    type: u4
  - id: total_count_subitems
    type: u4
  - id: data
    type: sub_type_1
    repeat: expr
    repeat-expr: count
types:
  sub_type_1:
    seq:
      - id: unk_crc1
        type: u4
      - id: unk_crc2
        type: u4
      - id: unk_crc3
        type: u4
      - id: unk4
        type: u4
      - id: pos_x
        type: f4
      - id: pos_y
        type: f4
      - id: pos_z
        type: f4
      - id: count
        type: u4
      - id: unk_crcs
        type: u4
        repeat: expr
        repeat-expr: count
```
