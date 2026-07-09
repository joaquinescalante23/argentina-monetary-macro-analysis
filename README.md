# Análisis Integral de la Dinámica Monetaria y Cambiaria de la República Argentina
## Un Estudio Intertemporal del Impacto de las Políticas de Estabilización y la Deuda (2016-2017 vs. 2024-2025)

Este repositorio contiene el desarrollo del Proyecto Integrador de Machine Learning. El estudio analiza y compara empíricamente el comportamiento macrofinanciero de la economía argentina bajo dos esquemas de política monetaria y cambiaria diferenciados de la última década, y sobre ese análisis entrena y evalúa modelos de aprendizaje automático.

## Estructura del Proyecto

*   `proyecto_integrador_final.ipynb`: **Cuaderno de la entrega final.** Continúa el trabajo de la pre-entrega y agrega las etapas de modelado: definición del problema, entrenamiento y comparación de modelos, evaluación con métricas, validación cruzada, interpretación de errores, conclusiones y anexo.
*   `proyecto_integrador_preentrega.ipynb`: Cuaderno de la pre-entrega (carga de datos, procesamiento, feature engineering y EDA). Se conserva como referencia del avance previo.
*   `datasets/`: Directorio con las series de tiempo del BCRA, CNV, BYMA y BLS-EEUU empleadas en el análisis.
*   `.gitignore`: Exclusiones de archivos del entorno virtual y archivos temporales.

## Metodología y Enfoque Teórico

El análisis adopta un enfoque académico neutral y de economía política, contrastando dos regímenes:
1.  **Metas de Inflación (2016-2017):** Estrategia monetarista basada en el anclaje mediante tasas reales positivas (LEBAC) y flotación administrada, que desembocó en un proceso de endeudamiento externo internacional y el consecuente programa Stand-By firmado con el FMI en 2018.
2.  **Estabilización de Shock y Licuación (2024-2025):** Programa de emisión cero y superávit fiscal financiero de base, complementado con tasas reales negativas en su fase inicial (licuación de pasivos públicos y de salarios reales) y un esquema cambiario de *crawling peg*.

Se abordan variables clave como:
*   **Ecuación de Fisher:** Deflactación de tasas nominales (BADLAR y Adelantos) para medir el rendimiento real de los activos en moneda nacional.
*   **Tipo de Cambio Implícito en Obligaciones Negociables (ONs):** Reconstrucción del tipo de cambio corporativo libre frente a restricciones de cuenta de capital (cepo).
*   **Monetización Real:** Evolución del ahorro real en pesos y dólares de los residentes.

## Modelos de Machine Learning (Entrega Final)

Sobre el dataset consolidado (30 observaciones mensuales, 15 por régimen) se plantean dos problemas complementarios que ponen a prueba la hipótesis central del estudio:

*   **Regresión — Determinantes del ahorro real en pesos.** Se estima el saldo real de depósitos en pesos en función de las condiciones monetarias y cambiarias (tasa real, inflación, devaluación del TC implícito, actividad del mercado de ONs). Se comparan Regresión Lineal, Ridge y Random Forest, evaluados con MAE, RMSE y R², más validación cruzada K-Fold.
*   **Clasificación — Detección del régimen de licuación.** Se clasifica cada mes según tenga tasa real negativa (licuación) o positiva, usando únicamente la huella de comportamiento de los ahorristas (dolarización, depósitos reales, presión cambiaria) y excluyendo deliberadamente la tasa y la inflación para evitar fuga de información. Se comparan Regresión Logística y Random Forest, evaluados con precisión, recall, F1 y matriz de confusión, más validación cruzada estratificada.

## Ejecución en Google Colab

El cuaderno cuenta con un bloque de inicialización adaptativo. Si se ejecuta en entornos de nube como **Google Colab**, el script detectará el entorno y ofrecerá una interfaz interactiva de carga de archivos para subir los datasets en formato CSV desde su máquina local, organizándolos automáticamente en la estructura de directorios requerida.

Para ejecutarlo en Colab:
1.  Abra [Google Colab](https://colab.research.google.com).
2.  Importe el archivo `proyecto_integrador_final.ipynb`.
3.  Ejecute las celdas secuencialmente. Cuando se le solicite en la sección 3.1, suba los archivos de datos de la carpeta `datasets/` del repositorio.
