# France.map

`France.map` contains information about the map.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_map
  file-extension: map
  endian: le
  encoding: UTF-8
seq:
  - id: magic
    contents: "6PAM"
  - id: level_name
    type: strz
  - id: num_palettes
    type: u4
  - id: da84
    type: u4
  - id: debug_starting_position_count
    type: u4
  - id: debug_starting_position_unk
    type: u4
    if: debug_starting_position_count > 0
  - id: debug_starting_positions
    type: debug_starting_position
    repeat: expr
    repeat-expr: debug_starting_position_count
  - id: extent_low
    type: extent
  - id: extent_med
    type: extent
  - id: extent_high
    type: extent
  - id: grid_size_low
    type: grid_size
  - id: grid_size_med
    type: grid_size
  - id: grid_size_high
    type: grid_size
  - id: palettes
    type: block
    repeat: expr
    repeat-expr: num_palettes
  - id: num_interiors
    type: u4
  - id: interiors
    type: block
    repeat: expr
    repeat-expr: num_interiors
  - id: num_cinematics
    type: u4
  - id: cinematics
    type: block
    repeat: expr
    repeat-expr: num_cinematics
types:
  debug_starting_position:
    seq:
      - id: name_length
        type: u4
      - id: name
        type: strz
      - id: str_length
        type: u4
      - id: str
        type: str
        size: str_length
      - id: position
        type: vector3
      - id: x_axis
        type: vector3
      - id: y_axis
        type: vector3
      - id: z_axis
        type: vector3
      - id: script_length
        type: u4
      - id: script_name
        type: str
        size: script_length
  extent:
    seq:
      - id: min
        type: vector3
      - id: max
        type: vector3
  grid_size:
    seq:
      - id: x
        type: u2
      - id: z
        type: u2
  block:
    seq:
      - id: id
        type: u4
      - id: file_name_length
        type: u2
      - id: file_name
        type: str
        size: file_name_length
        if: file_name_length > 0
      - id: extents
        type: extent
      - id: unk_short
        type: u2
      - id: index
        type: u2
      - id: block_data
        type: block_data
        if: index == 2
  block_data:
    seq:
      - id: num_textures
        type: u4
      - id: textures
        type: texture
        repeat: expr
        repeat-expr: num_textures
      - id: num_textures2
        type: u4
      - id: textures2
        type: texture
        repeat: expr
        repeat-expr: num_textures2
      - id: unk
        type: u4
      - id: entry_counts
        type: u4
        repeat: expr
        repeat-expr: 9
      - id: num_unk_2
        type: u4
      - id: unk2s
        type: u4
        repeat: expr
        repeat-expr: num_unk_2
      - id: num_palettes
        type: u4
      - id: palettes
        type: u4
        repeat: expr
        repeat-expr: num_palettes
      - id: num_fences
        type: u4
      - id: fences
        type: fence
        repeat: expr
        repeat-expr: num_fences
  fence:
    seq:
      - id: crc
        type: u4
      - id: value_count
        type: u4
      - id: values
        type: u4
        repeat: expr
        repeat-expr: value_count
  texture:
    seq:
      - id: crc
        type: u4
      - id: size
        type: u4
  vector3:
    seq:
      - id: x
        type: f4
      - id: y
        type: f4
      - id: z
        type: f4
```
