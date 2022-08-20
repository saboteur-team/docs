# France.defen

`France.defen` contains crcs for edit nodes.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: defen
  file-extension: defen
  endian: le
  encoding: UTF-8
seq:
  - id: count
    type: u4
  - id: crcs
    type: u4
    repeat: expr
    repeat-expr: count
```
