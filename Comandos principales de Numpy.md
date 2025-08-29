¿Qué es NumPy?
NumPy es el paquete fundamental para la computación científica en Python. Es una biblioteca de Python que proporciona un objeto de matriz multidimensional, varios objetos derivados (como matrices y matrices enmascaradas) y una variedad de rutinas para operaciones rápidas con matrices, incluyendo operaciones matemáticas, lógicas, manipulación de formas, ordenamiento, selección, E/S, transformadas discretas de Fourier, álgebra lineal básica, operaciones estadísticas básicas, simulación aleatoria y mucho más.

1) Matrices (arrys) en Python

Los arrays son la base de toda la ciencia de datos en Python. Las matrices pueden ser multidimensionales, y todos los elementos de una matriz deben ser del mismo tipo, todos enteros o todos flotantes, por ejemplo.

Ventajas de utilizar una matriz
Las matrices pueden manejar con eficacia conjuntos de datos muy grandes
Eficiencia computacional y de memoria
Cálculos y análisis más rápidos que las listas
Funcionalidad diversa (muchas funciones en paquetes Python). Con varios paquetes de Python que facilitan la modelización de tendencias, la estadística y la visualización.
Conceptos básicos de una matriz
En Python, puedes crear nuevos tipos de datos, llamados arrays, utilizando el paquete NumPy. Las matrices NumPy están optimizadas para análisis numéricos y contienen un único tipo de datos.

Primero se importa NumPy y luego se utiliza la función array() para crear un array. La función array() toma una lista como entrada.

Ejemplo:

# Importamos la librería NumPy y le damos el alias "np" 
# (esto es una convención muy usada en Python).
```python
import numpy as np
```

# Definimos una lista de precios de acciones (valores en flotante).
prices = [170.12, 93.29, 55.28, 145.30, 171.81, 59.50, 100.50]

# Definimos una lista con las ganancias correspondientes 
# (también valores decimales).
earnings = [9.2, 5.31, 2.41, 5.91, 15.42, 2.51, 6.79]

# Convertimos la lista de precios en un arreglo de NumPy.
# Esto permite hacer operaciones matemáticas de manera más rápida y eficiente.
prices_array = np.array(prices)

# Convertimos la lista de ganancias en un arreglo de NumPy.
earnings_array = np.array(earnings)

# Imprimimos el arreglo de precios.
```python
print(prices_array)
```

# Imprimimos el arreglo de ganancias.
```python
print(earnings_array)
```


2) NumPy reshape

La función numpy.reshape() permite remodelar un array en Python. Remodelar significa, básicamente, cambiar la forma de un array. La forma de un array está determinada por el número de elementos en cada dimensión.

La remodelación permite añadir o eliminar dimensiones en un array. También podemos cambiar el número de elementos en cada dimensión.

Sintaxis y parámetros
Aquí está la sintaxis de la función:

numpy.reshape(array, shape, order = 'C')


matriz: matriz de entrada.

forma: Números enteros o tuplas de números enteros.

Orden: C-contiguo, F-contiguo, A-contiguo; este parámetro es opcional. El orden "C" significa que las operaciones de subida por filas en el array serán ligeramente más 
rápidas. El orden "F" significa que las operaciones por columnas serán más rápidas. "A" significa leer/escribir los elementos en orden de índice similar a Fortran.

Valor de retorno: una matriz que se reformatea sin realizar ningún cambio en sus datos.

Ejemplo

# Importamos la librería NumPy con el alias "np"
```python
import numpy as np
```

# Creamos un arreglo con valores desde 0 hasta 19 (20 elementos en total)
# np.arange(20) genera una secuencia de enteros consecutivos desde 0 hasta 19
```python
x = np.arange(20)
```
        
# Imprime el arreglo completo con sus elementos
```python
print(x)
print()   # Salto de línea para separar la salida visualmente
```
        
# Imprime la forma (shape) del arreglo
# En este caso, (20,) significa que es un arreglo de UNA dimensión con 20 elementos
```python
print(x.shape)
print()
```
        
# Imprime el número de dimensiones (ndim) del arreglo
# Como es un vector (arreglo unidimensional), devuelve 1
```python
print(x.ndim)
```


En este caso, los números [0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19] son ​​los elementos del array x. La salida (20,) es la forma del array. Finalmente, el valor 1 impreso indica la dimensión del array.

Para probar la función de remodelación de numpy, necesitamos especificar el array original como primer argumento y la forma del segundo argumento como una lista o tupla. 

# Importamos la librería NumPy
```python
import numpy as np   
```

# Creamos un array con valores enteros del 0 al 19
# np.arange(20) genera números desde 0 hasta 19 (20 elementos en total)
```python
x = np.arange(20)   
```

