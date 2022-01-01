# MESH
```{toctree}
---
maxdepth: 4
caption: Contents
includehidden:
---
lod
```


    Name            Type       Bytes
    ----------------------------------------------------
    instanceId      uint16     2

    if (instanceId == 0)
      numLods       uint8      1
      lods          LOD[numLods]



- `instanceId` ([uint16](types.md)) - 1-based frame id, of which to copy geometry.   
Zero if frame uses its own geometry.  
Id cannot be greater then current frame id. Must be zero for skinned frames.
- `numLods` ([uint8](types.md)) - size of lods array
- `lods` ([LOD](lod.md)[])- array of [LOD](lod.md)