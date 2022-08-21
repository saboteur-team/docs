# France.paths

`France.paths` contains some AI paths. Could be patrolling NPCs paths?

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_paths
  file-extension: paths
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "6HTP"
  - id: path_count
    type: u4
  - id: paths
    type: scripted_path
    repeat: expr
    repeat-expr: path_count
types:
  scripted_path:
    seq:
      - id: name_crc
        type: u4
      - id: node_count
        type: u4
      - id: nodes
        type: scripted_path_node
        repeat: expr
        repeat-expr: node_count
      - id: unk_count
        type: u4
      - id: unks
        type: u4
        repeat: expr
        repeat-expr: unk_count
      - id: unkshort
        type: u2
  scripted_path_node:
    seq:
      - id: pos_x
        type: f4
      - id: pos_y
        type: f4
      - id: pos_z
        type: f4
      - id: rotation
        type: f4
      - id: unk1
        type: f4
      - id: unk2
        type: f4
      - id: min_pause_time
        type: f4
```
