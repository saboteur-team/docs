# France.gpsgraph

`France.gpsgraph` contains some GPS graphs.

To be extended!

## [Kaitai](http://kaitai.io/) Format

Notice: uncomplete structure and it's in BIG ENDIAN!

### PC

```yaml
meta:
  id: france_gpsgraph
  file-extension: gpsgraph
  endian: be
  encoding: UTF-8
seq:
  - id: fourcc
    type: str
    size: 4
  - id: data_0
    type: gps_graph_0
    if: fourcc=="GPS0"
  - id: data_1
    type: gps_graph_1
    if: fourcc=="GPS1"
types:
  gps_graph_0:
    seq:
      - id: unk1
        type: u2
      - id: unk2
        type: u2
      #TODO
  gps_graph_1:
    seq:
      - id: unk_count1
        type: u2
      - id: unk2
        type: u2
      - id: unk_count3
        type: u2
      - id: sub1s
        type: gps_graph_1_sub1
        repeat: expr
        repeat-expr: unk_count1
      - id: sub2s
        type: gps_graph_1_sub2
        repeat: expr
        repeat-expr: unk_count3
      - id: unk4
        type: u2
      - id: unk5
        type: u2
      - id: unk6
        type: u2
      - id: unk7
        type: u2
      - id: unk8
        type: u2
      - id: unk9
        type: u2
      - id: data
        type: u2
        repeat: expr
        repeat-expr: unk4 * unk5
  gps_graph_1_sub1:
    seq:
      - id: unk1
        type: u2
      - id: unk2
        type: u2
      - id: unk_count3
        type: u1
      - id: data
        type: u2
        repeat: expr
        repeat-expr: unk_count3
  gps_graph_1_sub2:
    seq:
      - id: unkstring
        type: strz
      - id: unk_count
        type: u2
      - id: data
        type: u2
        repeat: expr
        repeat-expr: unk_count
```