# Imprime el array completo
```python
print(x)
```

# Línea en blanco para separar visualmente
```python
print()  
```

# .shape devuelve la forma (shape) del array
# Como es un vector de 20 elementos en una sola dimensión → (20,)
```python
print(x.shape)
```

# Línea en blanco
```python
print()  
```

# .ndim devuelve el número de dimensiones del array
# Como x es un vector (no una matriz) → tiene 1 dimensión
```python
print(x.ndim)
```

# Ahora reestructuramos el array con np.reshape
# np.reshape(x, [2, 2, 5]) reorganiza los mismos 20 elementos en un arreglo 3D:
# - 2 bloques
# - cada bloque con 2 filas
# - y cada fila con 5 columnas
```python
print(np.reshape(x, [2, 2, 5]))
```

Por lo tanto, un intento como print(np.reshape(x, [5,6])) generará un ValueError. Esto se debe a que no podemos transformar un array de tamaño 20 en la forma (5,6).

3) Numpy concatenate

La función numpy.concatenate() combina varios arrays en uno solo a lo largo de un eje específico. Esta función es especialmente útil al trabajar con grandes conjuntos de datos o al realizar operaciones que requieren la fusión de datos de diferentes fuentes. A diferencia de otras funciones de unión de arrays, como numpy.vstack() o numpy.hstack() , que solo unen arrays vertical u horizontalmente, numpy.concatenate() ofrece mayor flexibilidad al permitir especificar el eje a lo largo del cual se unirán los arrays.

Sintaxis

La sintaxis de la función numpy.concatenate() es la siguiente:

numpy.concatenar((matriz1, matriz2, ...), eje=0, salida=Ninguno, tipod=Ninguno)

Parámetros:

Arrays: Una secuencia de arrays de entrada que se concatenarán. Estos arrays deben tener la misma forma en todos los ejes, excepto en el especificado por el eje.

Eje: El eje a lo largo del cual se unirán las matrices. El valor predeterminado es 0 (el primer eje).

salida: si se proporciona, el resultado se colocará en esta matriz.

dtype: anula el tipo de datos de la matriz de salida.

Características principales de numpy.concatenate()

Especificación de eje flexible : puede concatenar matrices a lo largo de cualquier eje, lo que lo hace versátil para datos multidimensionales.

Compatibilidad de datos : las matrices deben tener formas coincidentes en todos los ejes excepto en el que se está concatenando.

Uso eficiente de la memoria : la función crea una nueva matriz pero comparte los datos subyacentes de las matrices de entrada cuando es posible.

Admite dimensiones superiores : funciona fácilmente con matrices 1D, 2D y de dimensiones superiores.

Ejemplo 1: Concatenación de matrices 1D

Supongamos que tiene dos matrices 1D y desea combinarlas en una sola matriz.


# Importamos la librería NumPy con el alias "np"
```python
import numpy as np
```

# Creamos el primer arreglo unidimensional con 3 elementos
```python
arr1 = np.array([1, 2, 3])
```

# Creamos el segundo arreglo unidimensional con 3 elementos
```python
arr2 = np.array([4, 5, 6])
```

# Usamos la función concatenate() de NumPy para unir ambos arreglos
# El resultado será un nuevo arreglo que contiene los elementos de arr1
# seguidos de los elementos de arr2
```python
result = np.concatenate((arr1, arr2))
```

# Imprimimos el resultado de la concatenación
```python
print("Result:", result)
```



Ejemplo 2: Concatenación de matrices 2D a lo largo de filas (eje=0)

Para matrices 2D, puede concatenar a lo largo de filas (comportamiento predeterminado) o columnas
# Importamos la librería NumPy con el alias "np"
```python
import numpy as np
```

# Creamos el primer arreglo (matriz 2x2)
# Tiene 2 filas y 2 columnas
```python
arr1 = np.array([[1, 2], 
```
                 [3, 4]])

# Creamos el segundo arreglo (matriz 1x2)
# Tiene 1 fila y 2 columnas
```python
arr2 = np.array([[5, 6]])
```

# Concatenamos ambos arreglos a lo largo del eje 0 (filas)
# Esto significa que arr2 se añade como una nueva fila debajo de arr1
```python
result = np.concatenate((arr1, arr2), axis=0)
```

# Imprimimos el resultado en formato de matriz
```python
print("Result:\n", result)
```
4) NumPy operaciones básicas
 Numpy ofrece todo lo necesario para obtener un buen rendimiento cuando se trata de hacer cálculos con arrays. Por como está concebida la biblioteca es una de sus principales virtudes si lo comparamos con los cálculos que pueden realizarse en Python con otras estructuras de datos como listas, tuplas y diccionarios.

