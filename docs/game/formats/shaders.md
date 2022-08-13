# France.shaders

`France.shaders` contains compiled shaders.

To be extended!.

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_shaders
  file-extension: shaders
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "RDHS"
  - id: pixel_shader_count
    type: u4
  - id: pixel_shaders
    type: pixel_shader
    repeat: expr
    repeat-expr: pixel_shader_count
  - id: vertex_shader_count
    type: u4
  - id: vertex_shaders
    type: vertex_shader
    repeat: expr
    repeat-expr: vertex_shader_count
  - id: unk_string
    type: str
    size: 258
types:
  pixel_shader:
    seq:
      - id: fourcc
        contents: "DHSP"
      - id: data
        type: shader_shared
  vertex_shader:
    seq:
      - id: fourcc
        size: 4
        contents: "DHSV"
      - id: data
        type: shader_shared
  shader_shared:
    seq:
      - id: index
        type: u4
      - id: has_data
        type: u4
      - id: data
        type: shader_data
        if: has_data != 0
  shader_data:
    seq:
      - id: shader_count
        type: u4
      - id: id
        type: u4
      - id: empty_chunk
        type: shader_chunk
        if: shader_count == 0
      - id: shaders
        type: shader_chunk
        repeat: expr
        repeat-expr: shader_count
  shader_chunk:
    seq:
      - id: shader_size
        type: u4
      - id: shader_data
        size: shader_size
      - id: config_param_count
        type: u4
      - id: config_params
        type: shader_config_param
        repeat: expr
        repeat-expr: config_param_count
  shader_config_param:
    seq:
      - id: name_size
        type: u4
      - id: name
        type: str
        size: name_size
      - id: unk1
        type: u4
```
