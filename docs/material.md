# MATERIAL

```{toctree}
---
maxdepth: 4
caption: Contents
titlesonly:
---
env_flags
mat_flags
```

The word 'map' is synonymous to texture

in v41 (HD2) and v42 (Chameleon) colors are `vector4` instead of `vector3`

    Name            Type       Bytes
    -----------------------------------------------------
    envTile         uint8       1
    envFlags        ENV_FLAGS   1
    flags           MAT_FLAGS   2
    ambientColor    vector3    12    vector4 in v41, v42
    diffuseColor    vector3    12    vector4 in v41, v42
    ( specularColor vector4    12 )  only v41, v42
    emissiveColor   vector3    12    vector4 in v41, v42
    ( glossiness    float       4 )  only v41, v42
    opacity         float       4 

    if (flags.ENV_MAP)
    | envMapAmount  float       4
    | envMapName    pstring    1-256

    diffuseMapName  pstring   1-256

    if (diffuseMapName.length > 0 and flags.ALPHA_MAP and not flags.IMAGE_ALPHA)
    | alphaMapName  pstring   1-256
        
    if (flags.ANIMATED_DIFFUSE)
    | frameCount    uint32      4
    | unknown                   2
    | frameDelay    uint32      4     
    | unknown                   8


- `envTile` ([uint8](types.md)) - tiling of the env map, usually 1. Has effect only in Mafia.  
- `envFlags` ([ENV_FLAGS](env_flags.md)) - this one is a weird mix of different options encoded in 8bit value. In order from the least significant bit, first is a 3bit integer (little-endian, bit 0-2), then a 1bit flag, then a 3bit integer again and a 1bit flag.  
- `flags` ([MAT_FLAGS](mat_flags.md))
- `ambientColor`, `diffuseColor` ([vector3](types.md#vector3)) - always used if COLORED flag is set. If COLORED is not set, its used only if DIFFUSE_MAP flag is not set. RGB, each component has range 0.0f - 1.0f  
- `specularColor` ([vector4](types.md#vector4)) - (not used in Mafia). RGB color of the specular highlight, additive mixing. black - no highlight, white - white highlight. Each component has range 0.0 - 1.0  
- `emissiveColor` ([vector3](types.md#vector3)) - RGB, each component has range 0.0 - 1.0  
- `glossiness` ([float](types.md)) - (not used in Mafia). Usable range 0.0f - 100.0f - higher value = shinier = smaller size of specular highlight  
- `opacity` ([float](types.md)) - usable range 0.0f - 1.0f. 1.0 = visible, 0.0 = invisible  
- `envMapAmount` ([float](types.md)) - usable range 0.0f - 1.0f, 1.0 = only env map is shown  
- `envMapName` ([pstring](types.md#pstring))
- `diffuseMapName` ([pstring](types.md#pstring))
- `alphaMapName` ([pstring](types.md#pstring))
- `frameCount` ([uint32](types.md)) - number of frames, maximum is 100. File names should end with double digit number, i.e. aaa00.bmp, aaa01.bmp ... aaa99.bmp  
- `frameDelay` ([uint32](types.md)) - delay between frames, in miliseconds  

## Strange behaviour of color in Mafia

There is this weird behaviour, either a bug or intended. This is only relevant for Mafia. HD2 or Chameleon are not affected.  
Let's say we have an object, this object is made of three spheres, each sphere has a different color, one is red, other is green and the third is blue. The problem is, in game, all spheres will be red.


It's because, for some reason `diffuseColor`, `ambientColor`, `emissiveColor` and `opacity` values are set only once per object, and set to the values of the first facegroup. 
But for `diffuseColor` and `ambientColor` whether the colors from the first facegroup are used depends on the DIFFUSE_MAP and COLORED flags - see [material flags](mat_flags.md). But these two flags can be enabled in any facegroup and it will work as if they are enabled in facegroup 0.

Example:  
facegroup 0, red  
facegroup 1, green  
facegroup 2, blue  
the final color will be red  

facegroup 0, red  
facegroup 1, green, DIFFUSE_MAP   
facegroup 2, blue  
the final color will be white (because DIFFUSE_MAP flag needs COLORED flag, otherwise default color will be used)

facegroup 0, red  
facegroup 1, green, DIFFUSE_MAP  
facegroup 2, blue, COLORED  
the final color will be red


Although the `opacity` value is shared among facegroups, the effect of transparency is enabled for each facegroup separately. To enable it, set opacity to less than 1.0f.

This is solely about `diffuseColor`, `ambientColor`, `emissiveColor` and `opacity`. Textures are not affected.
