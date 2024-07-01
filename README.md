# Scikitlearn_Solar_Prediction

Este repositorio contiene un trabajo realizado en la asignatura de **Aprendizaje Automático** de mi grado en Estadística y Empresa. El trabajo ha sido realizado en un archivo `.ipynb` (notebook de Jupyter), mientras que los datos se encuentran en formato .feather


## Descripción de los datos

**Nota**: Los datos utilizados en la práctica no son los originales y tienen ligeras modificaciones realizados por el tutor de la asignatura. La última columna de los datos, denominada "salida", representa la radiación solar acumulada durante todo el día.
- **Atributos de entrada**: Predicciones del día siguiente de 15 variables meteorológicas. Los datos han sido generados por una simulación de ecuaciones de la atmósfera denominada NWP (Numerical Weather Prediction).
- **Frecuencia**: Predicciones generadas para cinco momentos del día siguiente: 12h, 15h, 18h, 21h, 24h UTC.
- **Dimensiones**: 15 variables generadas para 5 momentos del día siguiente, totalizando 75 atributos de entrada.

### Ejemplos de variables:
- `apcp_sf1_1`: "3-Hour accumulated precipitation at the surface" para el primer momento del día siguiente.
- `dswrf_s2_1`: "Downward short-wave radiative flux average at the surface".

## Objetivo del Análisis

Calcular el RAE (Relative Absolute Error) entrenando con `train` (6 años) y evaluando con `validation` (3 años) usando árboles de decisión y KNN.

### Metodología

1. **EDA (Exploratory Data Analysis)**:
   - Comprobación de variables categóricas.
   - Conversión de variables categóricas a dummies usando `ColumnTransformer`.

2. **Preparación de datos**:
   - Creación de la matriz de predictores (`X`) y el vector de respuesta (`y`).

3. **Entrenamiento y Evaluación**:
   - Modelos de regresión: `DecisionTreeRegressor` y `KNeighborsRegressor`.
   - Métrica: `Mean Absolute Error (MAE)`.
   - Cálculo del RAE comparando con un modelo trivial.

### Importante

No usamos `train_test_split` para generar los conjuntos de `train` y `validation`, ya que `train_test_split` hace particiones aleatorias. Utilizamos directamente los conjuntos predefinidos:
- `X_train = X[0:(6*365),:]`

Este es un problema de regresión, por lo que usamos `DecisionTreeRegressor` y `metrics.mean_absolute_error`.

## Contenido del Repositorio

- **Datos**: Archivo en formato feather con las variables meteorológicas y la radiación solar acumulada.
- **Notebook**: Archivo `.ipynb` con el análisis completo, incluyendo el EDA, la preparación de datos y el entrenamiento y evaluación de los modelos de aprendizaje automático.

## Librerías Python utilizadas

Para ejecutar el análisis, se necesita tener instalado Python con las librerías `pandas`, `numpy`, `scikit-learn` y `matplotlib`. Se recomienda usar un entorno virtual.


