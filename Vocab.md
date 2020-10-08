## Linear Algebra

**Normal:** A normal is a directional vector perpendicular to the surface at any given point.

**Dot Product:** The dot product of two vectors is a scalar value equivalent to the cosine of the angle between two vectors multiplied by their magnitudes. The dot product represents how much two vectors work together, if they are orthogonal the dot product is 0 but if they are parallel then they are working together as much as possible.

## Rendering

**Bounding Box:** The smallest box in which a given mesh would fit. This is used to check if the mesh is in view of the camera.

**UV Coordinates:** UV Coordinates are 2D cartesian coordinates ranging from 0-1 on both axes for sampling textures. The horizontal axis is referred to as U and the vertical axis is referred to as V, hence "UV" coordinates. The U coordinate increases from left to right, and the V coordinate increases from bottom to top, except for Direct3D in which it increases from top to bottom. Each unique UV coordinate corresponds to a different pixel in a given texture.

**Bilinear Filtering:** When a texture is sampled inbetween 2 texels, those 2 texels are interpolated along both the U and V axis. A mipmap is sampled when the texel density becomes high enough that sampled texels are more than one texel apart.

**Mipmap:** A mipmap is a smaller version of a given texture. Each successive mipmap is half the width and height of the previous mipmap.

**Trilinear Filtering:** Similar to bilinear filtering, except this technique also interpolates between adjacent mipmap levels to get a smoother transition between mipmaps.

**Anisotropic Filtering:** Which mipmap is chosen is based on the worst dimension. If the difference between the width and the height of a projected texture is high, then the resulting render will be blurry in one dimension. Anisotropic filtering fixes this by decoupling the dimensions and sampling mipmaps with differing width and height.

**Detail Texture:** A detail texture is applied to an existing texture when viewing it up close to improve its appearance.

## Lighting

**Diffuse Reflection / Lambert's Cosine Law:** Diffuse reflection is the reflection of light from a surface such that the rays are scattered at many angles rather than just one. When these rays penetrate a surface they lose some wavelength and emerge colored. A simple way of calculating how much light is reflected off the surface is with Lambert's cosine law. Lambert's cosine law states that the amount of diffused light reflected from a surface is directly proportional to the cosine of the angle at which the light hits it. Since the dot product of two unit length vectors is the cosine of the angle, we just take the dot product of the light vector and the surface normal and we find how much light hits that surface.

**Specular Reflection:** Specular reflections are what happens when light is not diffused after hitting a surface, instead it bounces off the surface at an angle equivalent to the angle at which it hit the surface. Unlike diffuse reflections in which light rays are reflected in all directions, specular reflections are only visible when the reflected light is directed at you.
