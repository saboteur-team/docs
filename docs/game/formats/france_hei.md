# France.hei

`France.hei` contains most-likely heightmap data.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: hei5
  file-extension: hei
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "5IEH"
  - id: count
    type: u4
  - id: max_grid_x
    type: u4
  - id: max_grid_z
    type: u4
  - id: grid_size
    type: f4
  - id: top_left_x
    type: f4
  - id: top_left_y
    type: f4
  - id: top_left_z
    type: f4
  - id: content
    type: hei1
    repeat: expr
    repeat-expr: count
types:
  hei1:
    seq:
      - id: fourcc
        contents: "1IEH"
      - id: unk_32
        type: u4
      - id: unk_36
        type: u4
      - id: unk_40
        type: f4
      - id: unk_44
        type: f4
      - id: unk_48
        size: unk_32 * unk_36
      - id: start_pos_x
        type: u4
      - id: start_pos_y
        type: u4
      - id: start_pos_z
        type: f4
      - id: end_pos_x
        type: f4
      - id: end_pos_y
        type: f4
      - id: end_pos_z
        type: f4
```
