# Fase 3 - Componente Práctico: Algoritmos de Clustering

**Curso:** Machine Learning (203008067)  
**Universidad:** UNAD — Universidad Nacional Abierta y a Distancia  
**Especialización:** Ciencia de Datos y Analítica  
**Grupo:** 03  
**Autor:** Wilmer Ricardo Urda — Código: 101719427  
**Tutor:** Rafael Gaitan  
**Período:** 2026-I

---

## Descripción

Práctica simulada remota que implementa y compara tres algoritmos clásicos de clustering no supervisado sobre dos datasets del repositorio OpenML. Cada ejercicio aplica el algoritmo a ambos datasets, incluye análisis de parámetros, visualizaciones y perfilamiento interpretativo de los clústeres resultantes.

---

## Archivo principal

| Archivo | Descripción |
|---|---|
| `G03_Wilmer_Urda_Fase3.ipynb` | Notebook principal con los tres ejercicios |
| `Guía de aprendizaje - Fase 3 - Componente práctico - Prácticas simuladas.pdf` | Guía oficial de la actividad |

---

## Datasets

| Dataset | OpenML ID | Registros | Descripción |
|---|---|---|---|
| **BUPA Liver Disorders** | 8 | 345 | Variables clínicas y enzimas hepáticas (mcv, alkphos, sgpt, sgot, gammagt, drinks) |
| **German Credit (credit-g)** | 31 | 1000 | Variables financieras y sociodemográficas de solicitantes de crédito |

Los datasets se cargan directamente con `sklearn.datasets.fetch_openml()`. No se requieren archivos locales.

---

## Ejercicios

### Ejercicio 1: K-Means Clustering

Segmentación mediante K-Means aplicando el **método del codo** y el **índice de Silhouette** para determinar el número óptimo de clústeres (k=3 en ambos datasets).

| Dataset | Variables | Silhouette |
|---|---|---|
| BUPA | 2 vars (mcv, alkphos) | 0.356 |
| BUPA | Todas las variables | 0.197 |
| German Credit | 2 vars (duration, credit_amount) | 0.423 |
| German Credit | Múltiples variables | 0.053 |

### Ejercicio 2: DBSCAN

Clustering basado en densidad. Los parámetros óptimos de épsilon se determinaron mediante la **gráfica k-distance** (regla heurística: `min_samples = 2 × n_features`).

| Dataset | ε | min_samples | Clústeres | Ruido |
|---|---|---|---|---|
| BUPA | 0.8 | 6 | 3 | 27 pts (8.8%) |
| German Credit | 0.6 | 6 | 3 | 54 pts (6.5%) |

### Ejercicio 3: Agglomerative Clustering

Clustering jerárquico aglomerativo con **Ward linkage**. El número de clústeres se determinó por el dendrograma (corte en la mayor distancia de fusión).

| Dataset | Clústeres | Distribución |
|---|---|---|
| BUPA | 3 | 79 / 71 / 129 puntos |
| German Credit | 3 | 423 / 242 / 165 puntos |

---

## Preprocesamiento

Para ambos datasets se aplicó el siguiente pipeline:

1. Eliminación de valores nulos
2. Exclusión de la variable objetivo
3. Remoción de outliers con método IQR (solo variables numéricas)
4. One-hot encoding para variables categóricas (German Credit)
5. Estandarización con `StandardScaler`

---

## Requisitos

```
python >= 3.8
pandas
numpy
scikit-learn
matplotlib
scipy
```

Instalación:

```bash
pip install pandas numpy scikit-learn matplotlib scipy
```

---

## Ejecución

Abrir el notebook en Jupyter Lab o Jupyter Notebook y ejecutar todas las celdas en orden:

```bash
jupyter notebook G03_Wilmer_Urda_Fase3.ipynb
```

Las celdas están numeradas con `execution_count` 40–78 (última ejecución completa y sin errores).
