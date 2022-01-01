# FRAME

```{toctree}
---
maxdepth: 1
caption: Contents
hidden:
---
mesh
skin
morph
billboard
glow
projector
mirror
emitor
light
sector
dummy
target
joint
occluder
```

Y is up axis

    Name            Type       Bytes
    ----------------------------------------------------
    frameType       uint8       1

    if (frameType == FRAME_VISUAL)
      visualType    uint8       1
      renderFlags   uint8       1
      renderFlags2  uint8       1

    parentId        uint16      2       
    position        vector3    12      
    scale           vector3    12    scale and rotation are swapped in HD2, Chameleon
    rotation        quat       16    scale and rotation are swapped in HD2, Chameleon
    ( unknown       float       4 )  only HD2    
    cullingFlags    uint8       1     
    name            pstring    1-256    
    params          pstring    1-256
    ...


- `frameType` ([uint8](types.md))  
    1  = FRAME_VISUAL  
    2  = FRAME_LIGHT  
    5  = FRAME_SECTOR  
    6  = FRAME_DUMMY  
    7  = FRAME_TARGET  
    10 = FRAME_JOINT  
    12 = FRAME_OCCLUDER  

- `visualType` ([uint8](types.md))  
    0 = VISUAL_OBJECT  
    2 = VISUAL_SINGLEMESH  
    3 = VISUAL_SINGLEMORPH  
    4 = VISUAL_BILLBOARD  
    5 = VISUAL_MORPH  
    6 = VISUAL_GLOW  
    7 = VISUAL_PROJECTOR  
    8 = VISUAL_MIRROR  
    9 = VISUAL_EMITOR  

- `renderFlags` ([uint8](types.md)) - unknown  
- `renderFlags2` ([uint8](types.md))  
    bit 0 - use depth bias  
    bit 1 - receive shadows  
    bit 3 - unknown, always 1  
    bit 5 - enable texture projection  
    bit 7 - disable fog

- `parentId` ([uint16](types.md))  - 0 == no parent, parent must always be before children!  
- `position` ([vector3](types.md#vector3)) - in parent coordinates  
- `scale` ([vector3](types.md#vector3)) - in parent coordinates  
- `rotation` ([quat](types.md#quat-v29)) - in parent coordinates  
- `cullingFlags` ([uint8](types.md)) - bit 0 enables rendering  
- `name` ([pstring](types.md#pstring)) - sectors should begin with "sector"  
- `params` ([pstring](types.md#pstring)) - miscelleaneous parameters encoded as text  
```
...

switch (frameType)
FRAME_VISUAL:

    switch (visualType)
    VISUAL_OBJECT:
        mesh    MESH
    
    VISUAL_SINGLEMESH:
        mesh    MESH
        skin    SKIN
    
    VISUAL_SINGLEMORPH:
        mesh    MESH
        skin    SKIN
        morph   MORPH
    
    VISUAL_BILLBOARD:
        mesh    MESH
        billboard BILLBOARD

    VISUAL_MORPH:
        mesh    MESH
        morph   MORPH

    VISUAL_GLOW:
        glow    GLOW
    
    VISUAL_PROJECTOR:
        projector PROJECTOR

    VISUAL_MIRROR:
        mirror  MIRROR

    VISUAL_EMITOR:
        emitor  EMITOR    

FRAME_LIGHT:
    light   LIGHT

FRAME_SECTOR:
    sector  SECTOR

FRAME_DUMMY:
    dummy   DUMMY

FRAME_TARGET:
    target  TARGET

FRAME_JOINT:
    joint   JOINT

FRAME_OCCLUDER:
    occluder OCCLUDER
```