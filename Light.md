## Lighting

**Diffuse Reflection / Lambert's Cosine Law:** Diffuse reflection is the reflection of light from a surface such that the rays are scattered at many angles rather than just one. When these rays penetrate a surface they lose some wavelength and emerge colored. A simple way of calculating how much light is reflected off the surface is with Lambert's cosine law. Lambert's cosine law states that the amount of diffused light reflected from a surface is directly proportional to the cosine of the angle at which the light hits it. Since the dot product of two unit length vectors is the cosine of the angle, we just take the dot product of the light vector and the surface normal and we find how much light hits that surface.

**Specular Reflection:** Specular reflections are what happens when light is not diffused after hitting a surface, instead it bounces off the surface at an angle equivalent to the angle at which it hit the surface. Unlike diffuse reflections in which light rays are reflected in all directions, specular reflections are only visible when the reflected light is directed at you.

* **Fresnel Reflection:** The Fresnel effect shows that a surface is more reflective when observed at a shallower angle, such as the edge of an object. The Fresnel equations are the mathematics to describe how reflective at any given point an object is. The smoother a surface, the stronger the Fresnel reflections are.

### Techniques

**Lightmapping:** Lighting calculations are very costly, lightmapping provides a way to calculate light once and continually reuse it from then on. Lightmapping does not work for dynamic scenes as lighting must be recalculated every time something moves, but lightmapping is perfect for static geometry. Lightmapping also does not work for specular reflections. Another word for lightmapping is baked lighting.

**Image Based Lighting:** Image based lighting uses a cube map to inform an object of its ambient light. By painting on the environment surrounding an object, blurring it, and lowering the intensity, you can easily fake how ambient light is affecting an object.