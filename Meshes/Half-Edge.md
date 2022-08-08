A la hora de almacenar meshes se teine que tener en cunta 2 cosas:
-	Facilidad de renderizado
-	Facilidad de calculo
Ya que es posible que no solo tengamos que representarlar, si no que tambien tendriamos que ejectuar algun calculo sobre ellas (como fisicas por ejemplo).

Generalmetne se suele usar una Sopa de poligosonos, que amlacena los vertices y luego los referencia con una lsita de indices, lo cual no es optimo para usar de calculo, asi que vamso a ver que tal el Half-Edge

## La Idea basica
Ademas de tener la tipica informacion, que son los vertices, los ejes y las caras, tambien incorporaremos un half-edge, que hara de enlace entre diferentes elementos de las mesehs.
![[half-vertex_img.jpg]]

Es como una linked list de elementos, que nos ayuda a transversar los elementos de la mesh

## Estructura:
Por cada elemento, un vertice, un borde o una cara, se le asocia un half edge, que apunta a el siguiente half edge, y a su "gemelo".

De esta manera, podemos iterarpor la mesh por todos los half edge y cuando acavabmos con el que empezamos, vamos a su "gemelo" y repetimos el proceso.