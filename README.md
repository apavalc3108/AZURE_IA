# AutoML + MLflow: Comparativa de modelos de clasificación

Proyecto de **Machine Learning** que reproduce un flujo similar a **Azure Machine Learning** utilizando herramientas gratuitas y de código abierto como **FLAML, MLflow y scikit-learn**.

El proyecto puede ejecutarse en **Google Colab** o localmente mediante **Jupyter Notebook**.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/apavalc3108/pavon_adrian_ML_AZURE/blob/main/notebooks/auto_ml_classification.ipynb)

---

## 🎯 Objetivo

El proyecto tiene como objetivos:

* Utilizar **AutoML** para encontrar automáticamente un modelo de clasificación.
* Registrar experimentos mediante **MLflow**.
* Comparar el modelo obtenido con un modelo baseline interpretable.
* Analizar diferentes métricas y umbrales de decisión.
* Aplicar principios de **evaluación responsable**.

---

## 📊 Dataset

Se utiliza el dataset **Diabetes Pima** de OpenML.

* **768 registros**
* **8 variables**
* Problema de **clasificación binaria**
* Variable objetivo: `tested_positive`
* Aproximadamente 65 % de casos negativos y 35 % positivos.

Si no existe conexión con OpenML, el notebook utiliza automáticamente el dataset **Breast Cancer** de `scikit-learn`.

---

## 🛠️ Tecnologías

| Tecnología         | Uso                            |
| ------------------ | ------------------------------ |
| **FLAML**          | AutoML                         |
| **MLflow**         | Tracking de experimentos       |
| **scikit-learn**   | Modelos y métricas             |
| **LightGBM**       | Modelo seleccionado por AutoML |
| **XGBoost**        | Gradient Boosting              |
| **pandas / NumPy** | Tratamiento de datos           |
| **matplotlib**     | Visualización                  |
| **Google Colab**   | Entorno de ejecución           |

---

## 📁 Estructura

```text
pavon_adrian_ML_AZURE/
├── README.md
├── LICENSE
├── requirements.txt
├── .gitignore
└── notebooks/
    └── auto_ml_classification.ipynb
```

---

## 🔬 Metodología

El proyecto sigue este flujo:

```text
Carga de datos
      ↓
Preparación de datos
      ↓
AutoML con FLAML
      ↓
Entrenamiento
      ↓
Tracking con MLflow
      ↓
Comparación de modelos
      ↓
Evaluación responsable
```

---

## 📈 Resultados

### Comparación de modelos

| Modelo                  |   Accuracy |        AUC |
| ----------------------- | ---------: | ---------: |
| **FLAML (LightGBM)**    | **0.7662** |     0.8179 |
| **Regresión Logística** |     0.7446 | **0.8379** |

FLAML obtiene una mayor **accuracy**, mientras que la Regresión Logística consigue un **AUC superior** y ofrece una mayor interpretabilidad.

### Umbral de decisión

| Umbral |   Accuracy |         F1 |
| -----: | ---------: | ---------: |
|    0.3 |     0.7576 | **0.6818** |
|    0.4 |     0.7576 |     0.6627 |
|    0.5 | **0.7662** |     0.6301 |
|    0.6 |     0.7446 |     0.5630 |
|    0.7 |     0.7359 |     0.4959 |

El **accuracy máximo** se obtiene con un umbral de 0.5, mientras que el **F1 máximo** aparece con un umbral de 0.3.

---

## 🔑 Conclusiones

1. **AutoML no siempre proporciona el modelo más adecuado.** FLAML obtiene mejor accuracy, pero la Regresión Logística consigue mejor AUC.
2. **La interpretabilidad es importante**, especialmente cuando las diferencias de rendimiento son pequeñas.
3. **El umbral 0.5 no es universal.** Dependiendo del objetivo, puede ser conveniente modificarlo.
4. **No debe utilizarse una única métrica** para decidir qué modelo es mejor.
5. En un contexto médico, los **falsos negativos** pueden ser especialmente importantes.

---

## 🚀 Ejecución

### Google Colab

Abre directamente el notebook:

[**Abrir en Google Colab**](https://colab.research.google.com/github/apavalc3108/pavon_adrian_ML_AZURE/blob/main/notebooks/auto_ml_classification.ipynb)

### Jupyter local

```bash
git clone https://github.com/apavalc3108/pavon_adrian_ML_AZURE.git
cd pavon_adrian_ML_AZURE
pip install -r requirements.txt
jupyter notebook notebooks/auto_ml_classification.ipynb
```

---

## 📦 Requisitos

```text
mlflow>=2.0
flaml[automl]>=2.0
xgboost>=2.0
scikit-learn>=1.3
pandas==2.2.3
matplotlib>=3.7
```

---

## 📜 Licencia

Este proyecto está bajo licencia **MIT**. Consulta el archivo [`LICENSE`](LICENSE).

---

## 👤 Autor

**Adrián Pavón**

GitHub: [@apavalc3108](https://github.com/apavalc3108)

---

⭐ **Proyecto de Machine Learning utilizando AutoML, MLflow y scikit-learn como alternativa gratuita a un flujo de Azure Machine Learning.**
