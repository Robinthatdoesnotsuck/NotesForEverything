# WHAT IS A KILOMETER (Shaders)
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
