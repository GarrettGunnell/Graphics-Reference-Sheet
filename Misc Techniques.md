**Transparency:** The easiest way to render transparency is to keep it binary, either a fragment is entirely opaque or entirely transparent. With alpha clipping you can easily create a "dissolving" effect by increasing the alpha cutoff over a period of time for a mesh until it is completely transparent. In the case of legitimate transparency such as glass, we draw our transparent fragment last in order to blend it with whatever has already been drawn behind it.

**Dithering:** A method for fading out a texture. With dithering, we take a texture of dither patterns and use it to determine which fragments to clip, the farther along the dither patterns the more fragments are clipped.

* **Applications:** Dithering can be used to render shadows cast by faded out/transparent materials. The more dithered a shadow, the more apparent light is let through by a material.

**LOD Hierarchy:** LOD, or Level Of Detail, is a technique for rendering different meshes dependent on the view size of the object. When viewed from far away, you can use a lower detail mesh, while replacing it with higher detail meshes as you get closer.

* **Crossfading:** Crossfading is an extension of LOD, where you fade between the different meshes.

**GPU Instancing:** Batching instances with the GPU involves instructing the GPU to render the same mesh several times, reducing draw calls. When instancing with multiple lights, deferred rendering must be used. Potentially used for foliage like grass?

**Parallax:** To get a real sense of depth that goes beyond a normal map's abilities, we can fake parallax. In order to do this, we shift the texture coordinates relative to the observer.

* **Raymarching:** By sampling a height field several times per ray we can determine where the view ray actually penetrates a given surface to create a much more realistic parallax effect.

* * **Steep Parallax Mapping:** *Please fill this out*

* * **Relief Mapping:** *Please fill this out*

* * **Parallax Occlusion Mapping:** *Please fill this out*

**Flat Shading:** To see meshes as they actually are, made up of flat triangles, you can use the surface normals of the triangle itself rather than the vertices.