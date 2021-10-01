### Que es?
Una expansion de [[Gauss seidel]] para que resuelva problemas complementarios lineales, concretamente el No lineal [[Problemas Complementarios]]

### Diferencias
Se trata del metodo de Gauss-Seidel, pero con un ultimo paso de proyeccion entre 2 valores(Menos y mayor), de ahi que se llama Gauss-Seidel proyectado

### Parametros
- Matrix A: representacion del sistema lineal
- Vector b: solucion esperada del sistema lineal
- Vector maximos: contiene los maximos de las contraints para el paso de proyecccion
- Vector minimos: igual que magimos pero con minimos

### Algoritmo
Es exactamente igual que el metodo de Gauss Seidel, calculando cada paso como:
$$ x_i ^ {k+1} = \frac 1 {a_{ii}} (b_i - \sum_{j=i}^{i-1}{ a_{ij} x_j ^{k + 1}} - \sum_{n}^{j=i+1}{ a_{ij} x_j ^{k}}) $$
Pero anadiendo un paso de reproyeccion despues
$$ 1)  tx_i ^ {k+1} = \frac 1 {a_{ii}} (b_i - \sum_{j=i}^{i-1}{ a_{ij} x_j ^{k + 1}} - \sum_{n}^{j=i+1}{ a_{ij} x_j ^{k}}) $$
$$ 2) x_i ^ {k+1} = Max(Min(tx_i^{k+1}, minimun_i), maximun_i) $$

### Referencia
https://gist.github.com/erwincoumans/6666160
https://box2d.org/files/ErinCatto_IterativeDynamics_GDC2005.pdf