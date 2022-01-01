# SECTOR
```{toctree}
---
maxdepth: 4
caption: Contents
titlesonly:
---
portal
```
Frame name should begin with "sector".  
In Mafia, they should be always at world origin (0;0;0).
## SECTOR (v29)

    Name            Type       Bytes
    >---------------------------------------------------
    flags1          uint32      4     
    flags2          uint32      4    
    numVerts        uint32      4
    numFaces        uint32      4
    vertices        vector3[numVerts]
    faces           face[numFaces]
    min             vector3    12
    max             vector3    12
    numPortals      uint8       1
    portals         PORTAL[numPortals]


- `flags1` ([uint32](types.md)) - usually 2049, 2113, 2305  
bit 0 - unknown,  
bit 1 - disable,   
bit 6 - occlude
- `flags2` ([uint32](types.md)) - unknown, usually zero, non-zero only in HD2
- `numVerts` ([uint32](types.md))
- `numFaces` ([uint32](types.md))
- `vertices` ([vector3](types.md#vector3)[])
- `faces` ([face](types.md#face)[])
- `min`, `max` ([vector3](types.md#vector3)) - local space bounding box
- `numPortals` ([uint8](types.md)) - size of `portals` array
- `portals` ([PORTAL](portal.md)[])

## SECTOR (v41, v42)
Sector struct in v41 and v42 have the same entries but in slightly different layout - `min` `max` are at a different location, they come before vertex and face data.  

Version 41 (HD2) uses `vector4`. Version 42 (Chameleon) uses `vector3`.
```
        Name            Type       Bytes
        ----------------------------------------------------
        flags1          uint32      4     
        flags2          uint32      4     
        numVerts        uint32      4
        numFaces        uint32      4
   |->  min             vector4/vector3  16/12   <---|
   |->  max             vector4/vector3  16/12   <---|    
   |    vertices        vector4/vector3[numVerts]    |
   |    faces           face[numFaces]               |
   |--                                             --| 
   |--                                             --| 
        numPortals      uint8       1
        portals         PORTAL[numPortals]
```