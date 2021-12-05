# France_FST.info

The `France_FST.info` file contains data representing how the far scene terrain should be rendered, located at `(Game Root)\France_FST.info`.
When areas of the terrain are too far for the near scene models to be shown, the terrain is still visible in the far scene as a low LOD variation, so that distant hills
and mountains can be seen from anywhere in the game.

The format contains level of detail variables regarding number of chunks and vertices. It defines two CRCs, one for the map data used and one for the color data of the terrain.
The data map CRC is set to `FSTDataMap_NC`, and has an alternative CRC that can be selected (`0xC6FF3ED7`, referring to "FSTDataMap_NC_High"). This means there is a variation of the map data
for both High Will To Fight and No Color. Additionally the color map CRC is similar and has the value `FSTColorMap`, but has an alternative CRC (`0xB31F3E34`, referring to "FSTColorMap_High").

Additionally, the positioning of the terrain is determined by a pair of vector3 coordinates that define a cube. The pairing defines the min and max positions accordingly for all 3 axes.
Unlike the FSM format, the FST format only defines a single object.

## [Kaitai](http://kaitai.io/) Formats

### PC

```yaml
meta:
  id: france_fst
  file-extension: info
  endian: le
seq:
  - id: file_id
    type: u4
  - id: file_version
    type: u4
  - id: file_entry
    type: file_entry
types:
  file_entry:
    seq:
      - id: num_chunks
        type: u4
      - id: num_vertices
        type: u4
      - id: data_map_crc
        type: u4
      - id: color_map_crc
        type: u4
      - id: world_aabb_min
        type: vector3
      - id: world_aabb_max
        type: vector3
  vector3:
    seq:
      - id: x
        type: f4
      - id: y
        type: f4
      - id: z
        type: f4
```

