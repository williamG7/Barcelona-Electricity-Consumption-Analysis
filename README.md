# Barcelona Electricity Consumption Analysis 

## Descripción

Proyecto de análisis de datos enfocado en la **sostenibilidad energética en Barcelona**, utilizando técnicas avanzadas de **Machine Learning** y **análisis exploratorio de datos (EDA)**. Este repositorio examina patrones de consumo eléctrico a lo largo de 7 años (2019-2025) desagregados por código postal, sector económico y franja horaria.

El análisis se enmarca en los **Objetivos de Desarrollo Sostenible (ODS) 2030** de la ONU, con el objetivo de **generar propuestas de mejora** en eficiencia energética y sostenibilidad ambiental para la administración pública de Barcelona.

 **Fuente de datos:** [Open Data Barcelona - Consum d'Electricitat](https://opendata-ajuntament.barcelona.cat/data/ca/dataset/consum-electricitat-bcn)

---

##  Objetivos del Proyecto

### Objetivo Principal
Realizar un **retorno a la sociedad** mediante el análisis riguroso de datos de consumo eléctrico, identificando patrones y oportunidades de mejora en la gestión energética sostenible.

### Objetivos Secundarios

1. **Exploración exhaustiva** de datos (EDA)
2. **Predecir tendencias futuras** mediante regresión
3. **Identificar variables determinantes** con árboles de decisión
4. **Clasificar consumo energético** con algoritmos ML
5. **Visualizar patrones complejos** de forma clara
6. **Proponer medidas concretas** de eficiencia energética
7. **Documentar profesionalmente** los hallazgos

---

##  Hipótesis a Demostrar

1. ✅ El consumo eléctrico **varía significativamente según el código postal**
2. ✅ Existen **diferencias claras de consumo según el sector económico**
3. ✅ La **franja horaria influye directamente** en el consumo eléctrico
4. ✅ Se pueden construir **modelos predictivos** de consumo
5. ✅ Los patrones identificados **permiten propuestas de mejora** concretas

---

##  Tecnologías y Dependencias

### Librerías Core

```python
# Procesamiento y Análisis de Datos
import pandas as pd              # Análisis de datos
import numpy as np              # Cálculos numéricos
import io                       # Manejo de archivos en memoria

# Machine Learning
from sklearn.model_selection    # División train/test
from sklearn.preprocessing      # Escalado y transformación
from sklearn.linear_model       # Regresiones lineales
from sklearn.tree               # Árboles de decisión
from sklearn.ensemble           # Random Forest
from sklearn.neighbors          # KNN
from sklearn.cluster            # Clustering (KMeans)
from sklearn.decomposition      # PCA
from sklearn.pipeline           # Pipelines ML
from sklearn.metrics            # Métricas de evaluación

# Visualización
import matplotlib.pyplot as plt  # Gráficos básicos
import seaborn as sns           # Gráficos estadísticos

# APIs y Datos
import requests                 # Cliente HTTP
import json                     # Procesamiento JSON

# Google Colab
from google.colab import files  # Upload/download de archivos
```

**Versiones Recomendadas:**
- **Python ≥ 3.8**
- **pandas ≥ 1.3**
- **numpy ≥ 1.21**
- **scikit-learn ≥ 1.0**
- **matplotlib ≥ 3.4**
- **seaborn ≥ 0.11**
- **requests ≥ 2.28**

---

##  Estructura del Repositorio

```
Barcelona-Electricity-Consumption-Analysis/
│
├── README.md                                    # 📖 Documentación principal
├── Barcelona_Electricity_Consumption_Analysis_GuzmanWilliam.ipynb
│   └── # Notebook principal con análisis completo
│
├── datasets/
│   ├── 2019_consum_electricitat_bcn.csv        # Datos 2019
│   ├── 2020_consum_electricitat_bcn.csv        # Datos 2020
│   ├── 2021_consum_electricitat_bcn.csv        # Datos 2021
│   ├── 2022_consum_electricitat_bcn.csv        # Datos 2022
│   ├── 2023_consum_electricitat_bcn.csv        # Datos 2023
│   ├── 2024_consum_electricitat_BCN.csv        # Datos 2024
│   └── 2025_consum_electricitat_BCN.csv        # Datos 2025 (parcial)
│
├── results/
│   ├── visualizations/                          # Gráficos generados
│   ├── models/                                  # Modelos entrenados
│   └── reports/                                 # Reportes finales
│
└── .gitignore                                   # Archivos ignorados
```

---

## Instalación y Configuración

### Requisitos Previos
- **Python 3.8+**
- **pip** o **conda**
- Conocimientos de estadística y ML (recomendado)

### Opción 1: Google Colab (Recomendado ⭐)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/williamG7/Barcelona-Electricity-Consumption-Analysis/blob/main/Barcelona_Electricity_Consumption_Analysis_GuzmanWilliam.ipynb)

**Ventajas:**
- ✅ Sin instalación de dependencias
- ✅ Entorno pre-configurado con GPU/TPU
- ✅ Ejecución rápida
- ✅ Integración con Google Drive

**Pasos:**
1. Click en el botón [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)]
2. Ir a `Entorno de ejecución` → `Cambiar tipo de entorno`
3. Seleccionar GPU o TPU (opcional)
4. Ejecutar las celdas en orden

