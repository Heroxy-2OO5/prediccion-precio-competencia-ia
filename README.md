# Predicción del precio de la competencia con Machine Learning

[![Abrir en Google Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Heroxy-2005/prediccion-precio-competencia-ia/blob/main/Prediccion_Precio_Competencia.ipynb)

Proyecto de Machine Learning desarrollado en Python para predecir el precio de un producto de la competencia a partir del precio del producto analizado.

En el proyecto se entrenan y comparan dos modelos de regresión: **Regresión Lineal** y **Random Forest Regressor**. Además, se incorpora una pequeña interfaz interactiva que permite ingresar un precio y obtener automáticamente la predicción correspondiente.

---

## Objetivo del proyecto

Desarrollar un modelo de Machine Learning capaz de estimar el precio de la competencia mediante el análisis de datos comerciales, comparando diferentes algoritmos de regresión y seleccionando el modelo con mejor rendimiento.

---

## Descripción

El sistema utiliza un conjunto de datos comerciales almacenado en un archivo de Excel. El dataset contiene información relacionada con precios, descuentos, promociones, publicidad, inventario, comportamiento de los clientes y otras variables del entorno comercial.

Para esta primera versión del proyecto se utiliza:

- **Variable de entrada:** `price`
- **Variable objetivo:** `competitor_price`

El conjunto de datos se divide en:

- 80 % para entrenamiento.
- 20 % para pruebas.
- Semilla aleatoria: `random_state=42`.

---

## Modelos utilizados

### Regresión Lineal

La Regresión Lineal busca establecer una relación matemática entre el precio del producto y el precio de la competencia.

```python
from sklearn.linear_model import LinearRegression

model = LinearRegression()
model.fit(x_train, y_train)
```

### Random Forest Regressor

Random Forest combina múltiples árboles de decisión para producir una predicción final.

```python
from sklearn.ensemble import RandomForestRegressor

rf_model = RandomForestRegressor(
    n_estimators=1000,
    random_state=42
)

rf_model.fit(x_train, y_train)
```

---

## Resultados obtenidos

El rendimiento de los modelos se evaluó mediante el coeficiente de determinación **R²**.

| Modelo | R² en el conjunto de prueba |
|---|---:|
| Regresión Lineal | 0.9372 |
| Random Forest Regressor | 0.9132 |

La **Regresión Lineal** obtuvo el mejor resultado, con un R² aproximado de **0.94**.

Esto significa que el modelo explica aproximadamente el 93.72 % de la variación observada en el precio de la competencia dentro del conjunto de prueba.

> El valor R² no representa exactamente un porcentaje de exactitud, sino la proporción de variabilidad explicada por el modelo.

---

## Interfaz interactiva

El notebook incluye una interfaz sencilla creada con `ipywidgets`.

La interfaz permite:

1. Ingresar el precio de un producto.
2. Presionar el botón **Predecir**.
3. Obtener la estimación del precio de la competencia.

Ejemplo:

```text
Precio del producto: 10

La predicción para el precio del competidor es 9.15
```

Los widgets no funcionan directamente desde la vista previa de GitHub. Para utilizar la interfaz es necesario abrir el notebook en Google Colab y ejecutar todas las celdas.

---

## Tecnologías utilizadas

- Python
- Google Colab
- Pandas
- Scikit-learn
- OpenPyXL
- ipywidgets
- GitHub

---

## Estructura del repositorio

```text
prediccion-precio-competencia-ia/
│
├── Prediccion_Precio_Competencia.ipynb
├── data_train_clean_ordenado (1).xlsx
└── README.md
```

### Archivos principales

- `Prediccion_Precio_Competencia.ipynb`: contiene la carga de datos, entrenamiento, evaluación y formulario de predicción.
- `data_train_clean_ordenado (1).xlsx`: conjunto de datos utilizado por el proyecto.
- `README.md`: documentación general del repositorio.

---

## Variables del dataset

El conjunto de datos contiene las siguientes columnas:

| Variable | Descripción |
|---|---|
| `id` | Identificador del registro |
| `price` | Precio del producto |
| `discount` | Descuento aplicado |
| `promotion_intensity` | Intensidad de la promoción |
| `footfall` | Flujo o cantidad estimada de clientes |
| `ad_spend` | Inversión en publicidad |
| `competitor_price` | Precio del producto de la competencia |
| `stock_level` | Nivel de inventario |
| `weather_index` | Índice relacionado con las condiciones climáticas |
| `customer_sentiment` | Nivel de percepción o sentimiento del cliente |
| `return_rate` | Tasa de devolución del producto |

---

## Cómo ejecutar el proyecto

### Opción 1: Google Colab

Presiona el botón ubicado al inicio del README:

**Abrir en Google Colab**

Después:

1. Ejecuta la primera celda para cargar las librerías y el dataset.
2. Ejecuta la celda de entrenamiento.
3. Revisa los resultados de los modelos.
4. Ejecuta la celda del formulario interactivo.
5. Ingresa un precio y presiona **Predecir**.

También puedes abrir el notebook desde este enlace:

```text
https://colab.research.google.com/github/Heroxy-2005/prediccion-precio-competencia-ia/blob/main/Prediccion_Precio_Competencia.ipynb
```

### Opción 2: Ejecución local

Primero clona el repositorio:

```bash
git clone https://github.com/Heroxy-2005/prediccion-precio-competencia-ia.git
```

Ingresa a la carpeta:

```bash
cd prediccion-precio-competencia-ia
```

Instala las dependencias:

```bash
pip install pandas scikit-learn openpyxl ipywidgets notebook
```

Después inicia Jupyter Notebook:

```bash
jupyter notebook
```

Finalmente, abre:

```text
Prediccion_Precio_Competencia.ipynb
```

---

## Carga del dataset desde GitHub

El notebook utiliza una dirección Raw de GitHub para leer el archivo Excel.

```python
import pandas as pd

url = (
    "https://raw.githubusercontent.com/"
    "Heroxy-2005/prediccion-precio-competencia-ia/"
    "main/data_train_clean_ordenado%20(1).xlsx"
)

dataframe = pd.read_excel(url, engine="openpyxl")
dataframe.head()
```

El código `%20` representa el espacio presente en el nombre del archivo.

Para evitar problemas con las direcciones URL, se recomienda posteriormente cambiar el nombre del archivo a:

```text
data_train_clean_ordenado.xlsx
```

---

## Proceso realizado

El desarrollo del proyecto sigue las siguientes etapas:

1. Importación de las librerías.
2. Lectura del archivo de Excel.
3. Exploración inicial del dataset.
4. Selección de la variable de entrada.
5. Selección de la variable objetivo.
6. División de los datos en entrenamiento y prueba.
7. Entrenamiento de la Regresión Lineal.
8. Entrenamiento de Random Forest Regressor.
9. Comparación del coeficiente R².
10. Creación del formulario interactivo.
11. Generación de nuevas predicciones.

---

## Ejemplo del código de entrenamiento

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.ensemble import RandomForestRegressor

x = dataframe[["price"]]
y = dataframe["competitor_price"]

x_train, x_test, y_train, y_test = train_test_split(
    x,
    y,
    test_size=0.2,
    random_state=42
)

model = LinearRegression()
model.fit(x_train, y_train)

rf_model = RandomForestRegressor(
    n_estimators=1000,
    random_state=42
)

rf_model.fit(x_train, y_train)

print("R² Regresión Lineal:", model.score(x_test, y_test))
print("R² Random Forest:", rf_model.score(x_test, y_test))
```

---

## Limitaciones actuales

- El modelo utiliza únicamente el precio del producto como variable de entrada.
- No se han realizado pruebas con todas las variables disponibles.
- El resultado depende de la calidad y cantidad de los datos.
- La interfaz funciona principalmente en Google Colab o Jupyter Notebook.
- Los widgets interactivos no se ejecutan desde la vista previa de GitHub.
- El proyecto todavía no cuenta con una aplicación web independiente.

---

## Mejoras futuras

Entre las posibles mejoras del proyecto se encuentran:

- Utilizar más variables del dataset.
- Aplicar selección de características.
- Evaluar métricas como MAE, MSE y RMSE.
- Incorporar validación cruzada.
- Optimizar los hiperparámetros de Random Forest.
- Comparar nuevos modelos de regresión.
- Crear gráficos de valores reales y predichos.
- Analizar la importancia de las variables.
- Guardar el modelo entrenado.
- Desarrollar una aplicación con Streamlit o Flask.
- Publicar una versión web del sistema.

---

## Conclusión

La Regresión Lineal presentó el mejor rendimiento en la predicción del precio de la competencia, superando al modelo Random Forest en el conjunto de prueba.

Los resultados demuestran que existe una relación importante entre el precio del producto y el precio de la competencia. Sin embargo, para obtener un sistema más completo, será necesario incorporar otras variables comerciales y evaluar el modelo con métricas adicionales.

Este proyecto representa una aplicación introductoria de Machine Learning orientada al análisis de precios y a la toma de decisiones comerciales.

---

## Autor

Desarrollado por **Heroxy-2005**.

GitHub: [Heroxy-2005](https://github.com/Heroxy-2005)

---

## Uso académico

Este proyecto fue desarrollado con fines educativos y académicos para demostrar la aplicación de modelos de regresión en un problema de predicción de precios.

Actualmente, el repositorio no tiene una licencia de uso definida.
