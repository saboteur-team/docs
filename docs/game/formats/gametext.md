# GameText.dlg

`GameText.dlg` is file which contains various text strings for cutscenes, help texts and etc... On PC version, you can find this file in `(Game Root)\Cinematics\Dialog\(Language)\GameText.dlg`.

## [Kaitai](http://kaitai.io/) Formats

### PC

```yaml
meta:
  id: saboteur_dialog_text
  title: Saboteur Dialog Text File
  file-extension: dlg
  endian: le
seq:
  - id: version
    type: u4
  - id: base_entries
    type: entry_array
  - id: sub_entry_count
    type: u4
  - id: sub_entry_arrays
    type: sub_entry
    repeat: expr
    repeat-expr: sub_entry_count
  - id: sub_arrays
    type: entry_array
    repeat: expr
    repeat-expr: sub_entry_count
types:
  entry_array:
    seq:
      - id: entry_count
        type: u4
      - id: total_char_count
        type: u4
      - id: entries
        type: dtxt_entry
        repeat: expr
        repeat-expr: entry_count
      - id: end
        contents: "DNEC"
  dtxt_entry:
    seq:
      - id: tag
        contents: "TXTD"
      - id: id
        type: u4
      - id: voice_over_key_size
        type: u2
      - id: voice_over
        type: str
        encoding: UTF-8
        size: voice_over_key_size
      - id: text_size
        type: u2
      - id: text
        type: str
        encoding: UTF-16
        size: text_size * 2
  sub_entry:
    seq:
      - id: id
        type: u4
      - id: offset
        type: u4
```

### Xbox 360 2008 beta Version

Note: All integers are in big endian, on PC version they are little endian.

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
