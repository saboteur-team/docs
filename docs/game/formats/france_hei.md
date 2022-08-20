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
  - id: unk_40
    type: u4
  - id: unk_44
    type: u4
  - id: unk_48
    type: f4
  - id: unk_4c
    type: f4
  - id: unk_50
    type: f4
  - id: unk_54
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
      - id: unk_0
        type: u4
      - id: unk_4
        type: u4
      - id: unk_8
        type: f4
      - id: unk_16
        type: f4
      - id: unk_20
        type: f4
      - id: unk_24
        type: f4
```
