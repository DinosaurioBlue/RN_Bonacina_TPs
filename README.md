# Redes Neuronales — Trabajos prácticos

Clasificación de documentos de 20 Newsgroups mediante un MLP y regresión Softmax. El trabajo principal es `MLP_TP.ipynb`, que incluye el desarrollo, los resultados y los gráficos.

> [!WARNING]
> **Tiempo de ejecución:** ejecutar todo el notebook repite dos búsquedas de hiperparámetros: 100 trials de MLP y 100 de Softmax, con hasta 5 épocas por trial y pruning. En el equipo utilizado, con CPU y hasta 4 hilos, las búsquedas demoraron aproximadamente **20 minutos**: 10,5 minutos para MLP y 9,1 minutos para Softmax. La primera ejecución puede tardar más por las descargas y la preparación inicial de los datos. El tiempo depende del equipo. Para leer los resultados y ver los gráficos guardados no es necesario ejecutar las celdas.

## Archivos principales

| Archivo | Contenido |
|---|---|
| `MLP_TP.ipynb` | Trabajo de MLP y comparación con Softmax, con resultados de train, validación y test. |
| `estructuraMLP.txt` | Definición de la metodología y del espacio de hiperparámetros. |
| `EnunciadoMLP.txt` | Consigna del trabajo práctico. |
| `requirements.txt` | Dependencias de Python. |
| `01_Softmax_Regression_20Newsgroups.ipynb` | Trabajo previo de regresión Softmax. |
| `clasificacion_de_textos.ipynb` | Notebook de clasificación de textos de referencia. |

## Reproducción

Desde la carpeta del repositorio, instalar las dependencias con `python -m pip install -r requirements.txt`. Abrir `MLP_TP.ipynb` en VS Code o Jupyter, seleccionar ese mismo entorno como kernel y ejecutar las celdas en orden, usando la carpeta del repositorio como directorio de trabajo. Se verificó con Python 3.14.5 y PyTorch 2.14.1+cpu; las dependencias no tienen versiones fijadas.

La primera ejecución requiere Internet para descargar 20 Newsgroups y los recursos de NLTK. No requiere modelos ni cachés preexistentes: las búsquedas entrenan los modelos y generan los archivos de preprocesamiento y los registros locales. Los resultados y gráficos entregados se pueden consultar sin ejecutar el notebook.

## Metodología y resultados

Se utilizan 9.051 documentos de train, 2.263 de validación y 7.532 de test, con semilla 42. Optuna TPE selecciona hiperparámetros mediante accuracy de validación y MedianPruner detiene trials poco prometedores. TensorBoard y MLflow registran las métricas. El vocabulario y el escalado se ajustan exclusivamente con train.


La configuración de entrega tiene `EVALUATE_TEST = True` para reproducir la evaluación final. Durante una nueva búsqueda exploratoria debe mantenerse en `False`; test se evalúa después de cerrar la selección y no se utiliza para ajustar hiperparámetros. Activar este flag por sí solo no vuelve a entrenar los modelos.

Al ejecutar el notebook, los modelos seleccionados se guardan en `modelos/` junto con su preprocesamiento y se verifica que su recarga reproduzca las predicciones de validación. Estos archivos se generan localmente y no se incluyen en el repositorio.

Los registros locales de MLflow, TensorBoard y las salidas de experimentos anteriores no forman parte de la entrega. El notebook contiene los gráficos y las métricas necesarios para revisar los resultados.
