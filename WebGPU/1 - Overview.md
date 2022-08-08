## Estructura
WebGPU funciona por command buffer, en vez de usar un Modo inmediato para comunicarse con la GPU, sreializando todos los estados u enviandolos en distintos comands buffers:

Puede ser 
- Render pass
- Copmute pass

### Que tiene un command buffer?
A partir de un comand encoder:
	- Empezamos un render pass
	- Xonfiguramos el estado
	- Configuramos la pipeline
	- dibujamos
	- Config extra si enecesaria
	- Terminamos
Y en el caso de un command encoder de Compute:
	- Empezamos un compute pass
	- Configuramos la pipeline
	- Dispatch
	- terminamos

Luego reunimos todos los comand buffers y los pasamos a una cola; y se iran ejecutando.



## Buffers & Memoria
Dado que ambas pipeline usaran datos que meteremos y generaremos en buffers, hay que tenr en cuenta que WebGPU maneja 2 tipos de memoria:
- En la CPU
- En la GPU (las texturas solo pueden exisitir dentro de la GPU)

### Crear Buffers
Creas los buffers asociadas a un dispositivo, espeficicando un tamano, y su uso:

	device.createBuffer({ size: whatever_bytes, usage: <options> })

Esas opciones de uso son:
- MAP_READ & MAP_WRITE: cuando se llena o se lee usando funcion de mapeo (?)
- COPY_SRC & COPY_DST:  para acceder usando funciones de copia o lectura (writeBuffer o copyBufferToBuffer y demas)
- INDEX: index buffer, si se pasa con setIndexBuffer
- VERTEX: como buffer de vertices si se pasa como setVertexBuffer()
- UNIFORM: como un buffer de uniformes, de datos que se han pasado por un bufferBindingLayout (??)

## Mapeo de memoria
Cuando se mapea una porcion de memoria, se esta haciendo disponible para el CPU, pudiendo leerlo o escribirlo, al tener el ownesrhip de esta memoria (un poco a lo Rust, la GPU no puede accederlo hasta que se llama a el unmap)

- MappedRange: el rango de memoria mapeada del buffer; del tipo ArrayBuffer, y accediendolo podemos subir o leer info de la memoria de la GPU.

### Escribir datos a un buffer: WriteBuffer
Generalmente para pasar datos a la memoria de la GPU lo prefereible es usar writeBuffer, porque:
- Es mas natural a la hora de tratar con WASM
- Mas sencilla de cara a complejidad
- Configura el buffer inmediatamente
- Si tu data ya esta como un arraybuffer, te ahorras el alojamiento o copia de un array buffer mapeado

Los buffers estan definidos dentro un device, pero la manipulacion de este (lectura y escritura) se tiene que hacer mediante una cola:

	device.queue.writeBuffer(<dest-buffer>, <buffer-offset>, <data>, <data-offset>, size)

