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
import numpy as np

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
print(prices_array)

# Imprimimos el arreglo de ganancias.
print(earnings_array)


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
import numpy as np

# Creamos un arreglo con valores desde 0 hasta 19 (20 elementos en total)
# np.arange(20) genera una secuencia de enteros consecutivos desde 0 hasta 19
x = np.arange(20)
        
# Imprime el arreglo completo con sus elementos
print(x)
print()   # Salto de línea para separar la salida visualmente
        
# Imprime la forma (shape) del arreglo
# En este caso, (20,) significa que es un arreglo de UNA dimensión con 20 elementos
print(x.shape)
print()
        
# Imprime el número de dimensiones (ndim) del arreglo
# Como es un vector (arreglo unidimensional), devuelve 1
print(x.ndim)


En este caso, los números [0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19] son ​​los elementos del array x. La salida (20,) es la forma del array. Finalmente, el valor 1 impreso indica la dimensión del array.

Para probar la función de remodelación de numpy, necesitamos especificar el array original como primer argumento y la forma del segundo argumento como una lista o tupla. 

# Importamos la librería NumPy
import numpy as np   

# Creamos un array con valores enteros del 0 al 19
# np.arange(20) genera números desde 0 hasta 19 (20 elementos en total)
x = np.arange(20)   

# Imprime el array completo
print(x)

# Línea en blanco para separar visualmente
print()  

# .shape devuelve la forma (shape) del array
# Como es un vector de 20 elementos en una sola dimensión → (20,)
print(x.shape)

# Línea en blanco
print()  

# .ndim devuelve el número de dimensiones del array
# Como x es un vector (no una matriz) → tiene 1 dimensión
print(x.ndim)

# Ahora reestructuramos el array con np.reshape
# np.reshape(x, [2, 2, 5]) reorganiza los mismos 20 elementos en un arreglo 3D:
# - 2 bloques
# - cada bloque con 2 filas
# - y cada fila con 5 columnas
print(np.reshape(x, [2, 2, 5]))

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
import numpy as np

# Creamos el primer arreglo unidimensional con 3 elementos
arr1 = np.array([1, 2, 3])

# Creamos el segundo arreglo unidimensional con 3 elementos
arr2 = np.array([4, 5, 6])

# Usamos la función concatenate() de NumPy para unir ambos arreglos
# El resultado será un nuevo arreglo que contiene los elementos de arr1
# seguidos de los elementos de arr2
result = np.concatenate((arr1, arr2))

# Imprimimos el resultado de la concatenación
print("Result:", result)



Ejemplo 2: Concatenación de matrices 2D a lo largo de filas (eje=0)

Para matrices 2D, puede concatenar a lo largo de filas (comportamiento predeterminado) o columnas
# Importamos la librería NumPy con el alias "np"
import numpy as np

# Creamos el primer arreglo (matriz 2x2)
# Tiene 2 filas y 2 columnas
arr1 = np.array([[1, 2], 
                 [3, 4]])

# Creamos el segundo arreglo (matriz 1x2)
# Tiene 1 fila y 2 columnas
arr2 = np.array([[5, 6]])

# Concatenamos ambos arreglos a lo largo del eje 0 (filas)
# Esto significa que arr2 se añade como una nueva fila debajo de arr1
result = np.concatenate((arr1, arr2), axis=0)

# Imprimimos el resultado en formato de matriz
print("Result:\n", result)
4) NumPy operaciones básicas
 Numpy ofrece todo lo necesario para obtener un buen rendimiento cuando se trata de hacer cálculos con arrays. Por como está concebida la biblioteca es una de sus principales virtudes si lo comparamos con los cálculos que pueden realizarse en Python con otras estructuras de datos como listas, tuplas y diccionarios.

Numpy permite realizar la misma operación aritmética con cada elemento de un array por separado y operar con arrays de igual o distintas dimensiones.

También cuenta con funciones matemáticas que abarcan distintas necesidades para operar con todos los elementos de un array o por ejes, sin olvidar el cálculo a nivel binario, estadístico y con números reales.

Operaciones aritméticas con un mismo valor

Con Numpy se puede operar un mismo valor con todos los elementos del array, elemento a elemento, utilizando los símbolos matemáticos: + (sumar), - (restar), * (multiplicar), / (dividir), // (dividir, cociente como entero), ** (potenciación).

