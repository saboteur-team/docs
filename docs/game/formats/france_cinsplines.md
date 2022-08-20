# France.cinsplines

`France.cinsplines` contains some cinematic spline data (probably for camera movement).

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: cinematicsplines
  file-extension: cinsplines
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "4LPS"
  - id: count
    type: u4
  - id: data
    type: cinema_spline
    repeat: expr
    repeat-expr: count
types:
  cinema_spline:
    seq:
      - id: name_crc
        type: u4
      - id: distance
        type: f4
      - id: duration
        type: f4
      - id: parent_crc
        type: u4
      - id: object_crc
        type: u4
      - id: pos_dir
        type: u2
      - id: despawn
        type: u2
      - id: pitch
        type: u2
      - id: gap
        type: u2
      - id: node_count
        type: u2
      - id: nodes
        type: cinema_spline_node
        repeat: expr
        repeat-expr: node_count
  cinema_spline_node:
    seq:
      - id: start_pos
        type: f4
      - id: distance
        type: f4
      - id: speed
        type: f4
      - id: start_time
        type: f4
      - id: duration
        type: f4
      - id: pos_x
        type: f4
      - id: pos_y
        type: f4
      - id: pos_z
        type: f4
      - id: quat_x
        type: f4
      - id: quat_y
        type: f4
      - id: quat_z
        type: f4
      - id: quat_s
        type: f4
      - id: float_38
        type: f4
      - id: float_4c
        type: f4
      - id: float_40
        type: f4
      - id: float_48
        type: f4
      - id: float_5c
        type: f4
      - id: float_50
        type: f4
      - id: float_58
        type: f4
      - id: float_6c
        type: f4
      - id: float_60
        type: f4
      - id: float_68
        type: f4
      - id: float_70
        type: f4
      - id: float_74
        type: f4
      - id: sub_count
        type: u2
      - id: float_array_7c
        type: f4
        repeat: expr
        repeat-expr: sub_count
```
