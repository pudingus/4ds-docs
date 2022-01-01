# GLOW

    Name        Type       Bytes
    ----------------------------------------------------
    numGlows    uint8      1
    glows       GLOW[numGlows]
      position    float       4
      ( unknown   float       4 )   only HD2, Chameleon
      matId       uint16      2  

- `numGlows` ([uint8](types.md)) 
- `glows` (GLOW[])
- `position` ([float](types.md))
- `matId` ([uint16](types.md)) - 1-based material id. Must not be zero.