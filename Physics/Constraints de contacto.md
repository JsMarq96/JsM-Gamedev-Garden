Dada una colision, compuesta por:
- Una normal de colision (indica una direccion) $n$
- Puntos de contacto entre 2 figuras
- Profundidades de los ptos de contacto
- Velocidades de los objetos
- Masas de los objetos

Definimos las partes de la constraint en funcion de [[Constraints (Limitaciones)]]
### Partes
$$JV+b \geq 0$$
La velocidad V es
$$V = \begin{bmatrix} V_a \\ \omega_a \\ V_b \\ \omega_b \end{bmatrix}$$
Siendo $\omega$ la velocidad angular de cada objeto.
Ahora definimos J como una amtriz de 12 x 1

$$ J_n = \begin{bmatrix} -n^T & (-r_a \times n)^T & n^T & (r_b \times n)^T \end{bmatrix}$$

$r_a$ y $r_b$ son vecotres que van desde el centro de masa hasta el punto de contacto.

### Clamping
Ya que esta es una constraint de desigualdad superior (?), la suma de todas las $\lambda$ deve de ser superior o igual a 0, asi que se hace un paso de clamping antes de inyectar las velocidades.

### Correccion de Errores
Para estabailizar la constraint y penalizar el incumplimeto, se implementa la correccion de Baumbarte

### Friccion
En vez de obtener la $\lambda_n$, para la constraint normal, se busca obtener la $\lambda_{t_n}$ para la tangente n.
Para resolver la friccion se resuelve como 2 constraints mas, en la que la Jacobiana biene dada por los 2 vectores tangentes (vease [[Friction]])

$$ J_{t1} = \begin{bmatrix} -t_1^T & (-r_a \times t_1)^T & t_1^T & (r_b \times t_1)^T \end{bmatrix}$$

$$ J_{t2} = \begin{bmatrix} -t_2^T & (-r_a \times t_2)^T & t_2^T & (r_b \times t_2)^T \end{bmatrix}$$

Pero ahi que anadir un paso mas, multiplicando por un termino de friccion, ya que

$$ -\mu\lambda_n \leq \lambda_t \leq \mu\lambda_n$$
Y se ha de manter la desigualdad.
El $\mu$ es el valor de la friccion, y aunque tecinamente se tiene que usar 2 valores distintos para la friccion estatica y de movimiento, en estas simulaciones se suele hacer con uno solo.