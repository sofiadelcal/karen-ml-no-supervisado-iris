# Iris: agrupamiento y reducción de dimensionalidad

Cuaderno de Karen Sofía Delgado Calderon para **R1-A3-S12, Introducción a Machine Learning**.

[Abrir el cuaderno en Google Colab](https://colab.research.google.com/github/sofiadelcal/karen-ml-no-supervisado-iris/blob/main/Karen_ML_No_Supervisado_Colab.ipynb)

Se estandarizan las cuatro medidas de Iris y se comparan K-means, Ward y una prueba de DBSCAN. Después se proyectan las flores con PCA y se comprueba la reconstrucción de rango dos mediante SVD. Las especies solo se consultan al calcular el ARI al final; no entran al entrenamiento.

El cuaderno incluye salidas ejecutadas. Para repetirlo en Colab, abre el enlace y selecciona **Entorno de ejecución > Ejecutar todo**. Los archivos de `resultados/` se vuelven a generar; no hay que cargar datos externos. Si lo ejecutas localmente, instala `requirements.txt` y usa Python 3.

Los resultados más relevantes son una silueta de 0,4599 para K-means con tres grupos y 0,5818 para dos. Elegir tres responde al ejercicio de la guía del curso y no al máximo de la silueta. Dos componentes PCA retienen el 95,81 % de la varianza. El informe explica por qué estas cifras no bastan para identificar correctamente todas las especies.

Datos: `sklearn.datasets.load_iris`. Fuente de la práctica: *Guía implementación de Clustering*, REA 1, Universidad de Cundinamarca.
