# France.waterctrl

`France.waterctrl` contains water control points.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_waterctrl
  file-extension: waterctrl
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "70CW"
  - id: count
    type: u4
  - id: controls
    type: water_control
    repeat: expr
    repeat-expr: count
types:
  water_control:
    seq:
      - id: name_crc
        type: u4
      - id: pos_x
        type: f4
      - id: pos_y
        type: f4
      - id: pos_z
        type: f4
      - id: unk_size
        type: u4
      - id: unk_data
        size: unk_size
        doc: blua structure, but it's always empty
```
