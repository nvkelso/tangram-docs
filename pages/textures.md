*This is the technical documentation for Tangram's `textures` block. For a conceptual overview of the texturing system, see the [Materials Overview](Materials-Overview.md).*

##`textures`

The `textures` element is an optional top-level element in the [scene file](scene-file.md). It has only one kind of sub-element: a _texture name_.

Textures allow image files to be used in the `ambient`, `diffuse`, `specular`, and `normal` parameters of a [material](materials.md). A texture requires, at the minimum, a `url` path.


```yaml
textures:
    pois:
        url: demos/images/marker.png
        mapping: uv
    brick:
        url: demos/images/brick.jpg
        mapping: uv
```

#### texture names
Required _string_, can be anything. No default.

### texture parameters

#### `mapping`
Optional _string_, one of `uv`, `planar`, `triplanar`, or `spheremap`. Default is `triplanar` for `normal` textures and `spheremap` for all others.

The `spheremap` mapping can't be used with a `normal` map.

```yaml
material:
    diffuse:
        texture: ./material/rock.jpg
        mapping: uv
```

#### `scale`

Optional _number_ or _2D vector_. `number` or `[x,y]`. Defaults to `[1,1]`.

Sets a scaling value for the texture.

```yaml
material:
    diffuse:
        texture: ./material/rock.jpg
        mapping: uv
        scale: 2.0
```

#### `amount`

Optional _number_ or _3D vector_. `number` or `[r,g,b]`. Defaults to `1`.

This value is a multiplier on the effect of the texture – it can be thought of as the texture's opacity.

```yaml
material:
    ambient: .5
    diffuse:
        texture: ./material/rock.jpg
        mapping: uv
        scale: 2.0
        amount: 0.5
``` 

#### `filtering`
Optional _string_, one of `linear`, `nearest`, or `mipmap`. Defaults to `linear`.

Sets the filtering mode for the texture, which determines quality at various zoom levels.

```yaml
    ghost:
        url: demos/images/ghost.png
        filtering: mipmap
```
        
#### `sprites`
Optional parameter. Defines the start of a `sprites` block.

`sprites` take only one kind of parameter: the _sprite name_. Any number of sprites may be defined.

#### sprite name
Required _string_. Can be anything. No default.

Defines an area of a texture to be used as an individual sprite, as _[x origin, y origin, width, height]_ in pixels. 

```yaml
    pois:
        url: demos/images/poi_icons_32.png
        filtering: mipmap
        sprites:
            airport: [0, 0, 32, 32]
            restaurant: [0, 777, 32, 32]
            cafe: [0, 814, 32, 32]
            museum: [0, 518, 32, 32]
```
