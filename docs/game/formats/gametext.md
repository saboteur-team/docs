# GameText.dlg

`GameText.dlg` is file which contains various text strings for cutscenes, help texts etc. On PC version, you can find this file in `The Saboteur\Cinematics\Dialog\(Language)\GameText.dlg`.

The format is quite easy and can be find out even without reverse engineering (that's how is the current Kaitai script made, but there are some things missing. Check [TODO](#todo)).

Some notes:

- On Xbox version (2008 beta build) all integers are in big endian, on PC version they are little endian.
- The tag type is not string but integer, so on PC it's `TXTD`, on Xbox it's `DTXT`

## Kaitai script for PC Version's `GameText.dlg`

```yaml
meta:
  id: dlg
  title: Saboteur Dialog File
  file-extension: dlg
  endian: le
  
seq:
  - id: header
    type: header
  - id: entries
    type: entry
    repeat: eos
    
types:
  header:
    seq:
      - id: version
        type: u4
      - id: entries_count
        type: u4
      - id: unknown2
        size: 4
  entry:
    seq:
      - id: tag_type
        type: str
        encoding: ASCII
        size: 4
      - id: body
        type:
          switch-on: tag_type
          cases:
            '"TXTD"': dtxt_entry
  dtxt_entry:
    seq:
      - id: hash
        size: 4
      - id: key_size
        type: u2
      - id: key
        type: str
        encoding: ASCII
        size: key_size
      - id: value_size
        type: u2
      - id: value
        type: str
        encoding: UTF-16LE
        size: value_size*2
```

## Kaitai script for Xbox 2008 beta Version's `GameText.dlg`

```yaml
meta:
  id: dlg
  title: Saboteur Dialog File
  file-extension: dlg
  endian: be
  
seq:
  - id: header
    type: header
  - id: entries
    type: entry
    repeat: eos
    
types:
  header:
    seq:
      - id: version
        type: u4
      - id: entries_count
        type: u4
      - id: unknown2
        size: 4
  entry:
    seq:
      - id: tag_type
        type: str
        encoding: ASCII
        size: 4
      - id: body
        type:
          switch-on: tag_type
          cases:
            '"DTXT"': dtxt_entry
  dtxt_entry:
    seq:
      - id: hash
        size: 4
      - id: key_size
        type: u2
      - id: key
        type: str
        encoding: ASCII
        size: key_size
      - id: value_size
        type: u2
      - id: value
        type: str
        encoding: ASCII
        size: value_size
```

## TODO

- In PC Release version, there are multiple `CEND` (`DNEC`) tags, and mostly between them are 8 bytes of something (and in one case 600+ bytes (offset `0xD988D` on PC Release English GameText.dlg)). It seems to have some structure, although it needs to be Reversed to find out.
- Hash is in weird format, also, it's not 100% confirmed if it's hash or ID (String `Return contraband` have same hash on PC Release and on Xbox 2008 beta version `b05ad4a`)
- Find out purposes of unknown properties