import numpy as np

# Creamos un arreglo 2D (matriz de 2 filas x 3 columnas)
a = np.array([(1, 2, 3), (4, 5, 6)])

# SUMA: se suma 1 a cada elemento del arreglo
a = a + 1
print(a)
# Resultado:
# [[2 3 4]
#  [5 6 7]]
# Creamos nuevamente el arreglo inicial
a = np.array([(1, 2, 3), (4, 5, 6)])
# RESTA: se resta 1 a cada elemento del arreglo
a = a - 1
print(a)
# Resultado:
# [[0 1 2]
#  [3 4 5]]
# Volvemos a crear el arreglo original
a = np.array([(1, 2, 3), (4, 5, 6)])
# MULTIPLICACIÓN: cada elemento se multiplica por 5
a = a * 5
print(a)
# Resultado:
# [[ 5 10 15]
#  [20 25 30]]
# Nuevo arreglo original
a = np.array([(1, 2, 3), (4, 5, 6)])
# DIVISIÓN REAL: cada elemento se divide entre 2
# El resultado puede ser decimal (float)
a = a / 2
print(a)
# Resultado:
# [[0.5 1.  1.5]
#  [2.  2.5 3. ]]
# Nuevo arreglo original
a = np.array([(1, 2, 3), (4, 5, 6)])
# DIVISIÓN ENTERA: cada elemento se divide entre 2
# pero solo se conserva la parte entera (sin decimales)
a = a // 2
print(a)
# Resultado:
# [[0 1 1]
#  [2 2 3]]
# Nuevo arreglo original
a = np.array([(1, 2, 3), (4, 5, 6)])
# POTENCIA: cada elemento se eleva al cuadrado (**2)
a = a ** 2
print(a)
# Resultado:
# [[ 1  4  9]
#  [16 25 36]]


Operaciones con arrays con las mismas dimensiones

Los mismos símbolos matemáticos (+, -, *, /, //, **) también se pueden utilizar para realizar operaciones aritméticas con dos arrays con las mismas dimensiones, elemento a elemento.

import numpy as np

# Creamos un array 2x3 con enteros de 8 bits (np.int8)
# int8: números enteros pequeños (-128 a 127)
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)

# Creamos un array 2x3 lleno de unos
# Por defecto np.ones() genera valores de tipo float64
b = np.ones((2, 3))

# SUMA: como a es int8 y b es float64,
# NumPy convierte automáticamente ambos al tipo más "amplio"
# → en este caso float64, para evitar pérdida de información
c = a + b

# Mostramos el array a
print(a)
# [[1 2 3]
#  [4 5 6]]
# Se mantiene como int8

# Mostramos el array b
print(b)
# [[1. 1. 1.]
#  [1. 1. 1.]]
# Es float64 (números decimales de doble precisión)

# Mostramos c (resultado de la suma)
print(c)
# [[2. 3. 4.]
#  [5. 6. 7.]]
# Es float64 porque se mezclaron int8 + float64

# RESTA: ocurre lo mismo, el resultado también será float64
c = a - b
print(c)
# [[0. 1. 2.]
#  [3. 4. 5.]]

Operaciones con arrays de diferentes dimensiones

