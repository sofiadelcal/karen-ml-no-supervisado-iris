# Iris: agrupamiento y reducción de dimensionalidad

Trabajo de Karen para **R1-A3-S12 — Introducción a Machine Learning**, actividad 73638 de la Universidad de Cundinamarca.


## Pregunta y alcance

¿Qué grupos aparecen en las cuatro medidas de 150 flores y cuánto se conserva al pasar a dos componentes? Se comparan K-means, Ward y DBSCAN. PCA y SVD permiten medir la pérdida de la representación bidimensional. Las clases conocidas se usan únicamente al calcular ARI después del ajuste.

## Ejecutar desde cero

1. Abre el enlace de Colab y elige **Entorno de ejecución > Ejecutar todo**.
2. Espera a que termine la última celda de código; debe indicar que las comprobaciones se superaron.
3. Revisa tablas y gráficos. La carpeta `resultados/` se vuelve a generar con los cálculos de esa ejecución.

No se necesita montar Drive, descargar datos externos ni configurar claves. Colab incluye las bibliotecas utilizadas. Para ejecución local, crea un entorno Python, instala las dependencias y abre el notebook en Jupyter:

```bash
python -m pip install -r requirements.txt
python -m pip install jupyter
jupyter notebook
```

El notebook muestra las versiones de Python y las bibliotecas de cada ejecución. Se conserva semilla 42 y 20 inicializaciones de K-means. El redondeo, la numeración de los clusters y los signos de componentes PCA pueden variar sin alterar la interpretación.

## Resultados del experimento

| Método | Silueta | Davies–Bouldin | ARI externo |
|---|---:|---:|---:|
| K-means | 0,4599 | 0,8336 | 0,6201 |
| Ward | 0,4467 | 0,8035 | 0,6153 |
| DBSCAN | 0,6018 | 0,5568 | 0,5401 |

DBSCAN encuentra dos grupos y seis muestras de ruido; su silueta y Davies–Bouldin excluyen esas seis muestras. No se compara como si utilizara las mismas 150 flores. La mejor silueta del barrido aparece con k=2; k=3 se conserva como contraste didáctico. PCA retiene 95,81 % de varianza y SVD de rango dos tiene error relativo 0,2046.

El cuadrado del error relativo coincide con la fracción de varianza descartada. Una proyección clara no demuestra separación perfecta ni capacidad de generalización.

## Contenido del repositorio

| Archivo | Para qué sirve |
|---|---|
| `Karen_ML_No_Supervisado_Colab.ipynb` | Código, explicación, resultados visibles y comprobaciones de consistencia |
| `Karen_Informe_ML_No_Supervisado_APA.pdf` | Informe actualizado, figuras, análisis y referencias APA |
| `requirements.txt` | Dependencias para ejecución local |
| `resultados/seleccion_k.csv` | Barrido de grupos e inercia/silueta |
| `resultados/comparacion_metodos.csv` | Métricas de los algoritmos |
| `resultados/resumen.json` | Resumen numérico del experimento |
| `resultados/*.png` | Figuras generadas por el notebook |

## Límites

Los grupos podrían ayudar a revisar mediciones botánicas, pero no identifican automáticamente especies ni diagnostican flores. La marca de ruido de DBSCAN depende de sus parámetros. No se han realizado pruebas con muestras externas ni un estudio de estabilidad entre semillas. Las comprobaciones automáticas revisan integridad numérica, no validez científica.

## Fuentes

- Scikit-learn developers. (s. f.). [Clustering](https://scikit-learn.org/stable/modules/clustering.html).
- Scikit-learn developers. (s. f.). [PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html).
- Scikit-learn developers. (s. f.). [load_iris](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_iris.html).
- Universidad de Cundinamarca. (s. f.). *Guía implementación de Clustering*. REA 1, material del curso.

Revisión: 28 de octubre de 2026. El cuaderno original se verificó también en Google Colab el 27 de octubre; esta revisión se volvió a ejecutar localmente con todas las salidas guardadas.
