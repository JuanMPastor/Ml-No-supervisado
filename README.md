# Segmentación de inmuebles en arriendo con K-Means y PCA

Trabajo de Machine Learning no supervisado. Especialización en Inteligencia Artificial, Universidad de Cundinamarca. Asignatura: Introducción a Machine Learning (2026-2).

Autor: Juan Manuel Pastor Salamanca Docente: Ing. Wilson Mauro Rojas Reales
---

## Descripción

Una inmobiliaria administra un portafolio de inmuebles en arriendo y no cuenta con una clasificación que permita identificar segmentos comerciales. Este proyecto busca responder:

> ¿Existen grupos naturales de inmuebles según sus características físicas, económicas y geográficas, y cómo ayuda la reducción de dimensionalidad a visualizarlos e interpretarlos?

Para ello se aplican:

| Técnica | Propósito |
|---|---|
| **K-Means** (k = 2, 3 y 4) | Descubrir segmentos de inmuebles con características similares |
| **PCA** | Reducir dimensionalidad, estudiar la varianza explicada y visualizar los grupos en el plano PC1–PC2 |
| Clustering jerárquico y SVD truncado (anexo) | Complementar y contrastar los resultados |

## Dataset

Archivo Excel con inmuebles en arriendo. El identificador se conserva para reconocer registros, pero **no se usa para calcular distancias**.

## Contenido del notebook

**Parte A – K-Means**
1. Lectura del Excel y escalado de variables numéricas.
2. Ejecución con k = 2, k = 3 y k = 4 (`random_state=42`, `n_init=10`).
3. Resultados por modelo.
4. Comparación de k.

**Parte B – PCA**
1. Preprocesamiento: escalado de numéricas y *one-hot* de categóricas.
2. PCA completo (varianza acumulada) y PCA de 2 componentes.
3. Gráfico PC1–PC2 coloreado por cluster.


## Cómo ejecutarlo

### Local
```bash
git clone https://github.com/TU_USUARIO/segmentacion-inmuebles-kmeans-pca.git
cd segmentacion-inmuebles-kmeans-pca
pip install -r requirements.txt
jupyter notebook notebooks/
```
> El notebook usa `google.colab.files.upload()`. Para ejecutarlo fuera de Colab, reemplaza esa celda por `df_base = pd.read_excel("data/DATASET_INmuebles.xlsx")`.

## Decisiones metodológicas

- El ID del inmueble queda fuera de los cálculos de distancia.
- Las variables numéricas se estandarizan (`StandardScaler`) porque K-Means y PCA dependen de distancias y varianzas.
- **Estrato** se trata como numérica ordinal.
- En la Parte A solo intervienen variables numéricas; localidad y tipo se usan para describir los grupos. En la Parte B se incluyen con *one-hot*.
- Los clusters se renumeran por precio medio (0 = más económico).

## Tecnologías

Python · pandas · NumPy · scikit-learn · SciPy · matplotlib · seaborn · openpyxl · Google Colab

## Nota académica

Proyecto desarrollado con fines educativos, el dataset utilizado fue compartido por el profesor para uso academico.
