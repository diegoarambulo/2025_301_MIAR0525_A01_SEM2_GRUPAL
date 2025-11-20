### 2025_301_MIAR0525_A01_SEM3_GRUPAL
Repositorio grupal para los entregables de la actividad grupal de la semana 3 - Grupo 6

### Integrantes
* Diego Arambulo Vitores
* Jesus Zambrano Parrales
* Bryan Alvarado Quimiz

### Informacion sobre el dataset usado
Nuestro dataset fue obtenido del portal de bases abiertas y gratuitas [<a href="https://www.kaggle.com/">kaggle</a>], mas en especifico 
la denominada [<a href="https://drive.google.com/uc?id=1YmQ0UqU5UTKB_qkegpWdzJsufrAp_J3u&export=download">BETH</a>], que deriva su nombre de la forma en que captura la informacion real sobre cyberseguridad, que se basa en trampas digitales
denominadas como "honey pots", al cual se le hace un seguimiento extendido para ver su comportamiento. Este set de datos contiene Informacion
real y en constante alimentacion sobre accesos de diversos tipos sobre mas de 20 unidades de honeypots. Para efecto de eficiencia, hemos reducido el dataset original a una version segmentada para ser soportada
para efectos academicos, la misma que puede ser obtenida directo desde el siguiente [<a href="https://drive.google.com/uc?id=16G0p0_DYZXyteQRUrqc0IWn_MkPTyX8A&export=download">link</a>].

### Resumen de la problematica
La detección de amenazas desconocidas y la identificación proactiva de vulnerabilidades en entornos de ciberseguridad requieren de metodologías que superen las limitaciones de los datos etiquetados. Se establece que el reto es superar las "limitaciones de los datos etiquetados", una debilidad común en la ciberseguridad, justificando el uso del aprendizaje no supervisado.

### Objetivo general identificado
Este proyecto se enfoca en la identificación temprana y proactiva de posibles vulnerabilidades y patrones anómalos dentro del sector de la ciberseguridad haciendo uso de un dataset de BETH, a través de la implementación y el análisis avanzado de modelos de aprendizaje no supervisado como K-means, DBSCAN, PCA y t-SNE. 

### Objetivos especificos detectados

1.-Análisis Exploratorio: Analizar el dataset BETH e identificar las características de los accesos más comunes y sus métricas.

2.- Descubrimiento de Patrones: Identificar patrones relevantes de actividad sospechosa, como la frecuencia, el horario, tipo de ataques, etc.

3.- Modelado No Supervisado: Crear y entrenar modelos de Machine Learning no supervisado basados en el dataset para que puedan reconocer de forma exitosa los diferentes clusters de actividad y anomalías en la infraestructura de TI.
	
### Análisis Comparativo entre Modelos

#### ¿Qué tipo de perfiles se pueden identificar?
Entre los perfiles mas notables podemos identificar los siguientes:
Ataques cibernéticos realizados en horarios diurnos
Ataque por apertura de archivos
Ataque iniciados por procesos de sistema
Ataque por apertura de conexión

#### ¿Qué diferencias clave surgieron entre los modelos?
K-means, al utilizar como base la distancia euclidiana,  revelara clusters limpios y esféricos, podemos considerarlo como la base.
DBSCAN, en cambio revelara cluster arbitrarios etiquetando los outliers con -1, ya que se basa en densidad mas no en distancia, útil cuando no hay balance en las clases, pero agrega ruido.
PCA, siendo realmente mas alineado a una reducción de dimensionalidad, se refleja de forma global y preserva la varianza, no tiene captación para estructuras no lineales, mayormente usado para identificar direcciones mas no separar cluster
T-SNE, al igual que PCA sirve mas para reducir densidad, para data no lineal. Revela cluster bien definidos, clusters de puntos cercanos y compactos, ademas de la posibilidad de mostrar continuidades escondidas

#### ¿Qué limitaciones encontraron y cómo las abordarían?
Implementación K-means
se asume cluster esféricos y altamente definidos ===> limpieza de outliers antes de clusterizar
alta sensibilidad con los outliers ===> si la forma del cluster no es esferiza, implementar K-medoids o modelo gauseano de mezcla
Implementación DBSCAN
hiperparámetros difíciles de pulir ===> para el ajuste eps, se podría usar k-dist plot en conjunto con grid
baja eficiencia en datasets de grande dimension ===> para un manejo de densidades variadas, se usaría High density BSCAN
Implementación PCA
pierde patrones complejos al capturar solo relaciones lineales ===> realizar una selección de features  sumado a una normalización antes de usar el PCA
existe posibilidad de mezclar ruido y señal ===> mezclarlo con métodos no lineales para capturas mas finas
Implementación t-SNE
genera clusters atractivos que pueden ser falsos ===> usarlo solo de forma exploratoria
alta sensibilidad a hiperparámetros siendo inestable ===> Ajustar learning rate y validar con otros métodos

### Conclusiones y recomendaciones
- Con la capacidad de sectorizar los puntos de impacto, tal cual nos indica los clusters, podremos ser mas eficientes y estratégicos al momento de ejecutar un mecanismo de contingencia.

- Al momento de realizar las transformaciones necesarias, debemos tener en cuenta que usar datos lineales le darán mayor sentido a nuestra almacen de informacion y por consiguiente en todos los dashboards que usemos. (recordemos que en el caso de la base BETH no existen un numero natural de clusters por lo que la definición de K para K-means puede tornarse conflictiva)

- No existe un modelo de ML perfecto para todos los problemas cotidianos, un analisis y comparativa es necesario para tomar el mas eficiente y adecuado a nuestras necesidades, métodos de redimensionamiento como el PCA pueden ser difíciles de interpretar debido a su capacidad de mezclar señales con ruidos, no deberían ser definitivos en estructuras finales.

- El uso de t-sne, es correcto si solo haremos exploración visual de los resultados, ya que estos serán de carácter ficticio, y no deben usarse para segmentación.