Numpy permite realizar la misma operación aritmética con cada elemento de un array por separado y operar con arrays de igual o distintas dimensiones.

También cuenta con funciones matemáticas que abarcan distintas necesidades para operar con todos los elementos de un array o por ejes, sin olvidar el cálculo a nivel binario, estadístico y con números reales.

Operaciones aritméticas con un mismo valor

Con Numpy se puede operar un mismo valor con todos los elementos del array, elemento a elemento, utilizando los símbolos matemáticos: + (sumar), - (restar), * (multiplicar), / (dividir), // (dividir, cociente como entero), ** (potenciación).

```python
import numpy as np
```

# Creamos un arreglo 2D (matriz de 2 filas x 3 columnas)
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```

# SUMA: se suma 1 a cada elemento del arreglo
```python
a = a + 1
print(a)
```
# Resultado:
# [[2 3 4]
#  [5 6 7]]
# Creamos nuevamente el arreglo inicial
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```
# RESTA: se resta 1 a cada elemento del arreglo
```python
a = a - 1
print(a)
```
# Resultado:
# [[0 1 2]
#  [3 4 5]]
# Volvemos a crear el arreglo original
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```
# MULTIPLICACIÓN: cada elemento se multiplica por 5
```python
a = a * 5
print(a)
```
# Resultado:
# [[ 5 10 15]
#  [20 25 30]]
# Nuevo arreglo original
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```
# DIVISIÓN REAL: cada elemento se divide entre 2
# El resultado puede ser decimal (float)
```python
a = a / 2
print(a)
```
# Resultado:
# [[0.5 1.  1.5]
#  [2.  2.5 3. ]]
# Nuevo arreglo original
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```
# DIVISIÓN ENTERA: cada elemento se divide entre 2
# pero solo se conserva la parte entera (sin decimales)
```python
a = a // 2
print(a)
```
# Resultado:
# [[0 1 1]
#  [2 2 3]]
# Nuevo arreglo original
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```
# POTENCIA: cada elemento se eleva al cuadrado (**2)
```python
a = a ** 2
print(a)
```
# Resultado:
# [[ 1  4  9]
#  [16 25 36]]


Operaciones con arrays con las mismas dimensiones

