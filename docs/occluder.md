# OCCLUDER

    Name            Type       Bytes
    -----------------------------------------------------
    numVerts        uint32     4
    numFaces        uint32     4
    verts           vector3[numVerts]       vector4 in HD2
    faces           face[numFaces]

- `numVerts` ([uint32](types.md))
- `numFaces` ([uint32](types.md))
- `verts` ([vector3](types.md#vector3)[]) - vertex positions are in local coordinates
- `faces` ([face](types.md#face)[])