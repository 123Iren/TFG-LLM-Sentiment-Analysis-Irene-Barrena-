# Análisis de Sentimientos en Reseñas de Comercio Electrónico con LLMs Cuantizados

Este repositorio contiene el código y los resultados del Trabajo de Fin de Grado (TFG) centrado en el análisis de sentimientos en reseñas de productos de comercio electrónico en español mediante modelos de lenguaje de gran escala (LLMs) cuantizados y técnicas de *prompting*. El repositorio sirve como apoyo a la metodología y los resultados presentados en la memoria del TFG.

## Objetivo

El objetivo principal de este proyecto es evaluar si los LLMs cuantizados a 4 bits son capaces de clasificar sentimientos en reseñas de productos en español con un rendimiento competitivo, operando exclusivamente en hardware convencional (Google Colab gratuito con GPU Tesla T4).

## Alcance

- Evaluación comparativa de tres modelos cuantizados (LLaMA 3.1 8B, Qwen 2.5 7B, Mistral 7B) en consumo de memoria, latencia y perplejidad
- Aplicación de seis técnicas de *prompting* (zero-shot, one-shot, few-shot, chain-of-thought, role-based e iterative)
- Evaluación del rendimiento clasificatorio mediante F1 macro-promediada, matrices de confusión e intervalos de confianza al 95%

## Estructura del repositorio

```
├── notebooks/
│   ├── 01_seleccion_modelo.ipynb
│   └── 02_prompting_evaluacion.ipynb
├── data/
│   └── reseñas_evaluacion_200.csv
├── results/
│   ├── resultados_completos.json
│   ├── resultados_parciales_Llama.json
│   ├── resultados_parciales_Qwen.json
│   └── resultados_parciales_Mistral.json
└── README.md
```

## Descripción de los notebooks

- **01_seleccion_modelo.ipynb**: Evaluación comparativa de los tres modelos candidatos bajo criterios de eficiencia computacional (consumo de VRAM, latencia por reseña y perplejidad sobre WikiText-2). Corresponde a la Fase 1 de la metodología (Sección 4.1 del TFG).

- **02_prompting_evaluacion.ipynb**: Aplicación de las seis técnicas de *prompting* sobre los tres modelos cuantizados, extracción de predicciones y cálculo de métricas de clasificación. Corresponde a las Fases 2 y 3 de la metodología (Secciones 4.2 y 4.3 del TFG).

## Descripción del dataset

El archivo `data/reseñas_evaluacion_200.csv` contiene las 200 reseñas en español seleccionadas del corpus Amazon Reviews Multi (split de test) mediante muestreo aleatorio con semilla fija (seed=42). Cada fila incluye el texto de la reseña, la puntuación original (1-5 estrellas) y la etiqueta ternaria asignada (positivo, negativo, neutro).

## Resultados

La carpeta `resultados/` contiene los resultados de las 18 combinaciones modelo-técnica evaluadas. El archivo `resultados_completos.json` incluye, para cada combinación: métricas de clasificación (accuracy, F1-macro, precision, recall, F1 por clase, intervalos de confianza), predicciones individuales, prompts enviados y respuestas generadas por cada modelo. Los archivos parciales corresponden a las ejecuciones independientes de cada modelo en sesiones separadas de Google Colab.

## Tecnologías

- Python
- LLMs cuantizados (bitsandbytes, NF4 a 4 bits)
- Transformers (Hugging Face)
- Técnicas de *prompting*
- Métricas de clasificación (scikit-learn)
- Google Colab (GPU Tesla T4)

## Autora

Irene Barrena
