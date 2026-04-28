# Detección de fraude en transacciones financieras

Proyecto de Machine Learning orientado a la detección de fraude en transacciones financieras, abordando un escenario real de desbalance extremo de clases mediante preprocesamiento, técnicas de balanceo y ajuste de umbral.

---

## Objetivo

Desarrollar modelos capaces de identificar transacciones fraudulentas, evaluando el equilibrio entre:

- Recall: capacidad de detectar fraudes reales.
- Precision: reducción de falsos positivos.

---

## Dataset

Fuente: Kaggle - Credit Card Fraud Detection

El dataset contiene más de 280.000 transacciones, donde aproximadamente el 0.17% corresponde a fraude. Esto representa un problema altamente desbalanceado, típico en escenarios reales.

---

## Metodología

### Preprocesamiento
- Escalado de variables `Amount` y `Time`.
- Separación en entrenamiento y prueba con estratificación.
- Análisis exploratorio de datos.

### Manejo de desbalance
- Aplicación de SMOTE sobre el conjunto de entrenamiento.
- Comparación con modelo base sin balanceo.

---
## Modelos
![Modelos](https://github.com/user-attachments/assets/3ef67590-a40a-4599-b4da-e3b3c5d473f1)
---
## Resumen de evaluación de modelos

### Logistic Regression - SIN SMOTE
El modelo base presenta buena precisión, pero menor capacidad para detectar fraudes. Esto significa que genera pocas falsas alertas, pero deja pasar una cantidad relevante de transacciones fraudulentas.

### Logistic Regression - CON SMOTE
Al aplicar SMOTE, el modelo mejora fuertemente la detección de fraude. Sin embargo, aumenta la cantidad de falsos positivos, generando más alertas incorrectas.

### Logistic Regression + SMOTE + Umbral 0.8
El ajuste de umbral permite reducir los falsos positivos respecto al modelo con SMOTE estándar, manteniendo un recall alto. Este enfoque mejora el equilibrio entre detección y costo operativo.

### Random Forest + SMOTE + Umbral 0.8
Random Forest presenta la mejor precisión general. Reduce casi por completo los falsos positivos, aunque detecta menos fraudes que Logistic Regression con SMOTE. Es el modelo más adecuado si se busca estabilidad operativa.

---

## Ajuste de umbral
Evaluación de distintos umbrales para controlar el trade-off entre precision y recall.
![Impacto del umbral](https://github.com/user-attachments/assets/33b35c85-8a6b-4c9d-b093-c5bdfc5f3ee7)

- Precision aumenta al subir el umbral, reduciendo falsos positivos.
- Recall disminuye levemente, manteniéndose alto.
- F1-score mejora al encontrar un mejor equilibrio.

---

## Resultados

![Comparación de modelos](https://github.com/user-attachments/assets/ac5e6115-f904-477d-aab3-c48f47c2678c)

| Modelo | Recall | Precision |
|--------|--------|----------|
| Logistic Regression (base) | 0.64 | 0.83 |
| Logistic Regression + SMOTE | 0.90 | 0.14 |
| Random Forest + SMOTE | 0.76 | 0.96 |


---

## Conclusión

- Este proyecto aborda un problema real de detección de fraude bajo condiciones de desbalance extremo, donde la elección del modelo no puede basarse en métricas tradicionales como accuracy, sino en el equilibrio entre recall y precision.
- Los resultados muestran que el modelo base (Logistic Regression sin balanceo) presenta una alta precisión, pero falla en detectar una proporción importante de fraudes, lo que lo hace inadecuado para escenarios donde el riesgo financiero es alto. Al aplicar SMOTE, se logra un aumento significativo en el recall, permitiendo detectar la mayoría de los fraudes. Sin embargo, esto introduce una gran cantidad de falsos positivos, generando un costo operativo elevado.
- El ajuste de umbral demuestra ser una herramienta clave para controlar este comportamiento, permitiendo reducir los falsos positivos sin perder completamente la capacidad de detección. Este paso es crítico, ya que evidencia que el rendimiento del modelo no depende únicamente del algoritmo, sino también de cómo se define la toma de decisión.
- En términos generales, el proyecto demuestra tres puntos clave: primero, que el manejo de datos desbalanceados es determinante en problemas de fraude; segundo, que las métricas deben alinearse con el contexto de negocio; y tercero, que el ajuste de umbral es una técnica fundamental para transformar un modelo técnico en una solución aplicable.

*El modelo Random Forest con SMOTE y ajuste de umbral resulta más adecuado para escenarios productivos donde el costo de falsos positivos es relevante. Permite reducir significativamente alertas incorrectas manteniendo una capacidad aceptable de detección.*

---

## Tecnologías

- Python
- Pandas, NumPy
- Scikit-learn
- Imbalanced-learn (SMOTE)
- Matplotlib, Seaborn

---

## Aprendizajes

- Manejo de datos desbalanceados.
- Importancia de métricas más allá de accuracy.
- Ajuste de umbral como herramienta clave.
- Evaluación de modelos desde una perspectiva de negocio.

---

## Próximas mejoras

- Implementación de XGBoost.
- Análisis de importancia de variables.
- Curvas ROC y Precision-Recall.
- Pipeline reproducible.

---

## Autor
Jeanette Zenteno
Ingeniera de Software y Datos con enfoque en análisis, procesamiento de datos y desarrollo de soluciones basadas en Machine Learning.
