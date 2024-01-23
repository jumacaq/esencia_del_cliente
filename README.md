![](https://github.com/jumacaq/esencia_del_cliente/blob/main/Challenge_3.webp)
# Conociendo la esencia del cliente
La junta directiva de la cadena de supermercados Universal Food ha observado una estabilización en sus ventas y busca comprender cómo mejorar la relación con sus clientes, entendiendo sus hábitos de compra, para ofrecerles un servicio de mayor calidad.
## Descripción: 
Desarrollaremos un modelo de machine learning del tipo clusterización para agrupar a los clientes considerando sus características, preferencias y habitos de consumo; para ello contamos con un Dataset que tiene más de 60.000 clientes que contiene sus INGRESOS, DETALLES DE PROMOCIÓN, DATOS DE LA TIENDA, DATOS DE VENTAS, COSTO DE MEDIOS, entre otra información relevante.
El modelo estara dividido de la siguiente manera:
* Configuración del ambiente,
* Obtención y transformación de los datos,
* Exploración de los datos,
* Preprocesamiento y obtención de features.
* Validación de clusters
* Análisis e interpretación de clusters.


### Configuración del ambiente: 
Utilizaremos el Jupyter Notebook que ofrece Google Colaboratory, también necesitarás instalar algunas librerías de Python que son esenciales para este proyecto, como: <br>
- Numpy 
- Pandas 
- Matplotlib
- Seaborn
- SKlearn.preprocessing OneHotEncoder
- SKlearn.preprocessing StandardScaler
- SKlearn.cluster KMeans
- Sklearn.metrics silhouette_score, davies_bouldin_score, calinski_harabasz_score


### Obtención de datos:
Accede a las siguientes URLs para descargar el dataset que estaremos utilizando: https://www.kaggle.com/datasets/ramjasmaurya/medias-cost-prediction-in-foodmart <br> 

![image](https://github.com/jumacaq/esencia_del_cliente/blob/main/Kaggle_esencia_cliente.png)

Como el dataset original está en inglés, lo voy a dejar todo en español para una mejor comprensión del mismo.  Por este motivo, se utilizará un archivo de python que contiene los diccionarios con la respectiva traducción.


### Exploración de los datos: 
La exploración visual de datos permite a los científicos de datos examinar y explorar grandes volúmenes de datos de manera intuitiva y eficiente. Al representar los datos visualmente, se pueden identificar características importantes, como valores atípicos, distribuciones, correlaciones y agrupaciones, que podrían no ser evidentes al examinar solo los números o las tablas de datos.

Se trata de una herramienta poderosa para comprender, analizar y comunicar información clave presente en los conjuntos de datos, brindando una comprensión más profunda y facilitando la toma de decisiones informadas.

* Haciendo uso de Matplotlib y Seaborn voy a generar diversos gráficos para entender mejor nuestros datos.

* A través de varios gráficos, observaremos la distribución de ingresos anuales de los clientes.

* Debajo de un grupo de gráficos anotaré observaciones e hipótesis utilizando una celda de texto del notebook.

### Preprocesamiento y obtención de features: 
En esta fase utilizaré una forma de codificar las variables categóricas para que el modelo de clusterización las pueda reconocer. Usaré el método get_dummies de pandas, así como el método OneHotEncoder de la librería sklearn.preprocessing de Python, estableceré un valor numérico para las variables de acuerdo con mi percepción; por ejemplo, si quiero categorizar primaria, secundaria y universidad, podría decir que el valor numérico para primaria podría ser 1, el valor numérico para secundaria, 2, y así sucesivamente. (Es importante aclarar que en ejemplo citado, asignamos los valores a cada nivel porque sabemos que primaria es menor que secundaria, y secundaria menor que universidad)

* Tras establecer un método de codificación para las variables categóricas, debo reemplazar los valores numéricos asignados en el dataset para sustituir las cadenas de texto,
únicamente codificaré las columnas que considere que puedan ser relevantes para la clusterización.

* Teniendo en cuenta el paso anterior, seleccionaré las variables que sean más relevantes para el caso de estudio: Se desea agrupar a los clientes en diversos clusters para entender sus características y brindarles el mejor servicio.

* Con los atributos seleccionados,  procederemos a estandarizar nuestros datos (que en este punto deben ser todos numéricos) para que todas las variables puedan ser tenidas en cuenta dentro de una misma escala. Varios de los hiperparámetros utilizados en las funciones de un modelo de Machine Learning asumen que todas las características están centradas alrededor de 0 y tienen varianza en el mismo orden.
* Si uno de los atributos del dataset tiene una varianza con orden de magnitud muy superior al de los demás atributos, puede dominar la función del modelo y hacer que el estimador no aprenda correctamente de los otros atributos como se espera. Vamos a utilizar el método StandardScaler de la librería sklearn.preprocessing de Python para ello. Almacenaré los valores estandarizados en una variable llamada X_std.


### Validación de clusters: 
El algoritmo recomendado para la clusterización es KMeans, para hallar el mejor número de clusters.

Validación
* Número de clusters: Debes instanciar de 3 a máximo 10 clusters con el(los) algoritmo(s) seleccionado(s), utilizando X_std y obtener el puntaje de Silhouette, junto a otras métricas como Davies-Bouldin y Calinski and Harabasz para decidir cuál es la mejor configuración para el número de clusters.
Restricciones: (El puntaje mínimo de Silhouette debe ser de 0.50; el de Davies-Bouldin máximo de 0.75; y el de CalinskiHarabasz, el número más alto posible.)
Luego haremos una visualización para observar la regla del codo y luego mediante una fórmula matematica determinaremos el mejor número de clusters para nuestro modelo.

* Estructura: Evaluaremos la estructura de los clusters tomando como referencia una baseline. Para generar la baseline, vamos a generar números aleatorios con el módulo random de numpy con las mismas dimensiones del dataset X_std y lo almacenaré en una variable llamada random_data y luego voy a repetir la validación. Analizaré los puntajes da las métricas utilizadas para asegurar que el X_std tenga un desempeño muy superior al de random_data.

* Estabilidad: Finalmente, evaluaré la estabilidad de los clusters con el número de clusters seleccionado en la validación. Para ello, segmentaré X_std en 3 partes iguales, (me apoyaré en la función array_split() de numpy, y almacenaré cada fragmento del dataset en una variable llamada set_1, set_2, ..., set_n) y repetir los pasos de validación para el número de clusters escogido en cada uno de los sets. Aquí lo verdaderamente importante es que los puntajes no presenten una variación mayor a ±5% entre sí. Esto va a garantizar que hay homogeneidad en la composición de los clusters.

* Instanciando la mejor configuración de clusters: 
  Voy a instanciar el algoritmo de clusterización una vez , con la configuración escogida, y crearé un nuevo atributo en el dataset datos_raw llamado 'cluster' para almacenar los labels de los clusters.
  Luego haré varios gráficos de dispersión para comparar las variables añadiendo una tercera dimensión con los clusters en el parámetro hue del gráfico. Luego haré la descripción de los hallazgos en cada gráfico.


<br>

### Análisis e interpretación de clusters: 
* Los clusters generados tienen una descripción y ahora es el momento de analizar cada una da las descripciones.
 Crearé una celda de texto con el resultado consolidado de mi análisis.
* Aquí voy a elaborar una serie de recomendaciones de estrategias para personalizar la experiencia de los clientes en cada uno de los clusters; 
Aquí la idea es proponer acciones para los clientes según sus características de consumo.<br>

#AluraChallengeEsenciadelCliente  #AluraLatam
<br>

