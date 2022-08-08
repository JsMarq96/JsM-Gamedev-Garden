# Compute pipeline

### 1.- Crear el Shader
Teniendo un shader en formato WGSL, para que funcine tenemos que anadirlo a un Modulo de Shader (ShaderModule), en el que definiremos el codigo, y opcional podemos definir un sourceMap (??) y unas pistas(??).

Esos ShaderModule se crean en contexto a un device, por lo tanto se llaman con

	device.crateShaderModule({code, [sourceMap], [hints]})


## 2.- Crear la pipeline
Una vez tenemos el modulo, podemos crearlo o incorporarlo a una pipeline en compute con

	GPUComputePipeline = device.createComputePipeline({ compute: { module: shaderModule, entryPoint: "mainShaderFunc" } })

