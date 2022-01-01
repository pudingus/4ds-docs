# MAT_FLAGS
(uint16)
Bit | Mask | Name | Description
----|------|------|------
0  | 0x1 | DISABLE_U_TILE | disable texture wrap on the U axis, useful for skyboxes or color keyed car wheels
1  | 0x2 | DISABLE_V_TILE | disable texture wrap on the V axis, useful for skyboxes or color keyed car wheels
2  | 0x4 | DIFFUSE_MAP | enable diffuse texture
3  | 0x8 | ENV_MAP | enable environment texture, used for cheap reflection of the surroundings
4  | 0x10 | UNKNOWN_4 | 
5  | 0x20 | UNKNOWN_5 | 
6  | 0x40 | UNKNOWN_6 | 
7  | 0x80 | MIP_MAPPING | enable mipmapping
8  | 0x100 | IMAGE_ALPHA | use alpha channel from the diffuse map, COLOR_KEY or ALPHA_MAP flag must be on to have effect
9  | 0x200 | ANIMATED_ALPHA | used only if reading alpha map from separate file, ANIMATED_DIFFUSE flag must be on to have effect
10 | 0x400 | ANIMATED_DIFFUSE | enables diffuse map animation. If using embedded alpha channel in TGA or using color key then ANIMATED_DIFFUSE enables both diffuse and alpha animation.
11 | 0x800 | COLORED | enables the use of ambient and diffuse color in the material. If DIFFUSE_MAP is disabled, then ambient and diffuse color is always used regardless
12 | 0x1000 | TWO_SIDED | disables backface culling
13 | 0x2000 | COLOR_KEY | for 8bit bitmaps, the first color in the pallete is transparent, IMAGE_ALPHA flag supresses the effect
14 | 0x4000 | ALPHA_MAP | alpha map texture dimensions in separate file needs to be power of two (e.g. 128x64)
15 | 0x8000 | ADDITIVE_MIXING | 