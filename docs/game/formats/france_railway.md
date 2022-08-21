# France.railway

`France.railway` contains railway paths.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_railway
  file-extension: railway
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "6IAR"
  - id: railway_count
    type: u4
  - id: railways
    type: railway_spline
    repeat: expr
    repeat-expr: railway_count
types:
  railway_spline:
    seq:
      - id: name_len
        type: u4
      - id: name
        type: strz
        size: name_len
      - id: name_crc
        type: u4
      - id: distance
        type: f4
      - id: node_count
        type: u2
      - id: nodes
        type: railway_spline_node
        repeat: expr
        repeat-expr: node_count
  railway_spline_node:
    seq:
      - id: name_len
        type: u4
      - id: name
        type: strz
        size: name_len
      - id: name_crc
        type: u4
      - id: start_pos
        type: f4
      - id: distance
        type: f4
      - id: pos_x
        type: f4
      - id: pos_y
        type: f4
      - id: pos_z
        type: f4
      - id: influence_x
        type: f4
      - id: influence_y
        type: f4
      - id: influence_z
        type: f4
      - id: quat_x
        type: f4
      - id: quat_y
        type: f4
      - id: quat_z
        type: f4
      - id: quat_s
        type: f4
      - id: is_start
        type: u2
      - id: is_end
        type: u2
      - id: is_station
        type: u2
      - id: max_speed
        type: f4
      - id: station_wait_time
        type: f4
      - id: train_list_blueprint_crc
        type: u4
      - id: attachment_count
        type: u4
      - id: attachments
        type: railway_spline_node_attachment
        repeat: expr
        repeat-expr: attachment_count
  railway_spline_node_attachment:
    seq:
      - id: spline_name_crc
        type: u4
      - id: node_name_crc
        type: u4
```
