# GOOG_texture_ktx

## Contributors

* Stanlo Slasinski, Google

## Status

Draft

## Dependencies

Written against the glTF 2.0 spec.

## Overview

This extension adds the ability to specify textures using the [Khronos Texture file format (KTX)](https://github.com/KhronosGroup/KTX-Specification/tree/1.0). An implementation of this extension can use the textures provided in KTX files as an alternative to the PNG or JPG textures available in glTF 2.0.

The extension is added to the `textures` node and specifies a `source` property that points to the index of the `images` node which in turn points to the KTX texture file. A client that does not understand this extension can ignore the KTX file and continue to rely on the PNG or JPG textures specified.

```json
"textures": [
    {
        "source": 0,
        "extensions": {
            "GOOG_texture_ktx": {
                "source": 1
            }
        }
    }
],
"images": [
    {
        "uri": "defaultTexture.png"
    },
    {
        "uri": "ktxTexture.ktx"
    }
]
```

When used in the glTF Binary (.glb) format the `images` node that points to the KTX file uses the `mimeType` value of *image/ktx*.

```json
"textures": [
    {
        "source": 0,
        "extensions": {
            "GOOG_texture_ktx": {
                "source": 1
            }
        }
    }
],
"images": [
    {
        "mimeType": "image/png",
        "bufferView": 1
    },
    {
        "mimeType": "image/ktx",
        "bufferView": 2
    }
]
```

## glTF Schema Updates

* **JSON schema**: [glTF.GOOG_texture_ktx.schema.json](schema/glTF.GOOG_texture_ktx.schema.json)

## Known Implementations

This extension is used by [Sceneform](https://developers.google.com/ar/develop/java/sceneform/).