### Opción 2: Instalación Local

#### Paso 1: Clonar el Repositorio
```bash
git clone https://github.com/williamG7/Barcelona-Electricity-Consumption-Analysis.git
cd Barcelona-Electricity-Consumption-Analysis
```

#### Paso 2: Crear Entorno Virtual
```bash
# Con venv
python -m venv env
source env/bin/activate  # Windows: env\Scripts\activate

# O con conda
conda create --name barcelona-analysis python=3.9
conda activate barcelona-analysis
```

#### Paso 3: Instalar Dependencias
```bash
pip install -r requirements.txt
```

#### Paso 4: Ejecutar Jupyter Notebook
```bash
jupyter notebook Barcelona_Electricity_Consumption_Analysis_GuzmanWilliam.ipynb
```

---

## Datos del Proyecto

### Origen de Datos
- **Fuente:** Barcelona Open Data (AJUNTAMENT DE BARCELONA)
- **Dataset:** Consum d'Electricitat per code postal i sector econòmic
- **Período:** 2019 - 2025 (7 años)
- **Registros:** 1,665,130 filas de datos

### Estructura de Datos

| Campo | Tipo | Descripción |
|-------|------|------------|
| **Any** | Integer | Año del registro (2019-2025) |
| **Data** | String | Fecha en formato YYYY-MM-DD |
| **Codi_Postal** | String | Código postal (5 dígitos: 08xxx) |
| **Sector_Economic** | Categorical | Categoría: Indústria, Residencial, Serveis, No especificat |
| **Tram_Horari** | Categorical | Franja horaria: 00-06h, 06-12h, 12-18h, 18-24h |
| **Valor** | Numeric | Consumo en MWh |

### Estadísticas Generales

```
Total de Registros:     1,665,130
Período Analizado:      2019-2025 (7 años)
Códigos Postales:       42 zonas de Barcelona
Sectores Económicos:    4 categorías
Franjas Horarias:       5 intervalos
Consumo Total:          ~42 TWh (7 años)
Consumo Promedio:       ~25,829 MWh/registro
```

---

## Contenido y Análisis del Notebook

### 1️⃣ Carga y Preparación de Datos
```python
# Cargar múltiples archivos CSV
# Normalizar códigos postales
# Validar integridad de datos
# Detectar y tratar valores nulos
```

### 2️⃣ Exploración Exploratoria (EDA)
-  Estadísticas descriptivas
-  Análisis de distribuciones
-  Correlaciones variables
-  Patrones geoespaciales

### 3️⃣ Análisis por Dimensiones
- **Por Año:** Tendencias temporales de consumo
- **Por Sector Económico:** Comparativa Industria vs Residencial vs Servicios
- **Por Código Postal:** Mapa de consumo en Barcelona
- **Por Franja Horaria:** Patrones de demanda horaria

### 4️⃣ Modelos Predictivos (Regresión)
```python
# LinearRegression: Regresión lineal simple
# PolynomialFeatures: Regresión polinomial
# Métricas: MAE, MSE, R² Score
```

### 5️⃣ Árboles de Decisión
```python
# DecisionTreeClassifier: Identificar variables determinantes
# Feature Importance: Importancia de características
# Visualización de árbol de decisión
```

### 6️⃣ Algoritmos de Clasificación
```python
# LogisticRegression: Clasificación binaria/multiclase
# RandomForestClassifier: Ensamble de árboles
# KNeighborsClassifier: K-Nearest Neighbors
# Métricas: Accuracy, Precision, Recall, F1-Score
```

### 7️⃣ Clustering y Reducción Dimensional
```python
# KMeans: Agrupación de patrones de consumo
# PCA: Reducción a 2D para visualización
# Dendogramas de similitud
```

