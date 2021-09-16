### Que es?
Un metodo iterarativo de raiz, para aproximar los valores de una funcion real.

### Como?
Dada una funcion $f(x)$, usando un valor inicial $x_0$ y la derivada de la funcion $f'(x)$a la que encontrar la raiz.
$$ x_0 = x_0 - {f(x_0)}/{f'(x_0)} $$
O generalizando: 
$$ x_{n+1} = x_{n} - {f(x_{n})}/{f'(x_{n})} $$

### Problemas practicos
- Es posible que no converja, y antes habria que hacer una prueba
- "Pasarse"
- Puede lelgar al punto estacionario y fastidiar la simulacion al dividir por 0
- Uso de un malo estado inicila puede dificiultar mucho la convergencia.
- Convergencia lenta: es un metodo sencillo, pero por ello sufre