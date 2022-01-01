# PORTAL
## PORTAL (v29)

    Name            Type       Bytes
    ----------------------------------------------------
    numVerts        uint8       1
    flags           uint32      4    
    nearRange       float       4
    farRange        float       4
    normal          vector3    12
    dotp            float       4
    vertices        vector3[numVerts]


- `numVerts` ([uint8](types.md)) 
- `flags` ([uint32](types.md)) -   
bit 0 unknown  
bit 2 enables rendering  
- `nearRange` ([float](types.md)) - if the camera is farther than "nearRange" from the portal center then scene2.bin objects in the first sector behind it wont be rendered (for both sides)
- `farRange` ([float](types.md)) - unknown  
- `normal` ([vector3](types.md#vector3)) - inverted face normal of the portal
- `dotp` ([float](types.md)) - dot product of the first vertex and the face normal (non inverted)
- `vertices` ([vector3](types.md#vector3)[])

## PORTAL (v41, v42)
v41 (HD2) stores the vertices as `vector4`, v42 (Chameleon) as `vector3`
```
        Name            Type       Bytes
        ----------------------------------------------------
        numVerts        uint8       1
    |-> normal          vector3    12    <---|
    |-> dotp            float       4    <---|
    |   flags           uint32      4        |
    |   nearRange       float       4        |   
    |   farRange        float       4        |
    |--                                    --|  
    |--                                    --|
     *  unknown         float       4           
        vertices        vector4/vector3[numVerts]
```