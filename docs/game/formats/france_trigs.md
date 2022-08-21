# France.trigs

`France.trigs` contains trigger zones.

To be extended!

## [Kaitai](http://kaitai.io/) Format

### PC

```yaml
meta:
  id: france_trigs
  file-extension: trigs
  endian: le
  encoding: UTF-8
seq:
  - id: fourcc
    contents: "JGRT"
  - id: trigger_count
    type: u4
  - id: triggers
    type: trigger
    repeat: expr
    repeat-expr: trigger_count
types:
  trigger:
    seq:
      - id: type_crc
        type: u4
        enum: trigger_type
      - id: data
        type:
          switch-on: type_crc
          cases:
            trigger_type::unknown: trigger_unknown
            trigger_type::sound_trigger: trigger_sound_trigger
            trigger_type::box: trigger_box
            trigger_type::zone: trigger_zone
            trigger_type::district: trigger_district
            trigger_type::polygon: trigger_polygon
  trigger_unknown:
    seq:
      - id: name_crc
        type: u4
      - id: height
        type: f4
      - id: polygon_volume_count
        type: u2
      - id: polygon_volumes
        type: polygon_volume
        repeat: expr
        repeat-expr: polygon_volume_count
      - id: unk
        type: u4
  trigger_sound_trigger:
    seq:
      - id: name_crc
        type: u4
      - id: sen_tag_crc
        type: u4
      - id: enabled
        type: u2
      - id: height
        type: f4
      - id: polygon_volume_count
        type: u2
      - id: polygon_volumes
        type: polygon_volume
        repeat: expr
        repeat-expr: polygon_volume_count
      - id: string_length
        type: u2
      - id: string
        type: strz
        size: string_length
      - id: unk
        type: u4
      - id: sub1s
        type: trigger_sound_trigger_sub1
        repeat: expr
        repeat-expr: 5
      - id: unk2
        type: f4
      - id: unk3
        type: f4
      - id: sub2s
        type: trigger_sound_trigger_sub2
        repeat: expr
        repeat-expr: 3
      - id: sub1s2
        type: trigger_sound_trigger_sub1
        repeat: expr
        repeat-expr: 4
  trigger_sound_trigger_sub1:
    seq:
      - id: string_length
        type: u2
      - id: string
        type: strz
        size: string_length
      - id: unk
        type: u4
  trigger_sound_trigger_sub2:
    seq:
      - id: sub3_count
        type: u2
      - id: sub3s
        type: trigger_sound_trigger_sub3
        repeat: expr
        repeat-expr: sub3_count
  trigger_sound_trigger_sub3:
    seq:
      - id: string_length
        type: u2
      - id: string
        type: strz
        size: string_length
      - id: unk1
        type: u4
      - id: unk2
        type: f4
      - id: unk3
        type: u1
      - id: unk4
        type: f4
  trigger_box:
    seq:
      - id: name_crc
        type: u4
      - id: mat_0_x
        type: f4
      - id: mat_0_y
        type: f4
      - id: mat_0_z
        type: f4
      - id: mat_1_x
        type: f4
      - id: mat_1_y
        type: f4
      - id: mat_1_z
        type: f4
      - id: mat_2_x
        type: f4
      - id: mat_2_y
        type: f4
      - id: mat_2_z
        type: f4
      - id: mat_3_x
        type: f4
      - id: mat_3_y
        type: f4
      - id: mat_3_z
        type: f4
      - id: unk_x
        type: f4
      - id: unk_z
        type: f4
      - id: script_name_length
        type: u2
      - id: script_name
        type: strz
        size: script_name_length > 128 ? 128 : script_name_length
      - id: unkshort1
        type: u2
      - id: unkshort2
        type: u2
  trigger_zone:
    seq:
      - id: name_crc
        type: u4
      - id: height
        type: f4
      - id: polygon_volume_count
        type: u2
      - id: polygon_volumes
        type: polygon_volume
        repeat: expr
        repeat-expr: polygon_volume_count
      - id: unk_count
        type: u4
      - id: unks
        type: u4
        repeat: expr
        repeat-expr: unk_count
      - id: strings
        type: trigger_zone_strings
        repeat: expr
        repeat-expr: 2
      - id: unk6
        type: u4
      - id: unk7
        type: u2
  trigger_zone_strings:
    seq:
      - id: string1_length
        type: u2
      - id: string1
        type: strz
        size: string1_length > 128 ? 128 : string1_length
      - id: string2_length
        type: u2
      - id: string2
        type: strz
        size: string2_length > 128 ? 128 : string2_length
  trigger_district:
    seq:
      - id: name_crc
        type: u4
      - id: unk1
        type: u1
      - id: unk2
        type: f4
      - id: polygon_volume_count
        type: u2
      - id: polygon_volumes
        type: polygon_volume
        repeat: expr
        repeat-expr: polygon_volume_count
      - id: unk3
        type: u4
      - id: unk4
        type: u2
  trigger_polygon:
    seq:
      - id: name_crc
        type: u4
      - id: sen_tag_crc
        type: u4
      - id: enabled
        type: u2
      - id: height
        type: f4
      - id: polygon_volume_count
        type: u2
      - id: polygon_volumes
        type: polygon_volume
        repeat: expr
        repeat-expr: polygon_volume_count
      - id: string_length
        type: u2
      - id: string
        type: strz
        size: string_length > 128 ? 128 : string_length
      - id: flags
        type: u2
  polygon_volume:
    seq:
      - id: point_count
        type: u2
      - id: points
        type: vector3
        repeat: expr
        repeat-expr: point_count
  vector3:
    seq:
      - id: x
        type: f4
      - id: y
        type: f4
      - id: z
        type: f4
enums:
  trigger_type:
    0x976F2D35: "unknown"
    0x9C8E92D2: "unknown2"
    0x9EE26816: "sound_trigger"
    0xA0787FC8: "box"
    0x0A0AFF97: "zone"
    0xA13E6F5F: "district"
    0xAF36A899: "polygon"
```
