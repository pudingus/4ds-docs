# MORPH

    numTargets      uint8

    if (numTargets > 0)
      numRegions    uint8
      numLods       uint8
      lods          MORPH_LOD[numLods]
        regions       MORPH_REGION[numRegions]
      min           vector3        vector4 in HD2
      max           vector3        vector4 in HD2
      center        vector3
      radius        float

- `numTargets` ([uint8](types.md)) 
- `numRegions` ([uint8](types.md)) 
- `numLods` ([uint8](types.md)) 
- `lods` (MORPH_LOD[]) - array of MORPH_LOD
- `regions` (MORPH_REGION[]) - array of MORPH_REGION
- `min`, `max` ([vector3](types.md#vector3)) - bounding box of the morph, the extent of all regions and targets combined. In local space.
- `center` ([vector3](types.md#vector3)) - calculated as `(min + max) / 2`
- `radius` ([float](types.md)) - calculated as `distance(min, max) / 2`

## MORPH_REGION

    numVerts      uint16
    vertices      MORPH_VERTEX[numVerts]
      targets       MORPH_TARGET[numTargets]
        pos           vector3
        normal        vector3
            
    if (numTargets * numVerts > 0)
      unknown       uint8

    vertexIds     uint16[numVerts]

- `numVerts` ([uint16](types.md))
- `vertices` (MORPH_VERTEX[])
- `targets` (MORPH_TARGET[])
- `pos` ([vector3](types.md#vector3)) - new position (absolute)
- `normal` ([vector3](types.md#vector3))
- `vertexIds` ([uint16](types.md)[])

The first target in each region is always unchanged, it stores the resting position.

