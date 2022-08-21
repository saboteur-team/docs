# France.waterflow

`France.waterflow` contains water flow data.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_waterflow
  file-extension: france_waterflow
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "70FW"
  - id: count
    type: u4
  - id: water_flows
    type: water_flow
    repeat: expr
    repeat-expr: count
types:
  water_flow:
    seq:
      - id: name_crc
        type: u4
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
      - id: unk8
        type: f4
```
