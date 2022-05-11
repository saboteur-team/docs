# LuaScripts.luap

`LuaScripts.luap` contains compiled lua scripts containing the game logic. On the PC version, you can find this file at `(Game Root)\LuaScripts.luap`.

The path and name Crcs are easy to calculate. Let's say the file to be included in the package is: `Scripts\Experimental\AttackAction.lua`. The compiled version of it is at the same path, but with the extension `luac`. To calculate the path Crc, the prefix `d:\` must be prepended to that path. So the path Crc will be calculated from: `d:\Scripts\Experimental\AttackAction.luac`.

The name Crc is easier, that is calculated from the file name without extension. In the above example: `AttackAction`.

Size and size2 seems to be the same, no idea why is there two sizes currently.

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
