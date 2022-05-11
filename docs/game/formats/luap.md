# LuaScripts.luap

`LuaScripts.luap` contains compiled lua scripts containing the game logic. On the PC version, you can find this file at `(Game Root)\LuaScripts.luap`.

## [Kaitai](http://kaitai.io/) Formats

### PC

```yaml
meta:
  id: lua_package
  file-extension: luap
  endian: le
seq:
  - id: count
    type: u4
  - id: entries
    type: luac_entry
    repeat: expr
    repeat-expr: count
types:
  luac_entry:
    seq:
    - id: path_crc
      type: u4
    - id: name_crc
      type: u4
    - id: offset
      type: u4
    - id: size
      type: u4
    - id: size2
      type: u4
    - id: is_module
      type: u1
```
