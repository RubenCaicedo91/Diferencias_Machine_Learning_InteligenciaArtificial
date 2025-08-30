D)  Pandas – Operaciones avanzadas en DataFrames
(filtros, groupby, merge/join, manejo de valores nulos, exportación/importación).

En el mundo del análisis de datos, Pandas se ha consolidado como la biblioteca fundamental de Python para la manipulación y transformación de datos. Mientras que las operaciones básicas permiten familiarizarse con la estructura de DataFrames, son las operaciones avanzadas las que realmente liberan el potencial completo de esta poderosa herramienta.
Las técnicas de filtrado sofisticado, agrupamiento inteligente, combinación de datasets y manejo de valores missing representan el conjunto de habilidades que separan a los principiantes de los analistas expertos. Estas operaciones permiten transformar datos crudos en información significativa, responder preguntas complejas y preparar datasets para modelado predictivo.
En esta guía comprehensive, exploraremos las cinco piedras angulares del manejo avanzado de DataFrames:
•	Filtros avanzados para segmentación precisa de datos
•	Operaciones GroupBy para análisis agregado
•	Merge y Join para combinar múltiples fuentes de datos
•	Manejo de valores nulos para mantener la integridad de los datos
•	Exportación/Importación para flujos de trabajo eficientes
Cada una de estas operaciones, cuando se domina, se convierte en una herramienta indispensable en el arsenal de cualquier profesional de datos, permitiendo manipular grandes volúmenes de información con elegancia y eficiencia.

1. Filtros Avanzados
# Importa las librerías pandas (para DataFrames) y numpy (para operaciones numéricas)
import pandas as pd
import numpy as np


# Crear DataFrame de ejemplo
# Crea un DataFrame con 5 filas y 5 columnas de datos de empleados
df = pd.DataFrame({
    'nombre': ['Ana', 'Juan', 'María', 'Pedro', 'Laura'],
    'edad': [25, 30, 35, 40, 28],
    'ciudad': ['Bogota', 'Cali', 'Neiva', 'Cartagena', 'Bucaramanga'],
    'salario': [30000, 45000, 50000, 35000, 42000],
    'departamento': ['Ventas', 'IT', 'Ventas', 'RH', 'IT']
})


# Filtro básico
# Filtra las filas donde la edad sea mayor a 30 años
filtro_edad = df[df['edad'] > 30]


# Múltiples condiciones (usar &, |, ~)
# Filtra filas donde edad > 25 Y ciudad sea 'Bogota'
# & = AND, | = OR, ~ = NOT
filtro_complejo = df[(df['edad'] > 25) & (df['ciudad'] == 'Bogota')]


# Filtro con isin()
# Filtra filas donde la ciudad esté en la lista ['Bogota', 'Cali']
filtro_ciudades = df[df['ciudad'].isin(['Bogota', 'Cali'])]


# Filtro con query()
# Usa una cadena de texto con condiciones SQL-like para filtrar
filtro_query = df.query('edad > 30 and salario > 40000')

2. Filtros con texto
# Filtrar nombres que contengan "a"
# Filtra nombres que contengan la letra 'a' (case=False ignora mayúsculas/minúsculas)
filtro_nombre = df[df['nombre'].str.contains('a', case=False)]


# Filtrar con expresiones regulares
# Filtra ciudades que empiecen con 'M' usando expresiones regulares
# '^M' significa "que empiece con la letra M"
filtro_regex = df[df['ciudad'].str.contains('^M', regex=True)]

3. GroupBy Avanzado
# Agrupamiento básico
# Agrupa el DataFrame por la columna 'ciudad', creando grupos para cada ciudad única
grupo_ciudad = df.groupby('ciudad')


# Múltiples agregaciones
# Para cada departamento, calcula:
# - Del salario: promedio, mínimo, máximo y desviación estándar
# - De la edad: promedio
stats = df.groupby('departamento').agg({
    'salario': ['mean', 'min', 'max', 'std'],
    'edad': 'mean'
})


# Agrupamiento por múltiples columnas
# Agrupa por departamento Y ciudad, calcula:
# - Salario promedio
# - Conteo de empleados (y renombra esta columna)
grupo_multiple = df.groupby(['departamento', 'ciudad']).agg({
    'salario': 'mean',
    'edad': 'count'
}).rename(columns={'edad': 'cantidad_empleados'})

