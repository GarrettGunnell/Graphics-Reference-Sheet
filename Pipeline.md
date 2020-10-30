# Graphics Pipeline

Notes related to the graphics pipeline, as it exists in Direct3D 11.

## Input-Assembler Stage

The input-assembler stage, abbreviated to IA, is the stage in which all data is read from user-filled buffers provided to the GPU. The IA stage is responsible for assembling the data into primitives that will be used by the following pipeline stages, such as line lists or triangle strips. Additionally, the IA stage is responsible for attaching semantics to data to make shaders more efficient. Once this data has been processed, it is outputted to the vertex shader.

## Vertex Shader Stage (Programmable / Required)

The vertex shader stage processes the vertices provided from the input assembler stage. In this stage you can perform per-vertex operations such as transformation or per-vertex lighting. Vertex shaders operate on one vertex at a time, and output one vertex at a time, meaning that the shader is executed once for every vertex passed through it. The vertex's location is converted into clip space and then output is passed to the hull shader if used, if not then the geometry shader, and if neither are used then the output is sent to the rasterizer.

## Tessellation Stages (Programmable / Optional)

### Hull Shader Stage

The hull shader stage takes as input one patch (quad, triangle, or line), and outputs a patch with tessellation factors attached to each edge. If an edge's tessellation factor is set to 0 or null, the patch will be culled, and the following stages will not be ran on the patch. This data is then passed into the tessellator stage.

### Tessellator Stage

The tessellator is a fixed function stage responsible for subdividing geometry as instructed by the tessellation factors received from the hull shader. The tessellator outputs this new mesh data as well as uv coordinates to the domain shader.

### Domain Shader Stage

The domain shader is responsible for converting the data from the tessellator stage into how it should be for the rest of the pipeline, such as interpolating the new vertex data from the original vertex data, as well as modifying the new vertex data like you would in the vertex shader. The domain shader is sort of like the real vertex shader when utilizing the tessellation stages. This vertex data is then supplied to the geometry shader, if used, otherwise it goes to the rasterizer.

## Geometry Shader Stage (Programmable / Optional)

The geometry shader, like the hull shader, takes as input a full primitive. This allows you to operate on up to 3 vertices at a time to implement different effects. So far, the only effect I have used the geometry shader for is generation of barycentric coordinates for the pixel shader, wire framing, and flat shading (using the same normal for all the vertices). Example algorithms that could be implemented in this stage, provided by microsoft, are: point sprite expansion, dynamic particle systems, fur/fin generation, shadow volume generation, single pass render-to-cubemap, per-primitive material swapping, and per-primitive material setup. This modified geometry data is then passed into the rasterizer.

## Rasterizer Stage

The rasterizer stage converts vector information into a raster image. Each primitive is converted into pixels with vertex values being interpolated across the primitive. These fragments (pixels) and interpolated data are then passed on to the fragment shader.

## Fragment Shader Stage (Programmable)

The fragment shader is responsible for coloring pixels on the screen. The fragment shader is mainly where textures are sampled, lighting is calculated, and post-processing effects are applied. This pixel data is outputted to the final stage.

## Output-Merger Stage

The output-merger stage generates the final rendered image. This stage is where depth testing is used to determine if a pixel should be drawn or not, as well as pixel color blending.