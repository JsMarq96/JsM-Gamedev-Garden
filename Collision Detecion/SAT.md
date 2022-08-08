# SAT
## Separating Axis Theorem

## 3D
A la hora de ejecutar un test SAT sobre 2 cuerpos en 3D, ahi que hacer un cambio con respecto a 2D: probar tambien las esquinas

### Test de Esquinas
Ya que en 3D se tienen 3 angulos de libertad mas, hay que generar normales extra sobre las que probar.
Las generamos usando un cross prod entre todas las normales de los 2 objetos.
OJO: ya que en un cubo las normales estan en direccion opuestas, solo hay que probar 3 direcciones vs 3 direcciones positivas de cada cuerpo.

### Clipping
Clipping se complica un poco,a andiendo mas casos
- Cara a cara, sutherland-hogdman clipping (Done)
- Cara a vertice: interseccion interior (pseudo done)
- Vertice a vertice: interseccion entre 2 lineas

Para diferenciar entre los distintos algoritmos de clipping, SAT deve de ser consciente de que noramles se estan porbando entre ellas