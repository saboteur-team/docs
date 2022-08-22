# EditNodes.pack

`EditNodes.pack` contains a small header and some file data for yet unknown reasons.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: editnodes
  file-extension: pack
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "00ED"
  - id: count
    type: u4
  - id: nodes
    type: editnode
    repeat: expr
    repeat-expr: count
types:
  editnode:
    seq:
      - id: crc
        type: u4
      - id: length
        type: u4
      - id: offset
        type: u4
    instances:
      data:
        pos: offset
        size: length
```
