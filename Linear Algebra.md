## Linear Algebra

**Normal:** A normal vector is a directional vector perpendicular to the surface at any given point.

**Unit Vector (Normalized):** A unit vector is a vector of magnitude (length) 1. A vector is considered normalized when it is unit length.

**Dot Product:** The dot product of two vectors is a scalar value equivalent to the cosine of the angle between two vectors multiplied by their magnitudes. The dot product represents how much two vectors work together, if they are orthogonal the dot product is 0 but if they are parallel then they are working together as much as possible.

**Cross Product:** The cross product of two vectors is another vector that is at a right angle to both, also known as perpendicular. The magnitude of this vector equals the area of a parallelogram with the original two vectors as its sides.

* **Bitangent / Binormal:** The cross product of a normal vector *N* and its tangent vector *T* results in the bitangent vector *B*. Using these three vectors we can construct an orientation matching the real orientation of the face at any given point. This allows us to match the real orientation of the face when bump mapping.