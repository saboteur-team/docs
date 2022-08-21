# France.spore

`France.spore` contains human spawning data. MIGHT BE UNUSED!

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_spore
  file-extension: spore
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "I0SS"
  - id: spore_count
    type: u4
  - id: spores
    type: spore
    repeat: expr
    repeat-expr: spore_count
types:
  spore:
    seq:
      - id: name_crc
        type: u4
      - id: unk1_crc
        type: u4
      - id: unk2_crc
        type: u4
      - id: unk3
        type: f4
      - id: unk4
        type: f4
      - id: unk5
        type: f4
      - id: unk6
        type: f4
      - id: unk7
        type: f4
      - id: unk8
        type: f4
      - id: unk9
        type: f4
      - id: unk10
        type: f4
      - id: unk11
        type: f4
      - id: unk12
        type: f4
      - id: unk13
        type: f4
      - id: unk14
        type: f4
      - id: unk15
        type: u4
      - id: unk16
        type: u4
      - id: fields
        type: field
        repeat: expr
        repeat-expr: unk16
  field:
    seq:
      - id: name_crc
        type: u4
      - id: size
        type: u4
      - id: data
        size: size
```
