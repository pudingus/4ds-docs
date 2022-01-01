# ENV_FLAGS
(uint8)

Bit | Description
-----|------
0 | envMode (bit 0)
1 | envMode (bit 1)
2 | envMode (bit 2)
3 | disable all textures
4 | envType (bit 0)
5 | envType (bit 1)
6 | envType (bit 2)
7 | addEffect

         envType   envMode
           |         |
         |‾‾‾|     |‾‾‾|
       1 1 1 1   1 1 1 1
       |         |
       |         |
    addEffect   disable


`envMode` is a 3bit unsigned integer with range 0-7, but usable values are 1-5. This sets the operation used for blending the diffuse map with env map. See [D3DTEXTUREOP](https://docs.microsoft.com/en-us/windows/win32/direct3d9/d3dtextureop) from DirectX SDK.

    0 = unset
    1 = D3DTOP_BLENDFACTORALPHA
    2 = D3DTOP_BLENDCURRENTALPHA
    3 = D3DTOP_MODULATE
    4 = D3DTOP_MODULATE2X
    5 = D3DTOP_ADD
    6 = ---
    7 = ---

Value 0 should never be used, it doesn't set any blending operation, that means the last value set in previous draw calls will be used. This could be different every frame due to view frustrum culling, depth sorting... In Mafia values 6, 7 are the same as 0. In HD2 and Chameleon they are usable, details to be determined.

`envType` is a 3bit unsigned integer with range 0-7. This is about UV coordinates.

    0 = sphere mapping
    1 = flipped sphere mapping
    2..7 = don't use sphere mapping, the behavior is slightly different in each game


The names `EnvMode` and `EnvType` are present Mafia engine dll with debug symbols, but I don't which name correspond to which description, they might mean the opposite thing in the engine.
