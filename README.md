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
<br>
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


### Limpieza de datos: 
Una vez cargados los datos en un DataFrame de Pandas se procede a su tratamiento y manipulación para obtener una base limpia, luego se construye la función que retornará el precio promedio del Bitcoin.

### Tomar decisiones: 
Con la obtención del precio promedio, se compara con el precio actual y tendencia del Bitcoin, que previamente se obtuvo con Web Scraping, con estas tres variables crearemos la función que retornará el algoritmo de decisión, el cual es un algoritmo simple que ayudará a los clientes inexpertos a decidir el mejor momento de comprar o vender Bitcoin.

### Visualización: 
Se utiliza la librería Matplotlib para crear una función que retornará el gráfico donde se mostrará la evolución del precio del Bitcoin durante el periodo seleccionado al obtener los datos históricos, se dibujarán dos líneas: una fluctuante que indica el movimiento del precio y la otra plana que representa el precio promedio. Por último, se muestra un mensaje en el gráfico que indique “Vender”, “Comprar” o “Esperar” según sea la decisión del algoritmo.<br>
<br>

### Automatización: 
Finalmente, ahora que se tienen: la extracción de información,  la limpieza de datos, la visualización, y el algoritmo de decisión, es hora de automatizar el proceso. Se utiliza la librería de Python "time" para ejecutar el algoritmo de decisión cada 5 minutos y actualizar el gráfico, además del método clear_output para limpiar el gráfico antes de volver a iniciar el ciclo.<br>

#aluraChallengeRobotTrading.
<br>

