# JOINT
    
    Name        Type       Bytes
    -----------------------------------------------------
    ( matrix    matrix4    64 )      Only Mafia
    jointId     uint32      4


- `matrix` ([matrix4](types.md#matrix4)) - unused, can be set to identity matrix for export
- `jointId` ([uint32](types.md)) - 1-based, uniquely identifies this joint among other joints within parent singlemesh frame. This is not a frame id. If there are multiple singlemeshes, each has it's own set of ids. Zero if joint is not a descendant of a singlemesh.

