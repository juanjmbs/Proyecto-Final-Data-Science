# Análisis de Indicadores Socioeconómicos por Países
 
- Bravo, Juan  


## Tabla de Contenidos

1. Presentación del Problema
2. Preguntas y Objetivos de la Investigación
3. Indicación de la Fuente del Dataset y los Criterios de Selección
4. Data Wrangling y EDA
5. Visualización de Variables
6. Análisis Descriptivo del Dataset
7. Feature Engineering
8. Pairplot - Análisis Bivariado
9. K-means
10. Heatmap
11. Regresión Lineal
12. Método LOOCV
13. LightGBM
14. Conclusiones

## Presentación del Problema

La multinacional Mask-Bezos pretende ayudar con U$D 200 millones a los países del mundo que necesiten ayuda económica. Se solicita observar cuáles son los países que necesitan ayuda y en base a qué variables se determinaría tal decisión. Los países deben ser clasificados según su nivel de desarrollo.

## Preguntas y Objetivos de la Investigación

**Objetivo:** Determinar cuáles son los países que necesitan ayuda económica basándose en variables de medición de la pobreza.

## Indicación de la Fuente del Dataset y los Criterios de Selección

El dataset se obtuvo de la página web Kaggle y contiene indicadores como pobreza, inflación, PBI per cápita, entre otros. Estos indicadores ayudan a categorizar los países según factores socioeconómicos y de salud.

## Data Wrangling y EDA

Se realizó un análisis exploratorio de datos (EDA) para identificar patrones estadísticos y distribuciones. El dataset contiene 167 registros y 10 columnas, sin datos nulos.

## Visualización de Variables

Se utilizó un mapamundi interactivo y un Boxplot para visualizar las variables y sus valores extremos.

## Análisis Descriptivo del Dataset

Se analizaron las principales características de cada columna utilizando métodos como `dtypes`, `info` y `shape`.

## Feature Engineering

Se crearon dos nuevas variables: `Need Help` y `k_labels`, para establecer la necesidad de ayuda y el rango de prioridad de los países.

## Pairplot - Análisis Bivariado

Se utilizó `pairplot` de seaborn para obtener gráficos con múltiples distribuciones bivariadas de a pares.

## K-means

Se utilizó el algoritmo K-means para clasificar los países en sub-desarrollados, en vías de desarrollo y desarrollados.

## Heatmap

Se utilizó un heatmap para observar la correlación entre las variables. Las variables `income` y `gdpp` mostraron una fuerte correlación.

## Regresión Lineal

Se implementó un modelo de regresión lineal para modelar la relación entre `income` y `gdpp`.

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score

X = countriessocioeconomic[['income']]
Y = countriessocioeconomic['gdpp']

x_train, x_test, y_train, y_test = train_test_split(X, Y, test_size=0.2)

linear_model = LinearRegression(normalize=True).fit(x_train, y_train)

print('Puntaje Entrenamiento: ', linear_model.score(x_train, y_train))

y_pred = linear_model.predict(x_test)
print('Puntaje Testing: ', r2_score(y_test, y_pred))

