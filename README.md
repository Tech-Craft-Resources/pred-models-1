# Predicción de Colelitiasis — Dataset UCI

Modelos de clasificación para predecir la presencia de cálculos biliares a partir de variables clínicas y bioquímicas de rutina. Proyecto académico de modelos predictivos.

## Estructura del Proyecto

```
pred_models-1/
├── data/
│   ├── raw/           # dataset-uci.csv (datos originales)
│   └── processed/     # particiones train/test preprocesadas
├── docs/              # figuras, informe y documentación
├── notebooks/
│   ├── analisis.ipynb      # exploración de datos
│   ├── preprocesing.ipynb  # preprocesamiento
│   └── models.ipynb       # entrenamiento y evaluación
├── pyproject.toml
└── README.md
```

## Requisitos

- Python ≥ 3.13
- Dependencias: pandas, numpy, scikit-learn, matplotlib, seaborn, ipykernel

## Instalación

```bash
uv sync
# o
pip install -e .
```

## Uso

Ejecutar los notebooks en orden:

1. **analisis.ipynb** — Carga el dataset, divide train/test (80/20, random_state=123), realiza el análisis exploratorio y guarda las particiones crudas en `data/processed/`.
2. **preprocesing.ipynb** — Selección de variables, winsorización de outliers, escalado. Persiste los datos procesados.
3. **models.ipynb** — Entrena 5 modelos (DummyClassifier, Regresión Logística, Random Forest, Gradient Boosting, SVM), valida con CV k=5 y evalúa sobre test.

## Dataset

- **Fuente:** UCI Gallstone Dataset
- **Registros:** 319
- **Variables:** 38 predictoras + 1 objetivo (`Gallstone Status`)
- **Objetivo:** `0` = sano, `1` = enfermo (cálculos presentes)

## Modelo Recomendado

**Random Forest** — Accuracy 75 %, Recall clase 1 = 71.9 %, ROC-AUC = 0.844. Mayor precisión y menor tasa de falsos positivos que la Regresión Logística con igual sensibilidad.

## Informe

El informe completo se encuentra en `docs/informe.md`. Incluye contexto clínico, exploración, preprocesamiento, resultados de modelos e impacto clínico estimado.
