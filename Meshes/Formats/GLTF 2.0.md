Formato muy modular y flexible para almacenar meshes, materiales Y escenas de 3D.

### Por encima
Escrito en JSON, con distintos modulos para describir los distitos apartados de una escena 3D

# Representar una escena
## Scene
El elemento raiz del GLTF es un array que enumera los Nodos que forman esta escena.
## Nodes
Cada Nodo tiene una mesh asignada (a modo de indice), y determinados elementos como la posicion (vector 3D), escala (Idem), o la rotacion (quaternion).

# Almacenar geometria
## Buffers
Formado por una URI y una longitud de esta, suele marcar el archivo en el que esta el binario de toda la informacion de la mesh; o puede ser una data URI, y tener los datos ahi embedidos.

 ### Bufferviews
Ya que en el buffer solo hay raw-data, y puede haber varias listas o tipos de informacion guardados ahi; como los vertices por un lado, o los indices por otro. O solo vertices.
Para diferenciarlo usamos las bufferviews, a las que en base de una longitud, un offset y un target (un codigo que representa el uso final, por ejemplo indec_buffer o geometry buffer).
Esto divide el buffer base, en varios sub-buffers, o bufferviews.

### Accessors
Ya que ahora tenemos divida los datos entrantes en varios buffers, ahora ahi que indicar como leerlo, y para eso usamos los accesores; que indican el formato (escalar, vec3, vec4, mat3...), el tipo (unsigned short, int, float..), el numero de instancias, y valores maximos y minimos que tendran los valores a leer.

# Representar Geometria
## Meshes
En el elemento raiz meshes enumeran las distintas meshes que ahi en la escena y cada una esta compuesta por sus primitivos y mas informacion:

### 1) Primitivos
Asocian los accesores con las meshes:
"atributes": enlazan los accesors con las propiedades, como por ejemplo:
	 {"POSITION" : 1,  "NORMAL": 2}
	 Indican que la position esta en el accesor 1, y se tiene que tomar la normal del accesor 2.
	  Esto indica que la geometria pura con la que renderizamos deveria ser una lista en la que cada vertice se define por 1 vector de postion y otro normal.
	  
### 2) Modo de renderizado
"mode": indica el tipo de primitivo que devera renderizar, a-la triangulos, puntos y demas. Por defetco se infiera triangulos.

### 3 ) Indexado
"indices": indica que accesor es el que contiene los indices (SI HAY). En caso de que no se usen indices para el renderizado, este elemento no estara.

### 4) Material
Si esta, indica el indice perteneciente al material del objeto.

# Almacenar texturas
Una textura se represetna por asociar un sampler con una fuente
## 1) Fuente/Source
El elemento de source hace referencia a la imagenes en "images", el cual almacena una lsita de URIs (que pueden ser raw data de texturas pero...).
## 2) Samplers
Definen como se va a leer la textura una vez cargada en memoria:
- Filtrado
- Wrapping
- Etc
Estos valores corresponden a valores de Opengl

# Representacion de Materiales
Un lsitado en el que estan almacenados todos los materiales.
En function de la las extensiones que se usen, pueden darse otros tipos, pero generalmente solo estan con el tipo "pbrMetalicRoughness".

## "pbrMetallicRoughness"
Se puden agregar valores directamente a los materiales:
- "baseColorFactor" un vec4 que contenga un color
- "metallicFactor" un float
- "roughnessFactor" un float
Pero tambien se puede enlazar con una textura.
- "baseColorTexture"
- "metallicTexture"
- "roughnessTexture"
Y se le tiene que agregar un entero que lo relacionara con la textura adecuada.

## "pbrSpecularGlossines"

## Valores por separado:
- Normal
- Especular
- Emisividad
- Oclusion
- Modo de alpha (blending)
- Unlit: Si la luz no le afecta o no..?
- Sheen (?)

# TODO
- Camaras
- Morphs
- Animaciones
-  Skins
-  Uso
- tagging a los elementos para construir escenas
- Anadir datos miscelaneos a los nodos 


# Como usarlo

## 1) Por cada Bufferview
Se generera un VBO o un EBO, que almacena los datos

## 2) Por cada Mesh
Generamos el VAO
Tomamos los VBOs asociados con cada uno y generamos los atribs arrays en funcion
de lo definido en cada primitivos
Asociamos el EBO tambien a el VAO actual
Y generamos una... render instance que relecione el VAO, elemento y demas

## 3) Por cada textura
La almacenamos (? si lo requerimos..?)

## 4) 


Asociado a cada VAO a la hora de dibujarlo esta un shader, con sus uniforms y varios VBOs y sus correspondientes EBOs

Los atribis pueden dar distintas partes de un buffer, o mezplar distintos buffers