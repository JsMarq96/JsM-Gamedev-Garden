### Que es
Un metodo iterativo para conseguir una solucion de un sistema de equaciones lineal para resolver los  [[Problemas Complementarios]]

### Parametros
- A: el sistema lineal represetnado como un sistema de ecuaciones
- b: el vector de la solucion esperada

### Preambulos
El algoritmo se basa en la triangulacion estricta que es, dado una matriz A:
$$A = \begin{pmatrix} 
a_{0,0} & a_{0,1} &a_{0,2} \\ 
a_{1,0} & a_{1,1} &a_{1,2} \\ 
a_{2,0} & a_{2,1} &a_{2,2} \\  \end{pmatrix}$$

$$L_* = \begin{pmatrix} 
a_{0,0} & 0 & 0 \\ 
a_{1,0} & a_{1,1} & 0 \\ 
a_{2,0} & a_{2,1} &a_{2,2} \\  \end{pmatrix}
U_* = \begin{pmatrix} 
0 & a_{0,1} &a_{0,2} \\ 
0 & 0 &a_{1,2} \\ 
0 & 0 & 0 \\  \end{pmatrix} $$

$$A = L_* + U_*$$

De esta manera, el sistema a resolver $Ax = b$ se puede representar como:
$$L_* x = b - Ux$$
Haciendo una sustitucion, conseguimos que
$$x = L_*^{-1} (b - U_* x)$$
Y si esto, lo aproximamos como si fuese un metodo iterativo, para calcular $x^{k+1}$ siendo k el paso en el tiempo, tenemos:
$$x^{k+1} = L_*^{-1}(b - U_* x^k)$$

Pero como L y U son matrices triangulares, podemos usar el metodo de "forward substitution" (?), para simplificar los calculos, y calcular todos los valores de x secuencialmente:

$$ x_i ^ {k+1} = \frac 1 {a_{ii}} (b_i - \sum_{j=i}^{i-1}{ a_{ij} x_j ^{k + 1}} - \sum_{n}^{j=i+1}{ a_{ij} x_j ^{k}}) $$

Esto se itera hasta que se ha converge o se delimitan las iteraciones