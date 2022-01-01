# TARGET

    Name        Type       Bytes
    -----------------------------------------------------
    flags       uint16     2
    numLinks    uint8      1
    linkIds     uint16[numLinks]        


- `flags` ([uint16](types.md)) - bit 0 enable  
- `numLinks` ([uint8](types.md)) 
- `linkIds` ([uint16](types.md)[]) - 1-based frame id, can be greater than current frame id