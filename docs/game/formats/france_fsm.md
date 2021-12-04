# France_FSM.info

`France_FSM.info` contains entries for placements long distance visible 3D monuments to be displayed. `(Game Root)\France_FSM.info`.
When monument buildings are too far to render normally, they are replaced with low lod representations that can be seen from very long distances.

The format contains an array of monument entries defining a CRC hash to represent the name of the 3D model to be used and 3D transform information for the position and scale of it on the map.
As an example for the CRC, the entry for the Eifel tower has `0x1E821A55`, which maps to the model name: `FFS_MN_A07_Eifel_Tower`.

The position of each monument is controlled by a 4x4 affine [transformation matrix](https://www.brainvoyager.com/bv/doc/UsersGuide/CoordsAndTransforms/SpatialTransformationMatrices.html), where `m11`, `m22`, and `m33` are the column vector controlling the scale of the monument. This allows adjusting where the monument will be placed in the far scene as well as the size of it.

## [Kaitai](http://kaitai.io/) Formats

### PC

```yaml
meta:
  id: france_fsm
  file-extension: france_fsm
  endian: le
seq:
  - id: file_id
    type: u4
  - id: file_version
    type: u4
  - id: num_sources
    type: u4
  - id: num_objects
    type: u4
  - id: sources
    type: monument_source
    repeat: expr
    repeat-expr: num_sources
  - id: monuments
    type: monument
    repeat: expr
    repeat-expr: num_objects
types:
  monument_source:
    seq:
      - id: file_id
        type: u4
      - id: file_version
        type: u4
      - id: name_crc
        type: u4
  monument:
    seq:
      - id: file_id
        type: u4
      - id: file_version
        type: u4
      - id: entry
        type:
          switch-on: file_version
          cases:
            1: monument_entry_1
            2: monument_entry_2
  monument_entry_1:
    seq:
      - id: mesh_crc
        type: u4
      - id: root_transform
        type: matrix44
  monument_entry_2:
    seq:
      - id: mesh_crc
        type: u4
      - id: min_aabb
        type: vector3
      - id: max_aabb
        type: vector3
      - id: root_transform
        type: matrix44
  vector3:
    seq:
      - id: x
        type: f4
      - id: y
        type: f4
      - id: z
        type: f4
  matrix44:
    seq:
      - id: m11
        type: f4
      - id: m12
        type: f4
      - id: m13
        type: f4
      - id: m14
        type: f4
      - id: m21
        type: f4
      - id: m22
        type: f4
      - id: m23
        type: f4
      - id: m24
        type: f4
      - id: m31
        type: f4
      - id: m32
        type: f4
      - id: m33
        type: f4
      - id: m34
        type: f4
      - id: m41
        type: f4
      - id: m42
        type: f4
      - id: m43
        type: f4
      - id: m44
        type: f4
```

