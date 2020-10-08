## ShaderLab

ShaderLab is the language Unity shaders are declared in.

A Unity shader skeleton looks as follows:

```
Shader "Custom/Example Shader" {
   
    Properties {
        _Albedo ("Albedo", Color) = (1, 1, 1, 1)
    }

   SubShader {

       Pass {
           CGPROGRAM
            #pragma vertex vp
            #pragma fragment fp

            #include "UnityCG.cginc"

            float4 _Albedo;

            float4 vp(float4 position : POSITION) : SV_POSITION {
                return UnityObjectToClipPos(position);
            }

            float4 fp(float4 position : SV_POSITION) : SV_TARGET {
                return _Albedo;
            }

           ENDCG
       }
   }
}
```

**Properties:** Properties are how Unity gives data to shaders from the inspector window. Basic properties include stuff like albedo, metallic, smoothness, textures, etc.

**Sub Shaders:** A sub shader is used to group multiple shader variants together for different platforms or performance levels.

**Pass:** A shader pass is what happens when an object is actually rendered, shaders must have at least one pass but can have any number of them. Multiple passes means the object is
rendered *n* times where *n* is the number of passes.

**CG PROGRAM / ENDCG:** These keywords indicate the beginning and end of HLSL/Cg shader code.

**#pragma vertex / #pragma fragment:** These preprocessor directives inform the entry points for the programmable parts of the rendering pipeline. In the example above, the vertex shader entry point is the function 'vp' and the entry point for the fragment shader is 'fp'.

## Semantics

Semantics inform the GPU what your data represents.

**POSITION:** The POSITION semantic is the position of the vertex given to the vertex program.

**SV_POSITION:** SV stands for system value and POSITION means the final vertex position.

**SV_TARGET:** This is the frame buffer, which contains the image being generated.
