# WHAT IS A KILOMETER (Shaders)
This lives in the pass section of the shader file
- Vertex Shader
	-  Set position of vertices on a mesh
	-  Pass info to the fragment shader
	- It is setup at clip space
- Fragment Shader
	- This modifies pixel color 
Material
- Part of the properties that we defined ourselves
- The material has a reference to the shader
- It is mostly a pre-configured shader data that the renderer uses well to render things on screen
	- So we assign a shader to a material and tweak the parameters to get the effect we want
- Colors
- Valves
- Textures
## Basic KnowHows on applying shaders in Unity
- You cannot apply a shader directly to an object in scene
	- First You have to create a material
	- Go to inspector for the Shader and select your UnlitShader path
	- Apply the shader to the material
## Basic structure of a .shader file in Unity

```hlsl
Shader "InspectorPath/ShaderName"
{
	Properties
	{
		// Shader properties in this field
	}
	SubShader
	{
		// Subshader conf in this field
		// We add other passes for additonal graphics calculations 
		Pass
		{
			CGPROGRAM
			// CG Program C for graphics - HLSL code here
			ENDCG
		}
	}
	// If the shader is f up
	Fallback "ExampleOtherShader"
}
```
- The script starts with the **InspectorPath** -> This makes reference to the inspector in Unity the one that lets us apply the materials in the shader option below the material name.
![[Pasted image 20240623221014.png]]
- Then the **Properties** regarding textures, vectors, colors and all the Render Pipeline mumbo-jumbo
- Finally to a **SubShader** and the **Fallback** a shader that is optional regarding the failing of the main shader

The shader code in pass executes sequentially this means anything you want to use, regarding functions or variables, have to be declared before any usage or you will get errors

```hlsl
float4 ourFunction() {
	return true;
}

fixed4 frag(v2f i) : SV_Target {
	float4 f = ourFunction();
	return f;
}
```

### ShaderLab Properties

These are properties that can be manipulated in the inspector and there are 8 different properties for us to handle but first have to be declared in the context of our shader.
- ``PropertyName ("display name", type) = defaultValue``
- We have four parts, first the name of the property itself, then the name in the inspector, the type for the property type and the default value assigned.
- For example when we created our unlit material this property appeared
- ![[Pasted image 20240625175539.png]]
- The **Texture** property was declared in the properties section of the shader code
- ![[Pasted image 20240625175655.png]]
- You can declare properties in different ways, like having a slider bar to assign it or a plain float number
```hlsl
Properties
    {
        // _MainTex ("Texture", 2D) = "white" {}
        _Specular ("Specular", Range(0.0, 1.1)) = 0.3
        _Factor ("Color Factor", Float) = 0.3
        
        // To change the RGBA at runtime
        _Cid ("Color id", Int) = 2
        _Color ("Tint", Color) = (1, 1, 1, 1)
        _VPos ("Vertex Position", Vector) = (0, 0, 0, 1)

        // Declaring textures in the shader
        _MainTex ("Texture", 2D) = "white" {}
        // Declaring a texture with cubemapping
        _Reflection ("Reflection", Cube) = "black" {}
        // 3D type texture
        _3DTexture ("3D Texture", 3D) = "white" {}
    }
```
- We declare the properties first in the shaderlab section so it has to be declared in ShaderLab, but when we use it in the **CGPROGRAM** section of our shader will be accessed in CG or in the case that we are using HLSL we will have to use that, but what we've done here is called connection variables.
- So when we declared this stuff shaderlab gives the context to the whole program