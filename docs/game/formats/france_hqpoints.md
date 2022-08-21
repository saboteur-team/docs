# France.hqpoints

`France.hqpoints` contains HQ related data.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_hqpoints
  file-extension: hqpoints
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "60PH"
  - id: count
    type: u4
  - id: hqs
    type:  hq_point
    repeat: expr
    repeat-expr: count
types:
  hq_point:
    seq:
      - id: name_crc
        type: u4
      - id: game_text_id_crc
        type: u4
      - id: strlen1
        type: u2
      - id: interior_script_name1
        type: strz
        size: strlen1 > 128 ? 128 : strlen1
      - id: strlen2
        type: u2
      - id: interior_script_name2
        type: strz
        size: strlen2 > 128 ? 128 : strlen2
      - id: matrix
        type: f4
        repeat: expr
        repeat-expr: 12
```
