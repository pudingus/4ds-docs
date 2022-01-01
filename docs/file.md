# FILE

```{toctree}
---
maxdepth: 1
caption: Contents
hidden:
---
material
frame
```

Little endian

    Name            Type       Bytes
    ----------------------------------------------------------------
    signature       char[4]    4        
    version         uint16     2
    timestamp       FILETIME   8
    numMaterials    uint16     2
    materials       MATERIAL[numMaterials]
    numFrames       uint16     2
    frames          FRAME[numFrames]
    hasAnimFile     bool       1

- `signature` ([char](types.md)[4]) - identifies the file format - {0x34, 0x44, 0x53, 0x00} or "4DS\0"  
- `version` ([uint16](types.md)) - version of the format  
- `timestamp` ([FILETIME](https://docs.microsoft.com/en-us/windows/win32/api/minwinbase/ns-minwinbase-filetime)) - date and time of creation   
- `numMaterials` ([uint16](types.md)) - size of `materials` array  
- `materials` ([MATERIAL](material.md)[]) - array of [MATERIAL](material.md)  
- `numFrames` ([uint16](types.md)) - size of `frames` array  
- `frames` ([FRAME](frame.md)[]) - array of [FRAME](frame.md)  
- `hasAnimFile` ([bool](types.md)) - whether a 5ds animation file with the same name should be loaded and the should be automatically applied  

## Versions
- v29 - Mafia  
- v41 - Hidden & Dangerous 2  
- v42 - Wings of War, Chameleon, Circus Empire   

These versions are mostly the same, there are some changes in the layout, in a few places some fields are swapped or some fields are added.  
All differences are documented throughout this documentation.  
[Overview of the differences](version_differences.md)

There are two model files in Mafia folder with version 27, they should be parsed the same as v29.  