Es una característica avanzada de Numpy para realizar operaciones aritméticas con arrays de distintas dimensiones, elemento a elemento, utilizando los símbolos matemáticos (+, -, *, /, //, **). Estas operaciones son posibles cuando el array resultante tiene la misma dimensión que al menos uno de los arrays operados.

En el ejemplo siguiente el array a tiene 3 elementos por fila que coincide con el número de elementos del array b. Numpy para realizar el cálculo suma cada fila de a con los elementos de b, elemento a elemento:


import numpy as np

# Creamos una matriz 3x3 llena de unos (dtype float64 por defecto)
a = np.ones((3, 3))
# Resultado:
# [[1. 1. 1.]
#  [1. 1. 1.]
#  [1. 1. 1.]]

# Creamos un array 1D con 3 elementos
b = np.array([1, 2, 3])
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
c = a + b

print(c)


En el ejemplo que sigue el array a tiene 3 elementos por columna que coincide con los elementos del array b. Numpy para realizar el cálculo suma cada columna de a con los elementos de b, elemento a elemento:

import numpy as np

# Creamos una matriz 3x3 llena de unos
a = np.ones((3, 3))
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

print("Resultado con vector fila:\n", c1)


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

print("\nResultado con vector columna:\n", c2)


# ===================== RESUMEN DEL BROADCASTING =====================
# - Si el array b es (3,), se expande como una fila repetida → suma por FILAS
# - Si el array b es (3,1), se expande como una columna repetida → suma por COLUMNAS



Funciones matemáticas (para operar con arrays)

add()

Sumar dos arrays, elemento a elemento.

import numpy as np

# Creamos un array 2x3 de enteros (int8 = números enteros pequeños de -128 a 127)
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos un array 2x3 lleno de unos
# Por defecto np.ones() crea valores tipo float64
b = np.ones((2, 3))
# b =
# [[1. 1. 1.]
#  [1. 1. 1.]]

# Usamos la función np.add() para sumar ambos arrays, elemento a elemento
# Esto es equivalente a escribir: c = a + b
c = np.add(a, b)

# Imprimimos el resultado
print(c)
# Resultado:
# [[2. 3. 4.]
#  [5. 6. 7.]]
# Nota:
# - Cada elemento de "a" se suma con el elemento correspondiente de "b".
# - Como a es int8 y b es float64, NumPy convierte el resultado automáticamente a float64.


subtract()

Restar dos arrays, elemento a elemento.

import numpy as np

# Creamos un array 2x3 de enteros (int8 = enteros pequeños entre -128 y 127)
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos un array 2x3 lleno de unos
# np.ones() genera valores tipo float64 por defecto
b = np.ones((2, 3))
# b =
# [[1. 1. 1.]
#  [1. 1. 1.]]

# Usamos np.subtract() para restar los arrays elemento a elemento
# Esto es equivalente a escribir: c = a - b
c = np.subtract(a, b)

# Imprimimos el resultado
print(c)
# Resultado:
# [[0. 1. 2.]
#  [3. 4. 5.]]
# Nota:
# - Cada elemento de "a" se resta con el correspondiente de "b".
# - Como "a" es int8 y "b" es float64, NumPy convierte el resultado a float64
#   para no perder información decimal (aunque aquí los resultados son enteros).


multiply()

Multiplicar dos arrays, elemento a elemento.

import numpy as np

# Creamos el primer array 2x3 de enteros (int8)
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos el segundo array 2x3 de enteros (int8)
b = np.array([(2, 2, 2), (3, 3, 3)], dtype=np.int8)
# b =
# [[2 2 2]
#  [3 3 3]]

# Usamos np.multiply() para multiplicar los arrays elemento a elemento
# Esto es equivalente a escribir: c = a * b
c = np.multiply(a, b)

# Imprimimos el resultado
print(c)
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

import numpy as np

# Creamos un array 2x3 con enteros
a = np.array([(1, 2, 3), (4, 5, 6)])
# a =
# [[1 2 3]
#  [4 5 6]]

# Multiplicamos el array por un valor escalar (4)
# Esto multiplica cada elemento de "a" por 4
b = a * 4      # equivalente a np.multiply(a, 4)

# Imprimimos el resultado
print(b)
# Resultado:
# [[ 4  8 12]
#  [16 20 24]]


Producto de dos arrays

En la teoría de matrices dos arrays se pueden multiplicar si el número de columnas de la primera coincide con el número de filas de la segunda.

El producto de dos arrays se realiza utilizando el operador @ (a partir de Python 3.5) o con la función np.dot() de Numpy.

import numpy as np

# Creamos la primera matriz (2x3)
a = np.array([(1, 2, 3), 
              (4, 5, 6)])
# a =
# [[1 2 3]
#  [4 5 6]]
# Forma: (2,3) → 2 filas y 3 columnas

# Creamos la segunda matriz (3x2) llena de unos
b = np.ones((3, 2))
# b =
# [[1. 1.]
#  [1. 1.]
#  [1. 1.]]
# Forma: (3,2) → 3 filas y 2 columnas

# Producto matricial con el operador @ (Python 3.5+)
# Equivalente a usar: np.dot(a, b)
c = a @ b

# Imprimimos el resultado
print(c)
# Resultado:
# [[ 6.  6.]
#  [15. 15.]]

divide()

Dividir dos arrays, elemento a elemento.

import numpy as np

# Creamos el primer array 2x3 de enteros (int8)
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos el segundo array 2x3 de enteros (int8)
b = np.array([(1, 1, 1), (2, 2, 2)], dtype=np.int8)
# b =
# [[1 1 1]
#  [2 2 2]]

# Usamos np.divide() para dividir elemento a elemento
# Esto es equivalente a escribir: c = a / b
c = np.divide(a, b)

# Imprimimos el resultado
print(c)
# Resultado:
# [[1.  2.  3. ]
#  [2.  2.5 3. ]]


mod()

Dividir dos matrices y obtener el resto de la división, elemento a elemento.

import numpy as np

# Creamos el primer array 2x3 con números enteros (int8)
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos el segundo array 2x3 con enteros (int8)
b = np.array([(1, 1, 1), (2, 2, 2)], dtype=np.int8)
# b =
# [[1 1 1]
#  [2 2 2]]

# Usamos np.mod() para calcular el resto de la división elemento a elemento
c = np.mod(a, b)

# Imprimimos el resultado
print(c)
# Resultado esperado:
# [[0 0 0]
#  [0 1 0]]


divmod()

Dividir dos arrays y obtener el cociente y el resto de la división, elemento a elemento.

import numpy as np

# Creamos el primer array 2x3 con enteros de 8 bits
a = np.array([(1, 2, 3), (4, 5, 6)], dtype=np.int8)
# a =
# [[1 2 3]
#  [4 5 6]]

# Creamos el segundo array 2x3 también con enteros
b = np.array([(1, 1, 1), (2, 2, 2)], dtype=np.int8)
# b =
# [[1 1 1]
#  [2 2 2]]

# Usamos np.divmod(a, b) → devuelve una TUPLA de arrays (cociente, resto)
c = np.divmod(a, b)

# Imprimimos el resultado
print(c)

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

import numpy as np

# Creamos un array 2x3 con valores enteros
a = np.array([(1, 2, 3), (4, 5, 6)])
# a =
# [[1 2 3]
#  [4 5 6]]

# Calculamos la raíz cuadrada de cada elemento con np.sqrt()
b = np.sqrt(a)

# Imprimimos el resultado
print(b)

# Resultado esperado:
# [[1.         1.41421356 1.73205081]
#  [2.         2.23606798 2.44948974]]


exp()

Calcular la exponencial, elemento a elemento

import numpy as np

# Creamos un array 2x3 con valores enteros
a = np.array([(1, 2, 3), (4, 5, 6)])
# a =
# [[1 2 3]
#  [4 5 6]]

# Calculamos la exponencial de cada elemento con np.exp()
# La función np.exp(x) = e^x , donde "e" es el número de Euler (≈ 2.71828)
b = np.exp(a)

# Imprimimos el resultado
print(b)

# Resultado esperado (aproximado):
# [[  2.71828183   7.3890561   20.08553692]
#  [ 54.59815003 148.4131591  403.42879349]]


power()

Elevar los elementos a la potencia de un número.

import numpy as np

# ==============================
#  Elevar los elementos de un array a una potencia fija
# ==============================

# Creamos un array 2x3
a = np.array([(1, 2, 3), (4, 5, 6)])
# a =
# [[1 2 3]
#  [4 5 6]]

# Elevamos cada elemento a la potencia 5
b = np.power(a, 5)

print("Array elevado a una potencia fija (5):")
print(b)
# Resultado:
# [[   1   32  243]
#  [1024 3125 7776]]

# ==============================
# Elevar los elementos de un array a las potencias de otro array
# ==============================

# Creamos dos arrays con la misma forma (2x3)
a = np.array([(1, 2, 3), (4, 5, 6)])
b = np.array([(2, 2, 2), (3, 3, 3)])

# Elevamos elemento a elemento: c[i][j] = a[i][j] ** b[i][j]
c = np.power(a, b)

print("\nArray elevado a los valores de otro array:")
print(c)
# Resultado:
# [[  1   4   9]
#  [ 64 125 216]]