# Transformaciones
# Para cada fila, calcula el salario promedio de su departamento
# y lo asigna a una nueva columna
df['salario_promedio_depto'] = df.groupby('departamento')['salario'].transform('mean')

4. Merge/Join
# Crear DataFrames adicionales
# Crea DataFrame con información adicional de empleados
df_info = pd.DataFrame({
    'nombre': ['Ana', 'Juan', 'María', 'Pedro', 'Laura', 'Carlos'],
    'email': ['ana@email.com', 'juan@email.com', 'maria@email.com',
              'pedro@email.com', 'laura@email.com', 'carlos@email.com']
})

# Crea DataFrame con información de departamentos
df_departamentos = pd.DataFrame({
    'departamento': ['Ventas', 'IT', 'RH', 'Marketing'],
    'gerente': ['García', 'López', 'Martínez', 'Rodríguez']
})


# Inner join (default)
# Combina los DataFrames, manteniendo solo las filas donde el nombre existe en AMBOS
merged_inner = pd.merge(df, df_info, on='nombre', how='inner')


# Left join
# Mantiene TODAS las filas del DataFrame izquierdo (df) y añade información del derecho
merged_left = pd.merge(df, df_info, on='nombre', how='left')


# Right join
# Mantiene TODAS las filas del DataFrame derecho (df_info) y añade información del izquierdo
merged_right = pd.merge(df, df_info, on='nombre', how='right')


# Outer join
# Mantiene TODAS las filas de AMBOS DataFrames
merged_outer = pd.merge(df, df_info, on='nombre', how='outer')

5. Manejo de valores nulos
# Crear DataFrame con valores nulos
# Crea una copia del DataFrame para no modificar el original
df_nulos = df_completo.copy()

# Asigna valores NaN (Not a Number) a los salarios de las filas 2 a 4
df_nulos.loc[2:4, 'salario'] = np.nan

# Asigna NaN a la edad de la fila 1
df_nulos.loc[1, 'edad'] = np.nan

# Asigna None a la ciudad de la fila 5 (None también se trata como valor nulo)
df_nulos.loc[5, 'ciudad'] = None


# Detectar valores nulos
# Cuenta cuántos valores nulos hay en cada columna
print("Valores nulos por columna:")
print(df_nulos.isnull().sum())

# Calcula el porcentaje de valores nulos en cada columna
print("\nPorcentaje de valores nulos:")
print(df_nulos.isnull().mean() * 100)


# Eliminar filas con valores nulos
# Elimina TODAS las filas que tengan AL MENOS un valor nulo
df_sin_nulos = df_nulos.dropna()

# Eliminar columnas con muchos nulos
# Elimina columnas que tengan menos del 70% de valores no nulos
# thresh = número mínimo de valores no nulos requeridos
df_limpio = df_nulos.dropna(thresh=len(df_nulos)*0.7, axis=1)



# Rellenar valores nulos
# Crea una copia para trabajar
df_rellenado = df_nulos.copy()

# Rellena los valores nulos en 'salario' con el promedio de salarios
df_rellenado['salario'] = df_rellenado['salario'].fillna(df_rellenado['salario'].mean())

# Rellena valores nulos en 'edad' con la mediana de edades
df_rellenado['edad'] = df_rellenado['edad'].fillna(df_rellenado['edad'].median())

# Rellena valores nulos en 'ciudad' con el texto 'Desconocida'
df_rellenado['ciudad'] = df_rellenado['ciudad'].fillna('Desconocida')

6. Exportacion/Importacion
# Exportar a diferentes formatos
# Guarda como CSV sin incluir el índice y usando codificación UTF-8
df.to_csv('empleados.csv', index=False, encoding='utf-8')

# Guarda como Excel, sin índice, en la hoja llamada 'Empleados'
df.to_excel('empleados.xlsx', index=False, sheet_name='Empleados')

# Guarda como JSON en formato de registros
df.to_json('empleados.json', orient='records')

# Guarda como Parquet (formato binario eficiente para grandes datos)
df.to_parquet('empleados.parquet')


# Importar desde diferentes formatos
# Lee archivo CSV con codificación UTF-8
df_csv = pd.read_csv('empleados.csv', encoding='utf-8')

# Lee la hoja 'Empleados' del archivo Excel
df_excel = pd.read_excel('empleados.xlsx', sheet_name='Empleados')

# Lee archivo JSON
df_json = pd.read_json('empleados.json')

# Lee archivo Parquet
df_parquet = pd.read_parquet('empleados.parquet')
