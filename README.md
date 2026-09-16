
# Análisis Exploratorio de Datos Clínicos: Infección por VIH/SIDA

<div align="center">

**Facultad de Ciencias, UNAM**  
**Materia:** Matemáticas Aplicadas  
**Autores:** 
* Andrés Roberto Galán Reséndiz
* Argenis Daniel Olivares Hernandez
* Paulina Ramos Reyes

</div>

---

##  Descripción del Proyecto

Este repositorio contiene la **Práctica 1 de Análisis Exploratorio de Datos (EDA)** enfocada en registros clínicos relacionados con la infección por VIH/SIDA. El objetivo principal de este trabajo es trascender la simple visualización univariada para comprender cómo interactúan las variables clínicas, demográficas y de tratamiento mediante un enfoque multivariado.

A través de herramientas estadísticas y de reducción de dimensionalidad, este análisis busca identificar patrones de comportamiento inmunológico (especialmente en los conteos celulares de CD4 y CD8) y su relación con la progresión o presencia de la infección.

---

## Estructura del Repositorio

* `TareaPráctica1.ipynb` (o `AIDS_Classification (3).ipynb`): Notebook principal que contiene todo el código ejecutable en Python para el procesamiento de datos, estadísticas descriptivas, análisis de correlación y visualizaciones multivariadas.
* `AIDS_Classification (3).csv`: Conjunto de datos clínico original utilizado para la práctica.
* `Presentacion_Analisis_Exploratorio_AIDS.pptx.pdf`: Resumen visual y ejecutivo de los hallazgos principales de la práctica.
* `README.md`: Documentación oficial del repositorio.

---

## Estructura de los Datos

El conjunto de datos consta de **2,139 observaciones** (pacientes) y **23 variables** clínicas y demográficas, sin valores faltantes ni filas duplicadas, lo que permite un enfoque directo en el análisis relacional. Las variables clave que guían el estudio son:

* **Demográficas:** `age` (edad), `wtkg` (peso).
* **Clínicas e Inmunológicas:** `cd40` (CD4 inicial), `cd420` (CD4 a las 20 semanas), `cd80` (CD8 inicial), `cd820` (CD8 posterior).
* **Historial y Estado:** `hemo` (hemofilia), `drugs` (uso de drogas), `karnof` (estado funcional), `preanti` (tratamiento previo).
* **Variable Objetivo:** `infected` (indicador de infección/progresión a SIDA).

---

## Preguntas de Investigación Guías

El análisis está estructurado para dar respuesta sistemática a las siguientes interrogantes clínicas y estadísticas:

1. ¿Qué características de los pacientes se relacionan con la infección?
2. ¿Cómo se comportan conjuntamente las variables clínicas, demográficas y de tratamiento?
3. ¿Los pacientes que comienzan con valores altos de CD4 los conservan después del tiempo ($20$ semanas)?
4. ¿Hay alguna relación observable entre la edad y los niveles de CD4?
5. ¿El peso influye en los patrones de las células CD4?

---

##  Metodología y Técnicas Aplicadas

El proyecto se divide en fases analíticas bien definidas implementadas en Python:

### 1. Mantenimiento y Verificación de Datos
* Revisión de consistencia, conteo de nulos ($0$) y duplicados ($0$).

### 2. Estadísticas Descriptivas y Univariadas
* Análisis de distribución de la variable objetivo (`infected`), mostrando un desbalance de clases favorable a la clase $0$.
* Histogramas de celdas CD4 iniciales y posteriores para evaluar la concentración de pacientes infectados hacia conteos más bajos.
* Diagramas de caja (*Boxplots*) para identificar valores atípicos (*outliers*) en los conteos celulares de CD8.

### 3. Análisis de Correlación y Estabilidad Temporal
* Matriz de correlación de Pearson para variables continuas (`age`, `wtkg`, `cd40`, `cd420`, `cd80`, `cd820`).
* Evaluación de la persistencia temporal mediante coeficientes de correlación entre momentos iniciales y posteriores ($r = 0.58$ para CD4; $r = 0.76$ para CD8).

### 4. Técnicas Multivariadas
* **Gráfico de Coordenadas Paralelas:** Normalización con `MinMaxScaler` para visualizar trayectorias multivariadas de los pacientes según su estado de infección.
* **Curvas de Andrews:** Representación funcional de observaciones multivariadas para examinar la superposición estructural entre clases.
* **t-SNE (t-Distributed Stochastic Neighbor Embedding):** Reducción de dimensionalidad no lineal ($2D$) estandarizada para buscar agrupaciones locales y patrones de separación de la variable `infected`.

---

##  Conclusiones Principales

* **Dinámica Inmunológica:** Los conteos de CD4 y CD8 son los mejores conectores temporales. Se observa una persistencia moderada en CD4 ($r = 0.58$) y una mayor estabilidad estructural en CD8 ($r = 0.76$).
* **Concentración de Riesgo:** La clase con infección confirmada muestra una mayor concentración de pacientes con recuentos bajos de CD4 tanto al inicio como a las 20 semanas.
* **Independencia Lineal Demográfica:** La edad y el peso presentan correlaciones prácticamente nulas ($r \approx -0.04$ y $r \approx 0.02$) con los niveles de CD4 de forma lineal en este conjunto de datos.
* **Complejidad Multivariada:** Las técnicas de coordenadas paralelas, Curvas de Andrews y t-SNE demuestran un fuerte traslape entre clases, indicando que la infección no responde a una sola característica aislada, sino a un patrón multivariado complejo.

---

## Cómo Ejecutar el Código

Puedes ejecutar este proyecto de dos formas principales:

### Opción A: Google Colab (Recomendado)
1. Sube el archivo `AIDS_Classification.ipynb` y el conjunto de datos `AIDS_Classification.csv` a tu Google Drive.
2. Abre el notebook directamente en [Google Colab](https://colab.research.google.com/).
3. Ejecuta la celda de montaje de Google Drive si es necesario para enlazar la ruta del archivo CSV:
   ```python
   from google.colab import drive
   drive.mount('/content/drive')
   ```
4. Ejecuta las celdas secuencialmente de arriba a abajo.

### Opción B: Entorno Local (Jupyter Notebook / Lab)
1. Clona este repositorio en tu máquina local:
   ```bash
   git clone https://github.com/tu-usuario/tu-repositorio.git
   cd tu-repositorio
   ```
2. Asegúrate de tener instalado Python y las librerías requeridas:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn
   ```
3. Inicia Jupyter Notebook:
   ```bash
   jupyter notebook
   ```
4. Abre el archivo `AIDS_Classification.ipynb` y asegúrate de actualizar la ruta del archivo CSV en la celda de lectura si es necesario (`pd.read_csv("AIDS_Classification.csv")`).

---

## Licencia

Este proyecto se distribuye con fines académicos y educativos para la Facultad de Ciencias de la UNAM.
