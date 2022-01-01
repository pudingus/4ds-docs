# Common types
these types are used throughout the documentation

## Primitive types
Type | Width | Description
-----|-------|------------
**uint8** | 1 byte | 8 bit unsigned integer
**uint16**| 2 bytes | 16 bit unsigned integer
**uint32**| 4 bytes | 32 bit unsigned integer
**float** | 4 bytes | 32 bit single precision floating point number
**char**  | 1 byte | 0-127 represents ascii letters  
  
 **** 
## Other common types

### vector3
Size: 12 bytes
```
x, y, z    float
```

### vector4
On it's own it's used only in version 41 (HD2). But it's used in all versions as part of the matrix4 type.  
Size: 16 bytes
```
x, y, z, w    float
```

### pstring
Length prefixed ASCII string, can hold maximum of 255 characters.  
Minimum size 1 byte. Maximum size 256 bytes.
```       
length  uint8  
text    char[length] 
```

### quat (v29)
Size: 16 bytes  
right hand rule
```
w, x, y, z   float
```

### quat (v41, v42)
Size: 16 bytes  
The `w` component is at the last place.
```    
x, y, z, w   float
```

### face
Size: 6 bytes
```
a, b, c   uint16    //0-based vertex indices
```

### matrix4
Size: 64 bytes
```
row1   vector4    //see vector4 above
row2   vector4
row3   vector4
row4   vector4
```