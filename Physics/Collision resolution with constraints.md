Partimos de que para solucionar un contacto entre 2 objetos emplearemos las sigueintes  [[Constraints de contacto]]
- Constraint de contacto normal para Obj1
- Constraint de constacto normal para Obj2
- Constraint de friccion para Obj1
- Constraint de friccion para Obj2

E intentaremos solucionarlas a la vez

### Matriz Jacobiana
Cada fila de la matriz es una constraint y se intentara resolver como un sistema
Ten en cuenta que las constraints de friccion son 2 constraints, un por cada vector tangente [[Columb Friction]]

$$ J = \begin{pmatrix} J_{N_1} \\ J_{N_2} \\ J_{F_{1_1}} \\ J_{F_{1_2}} \\ J_{F_{2_1}} \\ J_{F_{2_2}} \end{pmatrix} $$

Ya que una fila Jacobiana esta compuesta por 3 componentes de 3 valores, sera tratado como un vector de 1x12, asi que la matrix completa sera de 12x6

### Constraint de contacto
$$ J_N = \begin{pmatrix} -n^T && -(r_1 \times n)^T && n^T && -(r_2 \times n)^T) \end{pmatrix}$$
### Constraint de Friccion
$$ J_F = \begin{pmatrix} -u^T && -(r_1 \times u)^T && u^T && -(r_2 \times u)^T) \end{pmatrix}$$

### Resolver las contraints
Intentaremos resolverlo usando el Metodo de PGS (gauss seidel proyectado) [[Non-Linear Gauss Seidel aka Gauss-Seidel proyectado]].
Para ello, necestiamos:
- Una matriz A que represente el sistema lineal.
- Un vector B, que representa la velocidad de entrada
- Vectores de maximos y minimos, para "proyectar" o clampear la $\lambda$ resultante.

En este caso:
$$ A = J M^{-1} J^T$$
$$ b = \begin{pmatrix} V_1 \\ \omega_1 \\ V_2 \\ \omega_2 \end{pmatrix} $$
Y los amximos y minimos dependen de la constrant (seguro??)

Una vez tengamos esto tal cual, podemos calcular el resultado a lo largo de varias iteraciones como en [[Non-Linear Gauss Seidel aka Gauss-Seidel proyectado]]

### Que necesito?
- Calcular matrices de 12x6 y 12x12
- Multiplicar estoas 2 matrices. Done (to test)
- Trasponer una de estas matrices. Done
- Calcular Matriz de Masa
	- 6 rows por cada cuerpo de contraint,
	- Matriz cuadrada
	- Nosotros: 12 x 12
- Gauss-Seidel
- Una constraint por cada pto de contact
	- Una matriz por cada objeto...? o por cada pto de contacto
- Valores de la proyeccion: (Paper de Erin Catto Ecuacion 14) (Done!) 
	- Dependen del tipo de constraint:
		- Inecualidad $[0, \infty]$ Constraint de Contacto normal!!
		- Ecualidad $[-\infty, \infty]$
		- Friccion: $[-\mu m , \mu m]$ siendo $\mu$ la constante de friccion y m la masa