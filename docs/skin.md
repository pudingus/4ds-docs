# SKIN
The skinned frame acts itself as a joint. I call it 'root' here.

## SKIN  (v29)
In Mafia, mesh vertices are sorted by joint id and weight.  
Joint 1 fully weighted vertices (1.0 weight)  
Joint 1 weighted vertices  
Joint 2 fully weighted vertices (1.0 weight)  
Joint 2 weighted vertices  
...  
Root fully weighted vertices (1.0 weight)  

    lods        SKIN_LOD[mesh.numLods]
      numJoints   uint8
      numW1Verts  uint32
      min         vector3
      max         vector3
      joints      SKIN_JOINT[numJoints]
        matrix      matrix4
        numW1Verts  uint32
        numWeights  uint32
        parentId    uint32
        min         vector3
        max         vector3
        weights     float[numWeights]

- `lods` (SKIN_LOD[]) - array of SKIN_LOD
- `numJoints` ([uint8](types.md))
- `numW1Verts` ([uint32](types.md)) - number of verts with 1.0 weight influenced by root, at the end of vertex buffer
- `min`, `max` ([vector3](types.md#vector3)) - bounding box of verts affected by this (root) joint, in local space
- `joints` (SKIN_JOINT[]) - array of SKIN_JOINT
- `joint.matrix` ([matrix4](types.md#matrix4))
- `joint.numW1Verts` ([uint32](types.md)) - number of verts with 1.0 weight
- `joint.numWeights` ([uint32](types.md)) - number of explicitly defined weights
- `joint.parentId` ([uint32](types.md)) - 1-based parent joint id, 0 = root
- `joint.min`, `joint.max` ([vector3](types.md#vector3)) - bounding box of verts affected by this joint, in local space
- `joint.weights` ([float](types.md)[]) - array of float

Every vertex should be described - sum of all numW1Verts for root and numW1Verts and numWeights for each joint should be equal to number of mesh vertices.


## SKIN  (v41, v42)

v41 uses vector4, v42 uses vector3

    numJoints   uint8
    min         vector4/vector3
    max         vector4/vector3
    parentIds   uint8[numGroups]      0 = root
    joints      JOINT[numGroups]
      matrix      matrix4
      min         vector4/vector3
      max         vector4/vector3
    lods        LOD[mesh.numLods]
      numWeights  uint32
      weights     WEIGHT[numWeights]
        boneId      uint8
        weight      uint8
