# Inizialicacion y Setup
Para inicializar WebGPu requerimos de un GPUAdapter y un GPUDevice; siendo un Adapter representa la implementacion de WebGPU en el sistema, que lista las capacidades y demas de la instancia actual.
GPUDevice es lo que indica, una instancia que representa nuestra GPU, que conseguimos mediante el adapter; y un adapter puede tener mas de 1 GPU.

		Nota: puede que los disitntos devices de WebGPU tengan distintas "capacidades..."

## Proceso
1) Conseguir adapter (asincrono)
2) Conseguir el device del Adapter (asincrono)
3) (Si es necesario) Generar un Convas o contexto para dibujar los graficos
	1) Generar una GPUSwapChain en un dispositivo y con un formato concreto


## Ejemplo de Compute
 wv