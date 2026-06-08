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
│   └── tfg_llm_sentiment.ipynb
├── data/
│   └── (el dataset se descarga automáticamente desde HuggingFace durante la ejecución)
├── results/
│   ├── resultados_completos.json
│   ├── resultados_parciales_Llama.json
│   ├── resultados_parciales_Qwen.json
│   └── resultados_parciales_Mistral.json
└── README.md
```

## Descripción del notebook

**tfg_llm_sentiment.ipynb**: Contiene todo el código del experimento, organizado en dos partes:

- **Parte 1 - Selección del modelo**: Evaluación comparativa de los tres modelos candidatos bajo criterios de eficiencia computacional (consumo de VRAM, latencia por reseña y perplejidad sobre WikiText-2). Corresponde a la Sección 4.1 del TFG.

- **Parte 2 - Prompting y evaluación**: Aplicación de las seis técnicas de *prompting* sobre los tres modelos cuantizados, extracción de predicciones y cálculo de métricas de clasificación. Corresponde a las Secciones 4.2 y 4.3 del TFG.

El notebook incluye celdas de texto que explican cada paso de la metodología.

## Dataset

El corpus utilizado es Amazon Reviews Multi (español), disponible públicamente en HuggingFace. Se seleccionan 200 reseñas del split de test mediante muestreo aleatorio con semilla fija (seed=42) y se mapean a tres clases: positivo (4-5 estrellas), negativo (1-2 estrellas) y neutro (3 estrellas). La descarga se realiza automáticamente al ejecutar el notebook.

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
