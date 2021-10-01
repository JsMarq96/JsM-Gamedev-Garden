### Que es?
En una constraint, representa la masa y la inercia de 2 cuerpos, contenidos por las contraints.

### Forma
$$M = \begin{pmatrix} 
m_a & 0 & 0 & 0\\ 
0 & I_a & 0 & 0 \\ 
0 & 0 & m_b & 0 \\
0 & 0 & 0 & I_b\end{pmatrix}$$
Y si se invierte, se aplica la inversion solamente a la diagonal
$$M ^{-1} = \begin{pmatrix} 
m_a^{-1} & 0 & 0 & 0\\ 
0 & I_a^{-1} & 0 & 0 \\ 
0 & 0 & m_b^{-1} & 0 \\
0 & 0 & 0 & I_b^{-1}\end{pmatrix}$$

### Diferencias 2D y 3D
A la hora de aplicar la matriz de masa en simulaciones de 2D y 3D, ahi que tener en cuenta que el valor de inercia es una matriz de 4x4 llamada el tensor de inrcia, que describe la resistencia de un objeto a ser movido.
$m_a$ y $m_b$ son matrices cuya diagonal es el valor de la masa, y el resto son zeros.

$$M = \begin{pmatrix} 
m & 0 & 0 & 0\\ 
0 & m & 0 & 0 \\ 
0 & 0 & m & 0 \\
0 & 0 & 0 & I\end{pmatrix}$$