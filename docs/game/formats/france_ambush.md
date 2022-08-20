# France.ambush

`France.ambush` contains some AI will to fight data.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: ambush
  file-extension: ambush
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "I0LA"
  - id: count
    type: u4
  - id: data
    type: ambush_data
    repeat: expr
    repeat-expr: count
types:
  ambush_data:
    seq:
      - id: id1
        type: u4
      - id: id2
        type: u4
      - id: unk1
        type: u4
      - id: unk2
        type: u4
      - id: pos_x
        type: f4
      - id: pos_y
        type: f4
      - id: pos_z
        type: f4
      - id: unk_float1
        type: f4
      - id: unk_float2
        type: f4
      - id: unk_float3
        type: f4
      - id: unk_float4
        type: f4
      - id: unk_float5
        type: f4
      - id: unk_float6
        type: f4
      - id: unk_float7
        type: f4
      - id: unk_float8
        type: f4
      - id: unk_float9
        type: f4
```
