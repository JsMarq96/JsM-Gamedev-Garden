### Que es?
Una funcion escalar que representa una limitacion en un sistema fisico.
Cuando la funcion da 0, es que la constraint esta siendo cumplida.

Existen varios tipos de constraints:
- Veolcidad
- Posicion

### Forma general de constraints de velocidad
$$[J_{v1} J_{v2}] [V_x V_y] + b = 0$$
$$JV + b = 0$$

Siendo $J_{vx}$ la jacobiana de la velocidad y b el termino de baumngarte

### Como se resuelve las constraints de velocidad (Impulsos secuenciales)?
$$M(V_2 - V_1) = L\lambda$$
Siendo V2 la nueva velocidad y V1 es la vieja (?) y M la [[Matriz de Masa]]

TOmando la ecuacion podemos acabar con una solucion
$$V_2 = V_1 + M^{-1} J^t \lambda$$
Ahora bien como V2 es la velocidad que hace que la osntraint de 0, , tomamos la ecuacion base y sustituimos
$$J(V_1 + M^{-1} J^t \lambda) + b = 0$$
Por lo que
$$(J M^{-1} J^t)\lambda = -(J V_1 + b)$$
De esa manera, podemos concluir en que lambda
$$\lambda = \frac{J V_1 + b} {(J M^{-1} J^t)}$$

El divisor es llamado masa efectiva y lambda se trata como un [[Multiplicador de Lagrange]]

### Aplicar el resultado
Se puede aplicar a modo de un impulso, un cambio de valocidad, en el que $\lambda$ es la magnitud de la velocidad, y se usa una normal para marcar la direccion y un punto de en el cual aplicarlo, para modificar tambien la velocidad rotacional

### Resolver varias constraints de una iteracion
Se pueden amontonar las J, al iugal que el metodo de baumgarte, siguiendo esta manera:
$$J = [ J_1 J_2]$$


### Como se resuelve las constraints usando Solvers genericos?
Para ello se deveran primero calcular el sistema lineal, la matriz b; y el vector de maximo y minimos, si se trata de Gauss Seidel proyectado.
Usando el calculo lagrangiano sepodria calcular los maximos y minimos para la proyeccion
