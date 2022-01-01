# FACEGROUP

    Name            Type       Bytes
    -----------------------------------------------------
    numFaces        uint16     2
    faces           face[numFaces]
    materialId      uint16     2  


- `numFaces` ([uint16](types.md)) - size of faces array
- `faces` ([face](types.md#face)[]) - array of [face](types.md#face)
- `materialId` ([uint16](types.md)) - 1-based material id. Zero to use default grey material.