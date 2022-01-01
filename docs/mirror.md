# MIRROR
every `vector3` except `center` is `vector4` in HD2

    Name         Type       Bytes
    ----------------------------------------------------
    min          vector3    12        vector4 in HD2
    max          vector3    12        vector4 in HD2
    center       vector3    12
    radius       float       4
    matrix       matrix4    64           
    color        vector3    12        vector4 in HD2
    activeRange  float       4
    numVerts     uint32      4
    numFaces     uint32      4
    vertices     vector3[numVerts]    vector4 in HD2
    faces        face[numFaces]

- `min`, `max` ([vector3](types.md#vector3)) - local space bounding box
- `center` ([vector3](types.md#vector3)) - calculated as `(min + max) / 2`
- `radius` ([float](types.md)) - calculated as `distance(min, max) / 2`
- `matrix` ([matrix4](types.md#matrix4)) - transformation of a 2x2x2 box that represents rendered area, in local coordinates. Objects which lie outside of this area won't be visible. If only part of the object is inside the area, the whole object will be visible.
- `color` ([vector3](types.md#vector3)) - color of the backdrop (sky). Skyboxes are not rendered in mirror reflections.
- `activeRange` ([float](types.md)) - if player is beyond this range, mirror turns off - no objects in the reflection will be rendered and so only the provided color above will be drawn.
- `numVerts` ([uint32](types.md))
- `numFaces` ([uint32](types.md))
- `vertices` ([vector3](types.md#vector3)[])
- `faces` ([face](types.md#face)[])