Los mismos símbolos matemáticos (+, -, *, /, //, **) también se pueden utilizar para realizar operaciones aritméticas con dos arrays con las mismas dimensiones, elemento a elemento.

```python
import numpy as np
```

# Creamos un array 2x3 con enteros de 8 bits (np.int8)
# int8: números enteros pequeños (-128 a 127)
```python
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
```

# Creamos un array 2x3 lleno de unos
# Por defecto np.ones() genera valores de tipo float64
```python
b = np.ones((2, 3))
```

# SUMA: como a es int8 y b es float64,
# NumPy convierte automáticamente ambos al tipo más "amplio"
# → en este caso float64, para evitar pérdida de información
```python
c = a + b
```

# Mostramos el array a
```python
print(a)
```
# [[1 2 3]
#  [4 5 6]]
# Se mantiene como int8

# Mostramos el array b
```python
print(b)
```
# [[1. 1. 1.]
#  [1. 1. 1.]]
# Es float64 (números decimales de doble precisión)

# Mostramos c (resultado de la suma)
```python
print(c)
```
# [[2. 3. 4.]
#  [5. 6. 7.]]
# Es float64 porque se mezclaron int8 + float64

# RESTA: ocurre lo mismo, el resultado también será float64
```python
c = a - b
print(c)
```
# [[0. 1. 2.]
#  [3. 4. 5.]]

Operaciones con arrays de diferentes dimensiones

Es una característica avanzada de Numpy para realizar operaciones aritméticas con arrays de distintas dimensiones, elemento a elemento, utilizando los símbolos matemáticos (+, -, *, /, //, **). Estas operaciones son posibles cuando el array resultante tiene la misma dimensión que al menos uno de los arrays operados.

En el ejemplo siguiente el array a tiene 3 elementos por fila que coincide con el número de elementos del array b. Numpy para realizar el cálculo suma cada fila de a con los elementos de b, elemento a elemento:


```python
import numpy as np
```

# Creamos una matriz 3x3 llena de unos (dtype float64 por defecto)
```python
a = np.ones((3, 3))
```
# Resultado:
# [[1. 1. 1.]
#  [1. 1. 1.]
#  [1. 1. 1.]]

# Creamos un array 1D con 3 elementos
```python
b = np.array([1, 2, 3])
```
# Resultado:
# [1 2 3]

# Sumamos a + b
# Aquí ocurre el "broadcasting":
# - a es de forma (3,3)
# - b es de forma (3,)
# NumPy extiende automáticamente b a cada fila de la matriz a
# como si fuera:
# [[1 2 3]
#  [1 2 3]
#  [1 2 3]]
```python
c = a + b
```

```python
print(c)
```


En el ejemplo que sigue el array a tiene 3 elementos por columna que coincide con los elementos del array b. Numpy para realizar el cálculo suma cada columna de a con los elementos de b, elemento a elemento:

```python
import numpy as np
```

# Creamos una matriz 3x3 llena de unos
```python
a = np.ones((3, 3))
```
# a =
# [[1. 1. 1.]
#  [1. 1. 1.]
#  [1. 1. 1.]]

# ===================== CASO 1: Vector fila =====================

# Creamos un array 1D con 3 elementos (forma (3,))
b_fila = np.array([1, 2, 3])
# b_fila =
# [1 2 3]

# Sumamos a + b_fila
# Broadcasting:
#   - a tiene forma (3,3)
#   - b_fila tiene forma (3,)
# NumPy lo "extiende" por cada fila → (3,3)
c1 = a + b_fila
# Resultado:
# [[2. 3. 4.]
#  [2. 3. 4.]
#  [2. 3. 4.]]

```python
print("Resultado con vector fila:\n", c1)
```


# ===================== CASO 2: Vector columna =====================

# Creamos un array columna de forma (3,1)
b_col = np.array([[5], [10], [15]])
# b_col =
# [[ 5]
#  [10]
#  [15]]

# Sumamos a + b_col
# Broadcasting:
#   - a tiene forma (3,3)
#   - b_col tiene forma (3,1)
# NumPy lo "extiende" a lo largo de las columnas → (3,3)
c2 = a + b_col
# Resultado:
# [[ 6.  6.  6.]
#  [11. 11. 11.]
#  [16. 16. 16.]]

```python
print("\nResultado con vector columna:\n", c2)
```


# ===================== RESUMEN DEL BROADCASTING =====================
# - Si el array b es (3,), se expande como una fila repetida → suma por FILAS
# - Si el array b es (3,1), se expande como una columna repetida → suma por COLUMNAS



Funciones matemáticas (para operar con arrays)

add()

Sumar dos arrays, elemento a elemento.

```python
import numpy as np
```

# Creamos un array 2x3 de enteros (int8 = números enteros pequeños de -128 a 127)
```python
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos un array 2x3 lleno de unos
# Por defecto np.ones() crea valores tipo float64
```python
b = np.ones((2, 3))
```
# b =
# [[1. 1. 1.]
#  [1. 1. 1.]]

# Usamos la función np.add() para sumar ambos arrays, elemento a elemento
# Esto es equivalente a escribir: c = a + b
```python
c = np.add(a, b)
```

# Imprimimos el resultado
```python
print(c)
```
# Resultado:
# [[2. 3. 4.]
#  [5. 6. 7.]]
# Nota:
# - Cada elemento de "a" se suma con el elemento correspondiente de "b".
# - Como a es int8 y b es float64, NumPy convierte el resultado automáticamente a float64.


subtract()

Restar dos arrays, elemento a elemento.

```python
import numpy as np
```

# Creamos un array 2x3 de enteros (int8 = enteros pequeños entre -128 y 127)
```python
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos un array 2x3 lleno de unos
# np.ones() genera valores tipo float64 por defecto
```python
b = np.ones((2, 3))
```
# b =
# [[1. 1. 1.]
#  [1. 1. 1.]]

# Usamos np.subtract() para restar los arrays elemento a elemento
# Esto es equivalente a escribir: c = a - b
```python
c = np.subtract(a, b)
```

# Imprimimos el resultado
```python
print(c)
```
# Resultado:
# [[0. 1. 2.]
#  [3. 4. 5.]]
# Nota:
# - Cada elemento de "a" se resta con el correspondiente de "b".
# - Como "a" es int8 y "b" es float64, NumPy convierte el resultado a float64
#   para no perder información decimal (aunque aquí los resultados son enteros).


multiply()

Multiplicar dos arrays, elemento a elemento.

```python
import numpy as np
```

# Creamos el primer array 2x3 de enteros (int8)
```python
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos el segundo array 2x3 de enteros (int8)
```python
b = np.array([(2, 2, 2), (3, 3, 3)], dtype=np.int8)
```
# b =
# [[2 2 2]
#  [3 3 3]]

# Usamos np.multiply() para multiplicar los arrays elemento a elemento
# Esto es equivalente a escribir: c = a * b
```python
c = np.multiply(a, b)
```

# Imprimimos el resultado
```python
print(c)
```
# Resultado:
# [[ 2  4  6]
#  [12 15 18]]
# Nota:
# - Se multiplican los elementos de "a" y "b" que están en la misma posición.
#   Ejemplo: (1*2), (2*2), (3*2), (4*3), (5*3), (6*3)
# - Ambos arrays tienen el mismo tipo de dato (int8), 
#   así que el resultado también es int8.


dot()

Multiplicar un array por un valor, elemento a elemento.

```python
import numpy as np
```

# Creamos un array 2x3 con enteros
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Multiplicamos el array por un valor escalar (4)
# Esto multiplica cada elemento de "a" por 4
```python
b = a * 4      # equivalente a np.multiply(a, 4)
```

# Imprimimos el resultado
```python
print(b)
```
# Resultado:
# [[ 4  8 12]
#  [16 20 24]]


Producto de dos arrays

En la teoría de matrices dos arrays se pueden multiplicar si el número de columnas de la primera coincide con el número de filas de la segunda.

El producto de dos arrays se realiza utilizando el operador @ (a partir de Python 3.5) o con la función np.dot() de Numpy.

```python
import numpy as np
```

# Creamos la primera matriz (2x3)
```python
a = np.array([(1, 2, 3), 
```
              (4, 5, 6)])
# a =
# [[1 2 3]
#  [4 5 6]]
# Forma: (2,3) → 2 filas y 3 columnas

# Creamos la segunda matriz (3x2) llena de unos
```python
b = np.ones((3, 2))
```
# b =
# [[1. 1.]
#  [1. 1.]
#  [1. 1.]]
# Forma: (3,2) → 3 filas y 2 columnas

# Producto matricial con el operador @ (Python 3.5+)
# Equivalente a usar: np.dot(a, b)
```python
c = a @ b
```

# Imprimimos el resultado
```python
print(c)
```
# Resultado:
# [[ 6.  6.]
#  [15. 15.]]

divide()

Dividir dos arrays, elemento a elemento.

```python
import numpy as np
```

# Creamos el primer array 2x3 de enteros (int8)
```python
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos el segundo array 2x3 de enteros (int8)
```python
b = np.array([(1, 1, 1), (2, 2, 2)], dtype=np.int8)
```
# b =
# [[1 1 1]
#  [2 2 2]]

# Usamos np.divide() para dividir elemento a elemento
# Esto es equivalente a escribir: c = a / b
```python
c = np.divide(a, b)
```

# Imprimimos el resultado
```python
print(c)
```
# Resultado:
# [[1.  2.  3. ]
#  [2.  2.5 3. ]]


mod()

Dividir dos matrices y obtener el resto de la división, elemento a elemento.

```python
import numpy as np
```

# Creamos el primer array 2x3 con números enteros (int8)
```python
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos el segundo array 2x3 con enteros (int8)
```python
b = np.array([(1, 1, 1), (2, 2, 2)], dtype=np.int8)
```
# b =
# [[1 1 1]
#  [2 2 2]]

# Usamos np.mod() para calcular el resto de la división elemento a elemento
```python
c = np.mod(a, b)
```

# Imprimimos el resultado
```python
print(c)
```
# Resultado esperado:
# [[0 0 0]
#  [0 1 0]]


divmod()

Dividir dos arrays y obtener el cociente y el resto de la división, elemento a elemento.

```python
import numpy as np
```

# Creamos el primer array 2x3 con enteros de 8 bits
```python
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos el segundo array 2x3 también con enteros
```python
b = np.array([(1, 1, 1), (2, 2, 2)], dtype=np.int8)
```
# b =
# [[1 1 1]
#  [2 2 2]]

# Usamos np.divmod(a, b) → devuelve una TUPLA de arrays (cociente, resto)
```python
c = np.divmod(a, b)
```

# Imprimimos el resultado
```python
print(c)
```

# Resultado esperado:
# (
#  array([[1, 2, 3],
#         [2, 2, 3]], dtype=int8),   # cociente
#
#  array([[0, 0, 0],
#         [0, 1, 0]], dtype=int8)    # resto
# )



sqrt()

Calcular la raíz cuadrada, elemento a elemento.

```python
import numpy as np
```

# Creamos un array 2x3 con valores enteros
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Calculamos la raíz cuadrada de cada elemento con np.sqrt()
```python
b = np.sqrt(a)
```

# Imprimimos el resultado
```python
print(b)
```

# Resultado esperado:
# [[1.         1.41421356 1.73205081]
#  [2.         2.23606798 2.44948974]]


exp()

Calcular la exponencial, elemento a elemento

```python
import numpy as np
```

# Creamos un array 2x3 con valores enteros
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Calculamos la exponencial de cada elemento con np.exp()
# La función np.exp(x) = e^x , donde "e" es el número de Euler (≈ 2.71828)
```python
b = np.exp(a)
```

# Imprimimos el resultado
```python
print(b)
```

# Resultado esperado (aproximado):
# [[  2.71828183   7.3890561   20.08553692]
#  [ 54.59815003 148.4131591  403.42879349]]


power()

Elevar los elementos a la potencia de un número.

```python
import numpy as np
```

# ==============================
#  Elevar los elementos de un array a una potencia fija
# ==============================

# Creamos un array 2x3
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
```
# a =
# [[1 2 3]
#  [4 5 6]]

# Elevamos cada elemento a la potencia 5
```python
b = np.power(a, 5)
```

```python
print("Array elevado a una potencia fija (5):")
print(b)
```
# Resultado:
# [[   1   32  243]
#  [1024 3125 7776]]

# ==============================
# Elevar los elementos de un array a las potencias de otro array
# ==============================

# Creamos dos arrays con la misma forma (2x3)
```python
a = np.array([(1, 2, 3), (4, 5, 6)])
b = np.array([(2, 2, 2), (3, 3, 3)])
```

# Elevamos elemento a elemento: c[i][j] = a[i][j] ** b[i][j]
```python
c = np.power(a, b)
```

```python
print("\nArray elevado a los valores de otro array:")
print(c)
```
# Resultado:
# [[  1   4   9]
#  [ 64 125 216]]


Cibergrafia

https://numpy.org/devdocs/user/whatisnumpy.html

https://www.datacamp.com/es/tutorial/python-arrays

https://flexiple.com/python/numpy-reshape

https://www.geeksforgeeks.org/machine-learning/numpy-concatenate-function-python/

https://python-para-impacientes.blogspot.com/2019/12/calculo-con-arrays-numpy.html

# Operaciones estadísticas y funciones avanzadas
     Rama:B-numpy-estadisticas

# Funciones estadísticas 
Estadística es una rama de las matemáticas que permite recoger, organizar, analizar e interpretar datos, sacar conclusiones y tomar decisiones a partir de la información. En Numpy podemos encontrar funciones para calcular métricas como la media, la mediana, la varianza, la desviación estándar, el mínimo, el máximo y más. Funciones estadísticas proporcionadas por NumPy  se encuentran: 
•	median() : La mediana representa el valor que se encuentra justo en el centro de un conjunto de datos ordenados.
•	mean(): La media es una medida de tendencia central que representa el valor promedio de un conjunto de datos. El promedio.
•	std(): La desviación estándar mide cuánto se dispersan los datos respecto a la media. Es decir, indica si los valores están muy alejados o cercanos al promedio.
•	percentile(): Es una medida que indica el valor por debajo del cual cae un porcentaje determinado de datos en un grupo de datos.
•	min(): Valor mínimo de una matriz
•	max():  Elemento máximo de una matriz
Funciones:
1. mean () – Promedio
2. std () – Desviación Estándar
3. sum() – Suma (Suma los datos dentro del arreglo)
Ejemplo de Aplicación:

# =================================
import numpy as np
a = np.array([25, 28, 28, 30, 32, 35, 37, 39, 40])
b = np.array([3, 4, 5, 10, 12, 25])

print("Entregas:", a)
print("Devoluciones:", b)

print("\n *** Datos Entregas *** ")
print("Promedio: ", np.mean(a))
print("Desviación Estándar:", np.std(a))
print("Total entregas:", np.sum(a))

print("\n*** Datos Devoluciones *** ")
print("Promedio:", np.mean(b))
print("Desviación Estándar:", np.std(b))
print("Total Devoluciones:", np.sum(b))

print("\n ** Entregas vs Devoluciones **")
print("Diferencia de Promedios:", np.mean(a) - np.mean(b))
print("Diferencia de Desviaciones:", np.std(a) - np.std(b))
print("Diferencia de Sumas:", np.sum(a) - np.sum(b))
# Resultado:
Entregas: [25 28 28 30 32 35 37 39 40]
Devoluciones: [ 3  4  5 10 12 25]

 *** Datos Entregas *** 
Promedio:  32.666666666666664
Desviación Estándar: 5.033222956847166
Total entregas: 294

*** Datos Devoluciones *** 
Promedio: 9.833333333333334
Desviación Estándar: 7.51480021173033
Total Devoluciones: 59

*** Entregas vs Devoluciones ***
Diferencia de Promedios: 22.83333333333333
Diferencia de Desviaciones: -2.481577254883164
Diferencia de Sumas: 235
# ================================

# Funciones de creación de arreglos:
Un arreglo (o array en inglés) es una estructura de datos que permite almacenar múltiples valores en una sola variable, organizados en una secuencia. Los arreglos son fundamentales para realizar operaciones matemáticas de forma eficiente y vectorizada en los campos de programación científica y análisis de datos. El núcleo de NumPy es el arreglo o array. A diferencia de las listas en Python, los arreglos de NumPy son más eficientes en términos de almacenamiento y operaciones.
Funciones:
# 1.	arange():
Crea un arreglo con valores espaciados uniformemente dentro de un intervalo.
•	arange(stop): Valores creados dentro del intervalo semiabierto, incluye el inicio del arreglo pero no el final.  [0, stop)

•	arange(start, stop): Los valores se generan dentro del intervalo semiabierto, incluye el valor inicial y el valor final. [start, stop)
•	arange(start, stop, step): Los valores se generan dentro del intervalo semiabierto, con un espaciamiento entre valores dado por .[start, stop)step. Incluye el valor inicial, excluye el valor final y incrementa los valores.
Ejemplo: 
# ===============================
import numpy as np
a = np.arange(8)  # arreglo arange(stop)
print("a:",a)

b = np.arange(3, 12)  # arreglo arange(start, stop) 
print("b:",b)

c = np.arange(3,20,3) #arange(start, stop, step) intervalo de 3  
print("c:", c)

 # Resultado:

 a: [0 1 2 3 4 5 6 7]
b: [ 3  4  5  6  7  8  9 10 11]
c: [ 3  6  9 12 15 18]

# ==============================

# 2.	linspace(): 
Genera un arreglo con un número específico de puntos espaciados uniformemente en un intervalo. Es útil cuando se necesita una cantidad precisa de puntos calculados sobre el intervalo [ inicio , fin ].
•	np.linspace(start, stop, num).genera num valores equiespaciados entre start y stop (por defecto incluye stop).

# ================================

import numpy as np
#Devolver 5 numeros en un intervalo de 2 a 4
print("Intervalo:2 a 4, num Puntos =5,  puntos:", np.linspace(2, 4, 5))

# Resultado:

Intervalo:2 a 4, num Puntos =5,  puntos: [2.  2.5 3.  3.5 4. ]

# =================================

# Funciones Aleatorias con NumPy

Utiliza el módulo random para crear arreglos con valores aleatorios. En el trabajo con datos simulados, es común utilizar números aleatorios para imitar comportamientos reales, especialmente en modelos de Machine Learning, experimentos estadísticos y simulaciones complejas. Sin embargo, generar aleatoriedad de forma eficiente, reproducible y con control sobre la distribución de los datos es un desafío clave, ya que influye directamente en la validez y precisión de los resultados simulados.

# 1.	random()
•	Enteros aleatorios (randint): Genera enteros dentro de un intervalo definido [low, high).
•	Aleatorios uniformes: Crea un array con las dimensiones especificadas y lo llena con valores aleatorios de una distribución uniforme en el intervalo [0, 1).
•	Distribución Normal (Gaussiana): Generar datos con media y desviación estándar personalizables.
•	Aleatorios a partir de una semilla: Genera siempre los mismos resultados.
•	Selección aleatoria con muestreo: Permite extraer elementos de un array, con o sin reemplazo.

# ================================

import numpy as np

a = np.random.rand(4) # Crea un arreglo de 5 numeros aleatorios entre 0 y 1.
print("Arreglo A: ", a)

b= np.random.randint(3, 15, size=8) # arrgelo de 8 numero aleatorios entre 3 y 15
print("Arreglo B:", b)

c = np.random.uniform(10, 30, 3) # 5 valores uniformes entre 10 y 30
print("Uniforme [10,30]:", c)

# Normal con media 50 y desviación 5
d = np.random.normal(20, 5, 5)
print("Normal (media=20, Desvacion=5):", d)

np.random.seed(42) # Aleatorio con semilla
e = np.random.randint(0, 100, 5)
print("Semilla:", e)

# Resultado:
Arreglo A:  [0.38246199 0.98323089 0.46676289 0.85994041]
Arreglo B: [ 9  7 11  9  4  6 11 14]
Uniforme [10,30]: [21.26576436 17.70833005 10.31932504]
Normal (media=20, Desvacion=5): [16.16011749 16.25461738 16.10808996 24.74421429 27.90425293]
Con semilla: [51 92 14 71 60]

# ====================================

# Álgebra lineal:
Es el conjunto de herramientas que esta biblioteca de Python ofrece para trabajar con vectores, matrices y transformaciones lineales, de forma eficiente y estructurada. Es especialmente útil en ciencia de datos, ingeniería, estadística y machine learning, donde los cálculos matriciales son fundamentales.
# 1.	Vectores y matrices: 
Un vector se implementa como un array unidimensional, mientras que una matriz es un array bidimensional. Esto permite una sintaxis clara y consistente para todas las operaciones de álgebra lineal.
Producto punto (dot() o @): Multiplicar matrices es una operación fundamental
# ===================================
import numpy as np
# crear las matrices
A = np.array([[1, 2],
              [3, 4]])

B = np.array([[5, 6],
              [7, 8]])

print("Matriz A:",A)
print("Matriz B:",B )

# Resultado
Matriz A: [[1 2]
 [3 4]]
Matriz B: [[5 6]
 [7 8]]

# ===================================

# 2.	Operaciones básicas:
suma, resta, multiplicación, transposición

import numpy as np
# crear las matrices
A = np.array([[1, 2],
              [3, 4]])
C = A + B #suma
print("\nSuma A + B:",C)

D = A - B #resta
print("\nResta A - B:", D)

E = A * B #multiplicación
print("\nMultiplicación elemento a elemento A * B:", E)

F = np.dot(A, B) # producto matricial
print("\nProducto matricial A x B:", F)

print("\nTranspuesta de A:")# Transpuesta
print(A.T)
A_inv = np.linalg.inv(A)#inversa
print("\nInversa de A:")
print(A_inv)

# Resultado
Suma A + B: [[ 6  8]
 [10 12]]

Resta A - B: [[-4 -4]
 [-4 -4]]

Multiplicación elemento a elemento A * B: [[ 5 12]
 [21 32]]

Producto matricial A x B: [[19 22]
 [43 50]]

Transpuesta de A:
[[1 3]
 [2 4]]

Inversa de A:
[[-2.   1. ]
 [ 1.5 -0.5]]

 # =============================

# 3.	Determinante y matrices inversas.

El determinante indica si una matriz cuadrada es invertible (≠ 0) y tiene aplicaciones en sistemas lineales, transformaciones y geometría.
# =============================
Matriz = np.array([[6, 1, 1], [4, -2, 5], [2, 8, 7]])

# Calculamos la determinante
determinante_3x3 = np.linalg.det(Matriz)

print("\nMatriz 3x3:")
print(Matriz)
print(f"Determinante: {determinante_3x3}")

# Resultado:
Matriz 3x3:
[[ 6  1  1]
 [ 4 -2  5]
 [ 2  8  7]]
Determinante: -306.0
        *** ============== ***
M_original = np.array([[4, 7], [2, 6]])

# Calculamos la matriz inversa
M_inversa = np.linalg.inv(M_original)

print("Matriz original:", M_original)
print("\nMatriz inversa:", M_inversa)

# Resultado
Matriz original: [[4 7]
 [2 6]]

Matriz inversa: [[ 0.6 -0.7]
 [-0.2  0.4]]
# ==============================

# 4.	Autovalores y autovectores

Los autovalores (eigenvalues) y autovectores (eigenvectors) son conceptos que describen propiedades especiales de las transformaciones lineales representadas por matrices. Para una matriz cuadrada A, un vector no nulo v es un vector propio con valor propio λ si Av = λv.
# ============================
M_A = np.array([[4, 2],
              [1, 3]])
print("Matriz A:",M_A)

valores, vectores = np.linalg.eig(M_A)
print("\nAutovalores:", valores)
print("\nAutovectores (columnas):", vectores)

for i in range(len(valores)):
    v = vectores[:, i]  # i-ésimo autovector
    λ = valores[i]      # i-ésimo autovalor
    print(f"\nVerificación para autovalor λ = {λ:.2f}:")
    print("A·v =", M_A.dot(v))
    print("λ·v =", λ * v)
    *** Resultado ***
Matriz A: [[4 2]
 [1 3]]

Autovalores: [5. 2.]

Autovectores (columnas): [[ 0.89442719 -0.70710678]
 [ 0.4472136   0.70710678]]

Verificación para autovalor λ = 5.00:
A·v = [4.47213595 2.23606798]
λ·v = [4.47213595 2.23606798]

Verificación para autovalor λ = 2.00:
A·v = [-1.41421356  1.41421356]
λ·v = [-1.41421356  1.41421356]
# ================================
# 5.	Sistemas de ecuaciones lineales:
Un sistema de ecuaciones lineales se puede expresar en forma matricial como Ax = b, donde A es la matriz de coeficientes, x es el vector de incógnitas y b es el vector de términos independientes.
Numpy proporciona la función solve(), para resolver ecuaciones lineales.

# =================================
A = np.array([[2, 1],
              [1, -1]])

B = np.array([8, 1])#vector de resultado

print("Matriz A (coeficientes):")
print(A)
print("\nVector B (resultados):")
print(B)

X = np.linalg.solve(A, B)
print("\nSolución del sistema (x, y):")
print(X)
    *** Resultado ***
Matriz A (coeficientes):
[[ 2  1]
 [ 1 -1]]

Vector B (resultados):
[8 1]

Solución del sistema (x, y):
[3. 2.]     
# =================================
















