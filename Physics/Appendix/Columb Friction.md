Modelo empirico para aproximar la perdida de energia de un sistema.
Nos centramos en el modelado de friccion seca.
La base del modelo esta en la inecuacion
$$F_f \leq \mu F_n$$
Es decir dada una fuerza normal que se aplica opuesta a una fuerza por un objeto, la fuerzad e friccion no deve de ser menor que el coefienicente de fricciond e los materiales.
De cara a el model empirico, si la velocidad de deslizacmiento es 0, entonces la friccion tangencial es menor o igual que $\mu$ veces la fuerza normal (a).
Pero si la velocidad no es 0, entonces la firccion de magnitud es la fuerna normal opuesta a la direccion de deslizamiento (b).
$$ a) v = 0: F_t \leq \mu F_n $$
$$ b) v \neq 0: F_t = -\mu F_n v \cdot speed norm $$

Una expansion de esto es definir el termino $\mu$ como 2 coeficieintes destitnas, en funcion de si el objeto se esta desplazando o no; $\mu_s$ para cuando es un cuerpo estatico y $\mu_k$ para cuando esta en movimiento.
Generalmetne:
$$\mu_s > \mu_k$$
esto hace que cuando se esta parado. cueste ams energia el empezar a overse, pero una vez se empiece a mover la resistencia disminuya.

Generlamtne los valores de $\mu$ son de {0, 1}

El grupo de todas las fuerzas que se transmitern mediante la friccion de Coulumb se puede representar como un cono de friccion
![[mass-fric.png]]

Como se puede ver, esta formado por por un eje, marcado por la direccion
de la fuerza normal, y una anchura marcada por el angulo entre la fuerza normal y la direccion de la fuerza tangente
El radio de este cono, es la magnitud de la fuerza producida por la friccion
![[Cone-of-Friction.png]]
El angulo de la friccion $\theta$, que describe la anchura del cono viene dado por:
$$\theta = tan^{-1} \mu$$

Los extremos del cono, son vectores que representan todas las fuerzas de friccion.
Esto, si se trata de un sistema de 2 dimensiones es sencillo, ya que se trata de 2 vectores o 2 fuerzas, pero cuando se trata de espacios de 3 Dimensions, lo normal es aproximar el cono (de lados infintesimos) como un plohedro piramidal, de vectores finitos.
Estos vectores se pueden llamar wrenches
![[2-Figure1-1.png]]

Refenrecias:
https://modernrobotics.northwestern.edu/nu-gm-book-resource/12-2-1-friction/