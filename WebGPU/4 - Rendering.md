# Render Pipeline

## Shaders
- Programados en WGLS
- Pueden tener varios entripoints, pudiendo usar uno para cada stage


## Crearion de la pipeline (GPURenderPipeline)
Descriptor:
- primitive: el tipo de topologia
- depthStencil: establece la funcion de depth a usar
- multisample: sampling rate del MSAA??
- vertex:
	- buffers: una lista delos vertex buffers
		- arrayStride
		- stepMode ??
		- atributes
	- module: proporcionar el shader module ya compilado y marcar el entrypoint
- fragment:
	- module: igual, pero seleccionando el entripoint del fragment shader
	- targets: una lista de los render attachments
		- format: cada uno tiene su formato..?