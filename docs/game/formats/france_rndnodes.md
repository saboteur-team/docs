# France.rndnodes

`France.rndnodes` contains random nodes of some kind. The latest file is empty.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_rndnodes
  file-extension: rndnodes
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "70NR"
  - id: node_count
    type: u4
  - id: nodes
    type: rnd_node
    repeat: expr
    repeat-expr: node_count
types:
  rnd_node:
    seq:
      - id: unk1
        type: u4
      - id: unk2
        type: f4
      - id: unk3
        type: f4
      - id: unk4
        type: f4
      - id: sub_count
        type: u2
      - id: subs
        type: rnd_node_sub
        repeat: expr
        repeat-expr: sub_count
  rnd_node_sub:
    seq:
      - id: unk1
        type: u4
      - id: unk2
        type: u4
```
