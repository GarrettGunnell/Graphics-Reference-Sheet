## Texturing

**UV Coordinates:** UV Coordinates are 2D cartesian coordinates ranging from 0-1 on both axes for sampling textures. The horizontal axis is referred to as U and the vertical axis is referred to as V, hence "UV" coordinates. The U coordinate increases from left to right, and the V coordinate increases from bottom to top, except for Direct3D in which it increases from top to bottom. Each unique UV coordinate corresponds to a different pixel in a given texture.

### Maps

**Diffuse Map:** A texture that stores the base color of the model.

**Normal Map:** A normal map is a texture where each pixel represents a normal. This map informs how to more accurately light a albedo texture, giving the illusion of detail despite the geometry being flat. Most normals are encoded in RGB with the normal in the red and green channels. An exception is Unity, which encodes their normal maps with DXT5nm.

* **DXT5nm:** DXT5nm format stores the X and Y components of the normal and discards the Z. The Y component is stored in the green channel as usual but the X component is stored in the alpha channel. Because the Z component of the normal is discarded, it must be inferred at run time.

**Shadow Map:** A shadow map records the depth of geometry.

**Metallic Map:** A map to define the metallic value per texel instead of the whole material.

**Smoothness Map:** Same as the metallic map, a smoothness map defines the smoothness value per texel.

**Emission Map:** This type of map defines what texels should emit light.

**Occlusion Map:** This map informs what texels should be in shadow.

**Detail Map:** A detail map is applied to an existing texture for details, obviously.

* **Detail Mask:** A detail mask is applied when you don't want a detail map to show up over the entire material. With the mask you can control which texels sample the detail map and which don't.

**Transparency Map:** This map stores transparency data in each texel.

**Cube Map:** A cube map is a 3 dimensional texture sampled with a normal vector. Things like skyboxes are textured with cube maps.

### Normal Blending

* When using both a base normal map and a detail normal map, there are several ways to blend these normals together to produce more satisfying results.

**Linear Blending:** The most naive blending approach which produces poor results. With this method you unpack both normals, add them together, and renormalize. This basically averages the two normals, which ends up flattening both the base normals and the detail normals. Don't do this.

**Partial Derivative Blending:** By adding the partial derivatives of the *x* and *y* components we can find the sum of the height fields without averaging them like with linear blending. This approach works very nicely with maps that are mostly flat, but when dealing with steep slopes you will still lose some detail due to the normalization process. 

**Whiteout Blending:** This approach is like the one above but there's no scaling by *z* for *x* and *y*, only for *z*. With this approach detail is more apparent all across the board while flat normals still act as they should.
 
**UDN Blending:** UDN Blending is a simpler form of the above approach, it removes the multiplication of the *z* components, functionally leaving this method like linear blending but only adding *x* and *y*. This blending method is an optimization over whiteout blending, removing some precious ALU instructions.

### Filtering

**Bilinear Filtering:** When a texture is sampled inbetween 2 texels, those 2 texels are interpolated along both the U and V axis. A mipmap is sampled when the texel density becomes high enough that sampled texels are more than one texel apart.

**Mipmap:** A mipmap is a smaller version of a given texture. Each successive mipmap is half the width and height of the previous mipmap.

**Trilinear Filtering:** Similar to bilinear filtering, except this technique also interpolates between adjacent mipmap levels to get a smoother transition between mipmaps.

**Anisotropic Filtering:** Which mipmap is chosen is based on the worst dimension. If the difference between the width and the height of a projected texture is high, then the resulting render will be blurry in one dimension. Anisotropic filtering fixes this by decoupling the dimensions and sampling mipmaps with differing width and height.