### 8️⃣ Visualizaciones Profesionales
-  Gráficos de barras y líneas
-  Mapas de calor (heatmaps)
-  Scatter plots con regresiones
-  Distribuciones geográficas

### 9️⃣ Propuestas de Mejora
-  Recomendaciones basadas en datos
-  Medidas de eficiencia energética
-  Plan de acción para sostenibilidad

---

##  Resultados Clave

### Consumo por Año (2019-2025)

| Año | Consumo Total (MWh) | Variación |
|-----|-------------------|-----------|
| 2019 | 6,947,665,788 | Base |
| 2020 | 6,130,748,798 | -11.8% ↓ |
| 2021 | 6,191,946,389 | +1.0% ↑ |
| 2022 | 6,320,521,670 | +2.1% ↑ |
| 2023 | 5,951,235,783 | -5.9% ↓ |
| 2024 | 5,998,510,712 | +0.8% ↑ |
| 2025 | 5,468,607,664 | -8.8% ↓ |

**Observación:** Tendencia decreciente desde 2019, con caída acentuada en 2025.

### Consumo por Sector Económico

| Sector | Consumo Total (MWh) | Porcentaje |
|--------|-------------------|-----------|
| **Servicios** | 24,130,786,622 | 57.5% |
| **Residencial** | 15,098,786,593 | 36.0% |
| **Industria** | 3,747,243,414 | 8.9% |
| **No especificado** | 32,420,175 | 0.1% |

**Insight:** Los servicios representan más de la mitad del consumo (hoteles, comercios, etc.).

### Consumo por Franja Horaria

| Franja | Consumo Total (MWh) | Porcentaje |
|--------|-------------------|-----------|
| 12:00-18:00 | 12,770,973,595 | 30.5% |
| 18:00-24:00 | 11,597,625,145 | 27.7% |
| 06:00-12:00 | 11,082,273,575 | 26.5% |
| 00:00-06:00 | 7,551,925,221 | 18.0% |
| No consta | 6,439,268 | 0.02% |

**Insight:** Máximo consumo en horario diurno (12-18h), mínimo en madrugada.

---

##  Metodología ML Utilizada

### 1. Regresión (Predicción)
```python
from sklearn.linear_model import LinearRegression
from sklearn.preprocessing import PolynomialFeatures

# Predecir consumo futuro basado en tendencias históricas
modelo = LinearRegression()
modelo.fit(X_train, y_train)
predicciones = modelo.predict(X_test)
```

**Métrica:** R² Score para evaluar bondad del ajuste

### 2. Árboles de Decisión (Feature Importance)
```python
from sklearn.tree import DecisionTreeClassifier, plot_tree

# Identificar variables más determinantes
arbol = DecisionTreeClassifier(max_depth=5)
arbol.fit(X_train, y_train)
importancia = arbol.feature_importances_
```

### 3. Clasificación
```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score, classification_report

# Clasificar niveles de consumo (bajo/medio/alto)
clasificador = RandomForestClassifier(n_estimators=100)
clasificador.fit(X_train, y_train)
accuracy = accuracy_score(y_test, y_pred)
```

### 4. Clustering
```python
from sklearn.cluster import KMeans
from sklearn.decomposition import PCA

# Agrupar zonas con patrones similares
kmeans = KMeans(n_clusters=4)
etiquetas = kmeans.fit_predict(X_normalizado)
```

---

##  Propuestas de Mejora Sostenible

Basadas en el análisis de datos:

###  Para Sector Residencial
- Campañas de concienciación sobre consumo eficiente
- Incentivos para instalación de paneles solares
- Aislamiento térmico en viviendas antiguas

###  Para Sector Industrial
- Auditorías energéticas obligatorias
- Certificación de eficiencia energética
- Subvenciones para maquinaria de bajo consumo

###  Para Sector de Servicios
- Sistemas de iluminación LED inteligentes
- Automatización de HVAC
- Monitoreo en tiempo real de consumo

###  Medidas Generales
- Tarificación variable por hora (peak pricing)
- Red inteligente (Smart Grid) en Barcelona
- Centro de control energético municipal

---

##  Consideraciones Éticas

Este proyecto respeta los siguientes principios:

### ✅ Valores del Proyecto
-  **Sostenibilidad ambiental** como prioritario
-  **Transparencia pública** en datos abiertos
-  **Rigor científico** en análisis
-  **Accesibilidad educativa** del conocimiento
-  **Responsabilidad social corporativa**

###  Uso de Datos
- ✅ Los datos son públicos (Barcelona Open Data)
- ✅ No contienen información personal sensible
- ✅ Uso exclusivamente para fines educativos y de mejora pública
- ✅ Cumplimiento GDPR y normativas de privacidad

