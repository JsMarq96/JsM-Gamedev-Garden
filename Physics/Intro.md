## Motores de fisica
Sistemas que simulan comportamientos fisicos en tiempo real

### Como?
Constan de varias partes:
- Deteccion de colisiones
- Resolucion de colisiones
- [[Constraints (Limitaciones)]]


### Deteccion de Colisiones
Se dividen en 2 pasos:
1) Broadphase: busqueda de contactos poco precisa, solo para ver que cuerpos "se pueden" estar tocando. (Ya que la siguinete fase es mas dura computacionalmente, eso nos lo ahorra)
2) Narrowphase: busqueda de contacto muy precisa.

Este proceso tiene 1 objetivo, detectar si 2 objetos se estan tocando y extrar la informacion del contacto (en caso de que haya) y alamcenarla en un manifold de colisiones.


### Resolucion de colusiones
Aplica las correcciones para que los objetos se comporten como deverian mediante una simulacion, y siguiendo las limitaciones implicitas en las constraints.

Este proceso se puede modelar de mucahs maneras, pero la mas comun es usar impulsos (cambios de velocidad en una direccion, y aolicado en un pto a cada objeto).

Para el calculo de estos impulsos se usara un sistema de [[Solvers/Intro]] ya que en su mayoria son sistemas no lineales.

### [[Constraints (Limitaciones)]]
Es el equivalente de los shaders para el motor grafico, pero para el motor de fisica.
Son funciones escalres que cuando se cumplen dan 0.