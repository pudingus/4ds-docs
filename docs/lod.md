# LOD
```{toctree}
---
maxdepth: 4
caption: Contents
---
vertex
facegroup
```

    Name            Type       Bytes
    -----------------------------------------------------
    drawDistance    float      4 
    ( numExtraData  uint32     4 )   only HD2 and Chameleon
    numVerts        uint16     2
    vertices        VERTEX[numVerts]
    ( extraData     float[numVerts × numExtraData] )   only HD2 and Chameleon
    numFaceGroups   uint8
    faceGroups      FACEGROUP[numFaceGroups]


- `drawDistance` ([float](types.md)) - 0.0 for last (lowest detail) lod
- `numVerts` ([uint16](types.md))
- `vertices` ([VERTEX](vertex.md)[])- array of [VERTEX](vertex.md)
- `numFaceGroups` ([uint8](types.md))
- `facegroups` ([FACEGROUP](facegroup.md)[])- array of [FACEGROUP](facegroup.md)