---

##  Recursos y Referencias

### Documentación Oficial
- [Barcelona Open Data Portal](https://opendata-ajuntament.barcelona.cat)
- [ODS 2030 - UN Sustainable Development Goals](https://www.un.org/sustainabledevelopment/)
- [Scikit-learn Documentation](https://scikit-learn.org/)

### Tutoriales Relacionados
- [Pandas & Data Analysis - Real Python](https://realpython.com/learning-paths/pandas-data-science/)
- [Machine Learning A-Z - Andrew Ng](https://www.coursera.org/learn/machine-learning)
- [Time Series Analysis - Statquest with Josh Starmer](https://www.youtube.com/c/joshstarmer)

### Herramientas Complementarias
- **Google Colab:** Ejecución de notebooks en la nube
- **Jupyter Notebook:** Desarrollo interactivo
- **Pandas Profiling:** Generación automática de reportes EDA
- **Tableau/Power BI:** Visualización avanzada

### Publicaciones Relevantes
- Energy efficiency in smart buildings - IEEE
- Smart metering for sustainable cities - Journal of Environmental Sciences
- Machine learning for demand forecasting - Energy Policy

---

##  Troubleshooting

### Problema: `MemoryError` al cargar datos
```python
# Solución 1: Usar lectura por chunks
df_chunks = pd.read_csv('archivo.csv', chunksize=100000)
df = pd.concat(df_chunks, ignore_index=True)

# Solución 2: Usar dtypes eficientes
dtypes = {'Valor': 'int32', 'Codi_Postal': 'category'}
df = pd.read_csv('archivo.csv', dtype=dtypes)
```

### Problema: `ModuleNotFoundError: No module named 'sklearn'`
```bash
pip install scikit-learn --upgrade
```

### Problema: Descargas lentas en Colab
```python
# Usar caché de Colab
from google.colab import drive
drive.mount('/content/drive')
```

### Problema: Gráficos no visibles en Jupyter
```python
import matplotlib.pyplot as plt
%matplotlib inline
```

---

##  Contribuciones

¡Las contribuciones son bienvenidas! Para mejorar este proyecto:

1. **Fork** el repositorio
2. Crea una rama: `git checkout -b feature/mejora`
3. Commit cambios: `git commit -m "Add feature"`
4. Push: `git push origin feature/mejora`
5. Abre un **Pull Request**

**Directrices:**
- Mantén el código documentado
- Incluye docstrings en funciones
- Actualiza este README si es necesario
- Respeta los principios éticos

---

##  Licencia

Este proyecto está bajo licencia **MIT** para fines educativos y de investigación.

```
MIT License - Barcelona Electricity Consumption Analysis

Copyright (c) 2024 William Guzmán

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 👨‍💻 Autor

**William Guzmán**

- 🔗 **GitHub:** [@williamG7](https://github.com/williamG7)

---

## ⭐ Apoya el Proyecto

Si este análisis te ha resultado útil:

- ⭐ **Dale una estrella** en GitHub
- 🍴 **Fork** para contribuir
- 📢 **Comparte** con la comunidad
- 💬 **Deja feedback** en las issues
- 🌍 **Usa los datos** para mejoras sostenibles

---

## 📊 Estadísticas del Proyecto

![GitHub stars](https://img.shields.io/github/stars/williamG7/Barcelona-Electricity-Consumption-Analysis?style=social)
![GitHub forks](https://img.shields.io/github/forks/williamG7/Barcelona-Electricity-Consumption-Analysis?style=social)
![Python Version](https://img.shields.io/badge/Python-3.8+-blue?logo=python)
![Pandas](https://img.shields.io/badge/Pandas-1.3+-green?logo=pandas)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-orange?logo=scikit-learn)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter)
![License MIT](https://img.shields.io/badge/License-MIT-green)
![Data Science](https://img.shields.io/badge/Data%20Science-ML%20%2F%20Analytics-blue)
![Sustainable](https://img.shields.io/badge/Sustainable-ODS%202030-brightgreen)


---

###  UN Sustainable Development Goals Alignment

Este proyecto contribuye a los siguientes ODS:

-  **ODS 7:** Energía asequible y no contaminante
-  **ODS 11:** Ciudades y comunidades sostenibles
-  **ODS 12:** Producción y consumo responsables
-  **ODS 17:** Alianzas para lograr los objetivos

---

**¿Te gustó este proyecto? ⭐ Dale una estrella en GitHub y ayuda a difundir sostenibilidad energética**
