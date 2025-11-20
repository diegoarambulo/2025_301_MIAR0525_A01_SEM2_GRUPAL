### 2025_301_MIAR0525_A01_SEM4_GRUPAL
Repositorio grupal para los entregables de la actividad grupal de la semana 4 - Grupo 6

### Integrantes
* Diego Arambulo Vitores
* Jesus Zambrano Parrales
* Bryan Alvarado Quimiz

### Informacion sobre el dataset usado
Nuestro dataset fue obtenido del portal de bases abiertas y gratuitas [<a href="https://www.kaggle.com/">kaggle</a>], mas en especifico 
la denominada [<a href="ttps://drive.google.com/uc?id=1LGLypAMRHMw54oCdrSHUC6G80q2k71B_&export=download">BETH</a>], que deriva su nombre de la forma en que captura la informacion real sobre cyberseguridad, que se basa en trampas digitales
denominadas como "honey pots", al cual se le hace un seguimiento extendido para ver su comportamiento. Este set de datos contiene Informacion
real y en constante alimentacion sobre accesos de diversos tipos sobre mas de 20 unidades de honeypots. Para efecto de eficiencia, hemos reducido el dataset original a una version segmentada para ser soportada
para efectos academicos, la misma que puede ser obtenida directo desde el siguiente [<a href="https://drive.google.com/uc?id=16G0p0_DYZXyteQRUrqc0IWn_MkPTyX8A&export=download">link</a>].

### Problemática

La principal problemática es cómo asegurar que el modelo de Machine Learning supervisado Random Forest, desarrollado para la detección proactiva de patrones anómalos en el dataset BETH, sea un sistema de defensa robusto y confiable, capaz de superar sus sesgos inherentes y la vulnerabilidad a ataques de evasión, garantizando su efectividad operativa fuera del entorno de entrenamiento. 
La identificación de amenazas desconocidas y la detección proactiva de vulnerabilidades en ciberseguridad exigen metodologías que trasciendan las limitaciones inherentes a los datos etiquetados y los sesgos contextuales.
Esta dependencia de etiquetas preexistentes representa una debilidad estructural en los sistemas de defensa tradicionales, lo que justifica la adopción de enfoques de aprendizaje supervisado como Random Forest.
Dentro de este contexto, la principal problemática es identificar y mitigar los sesgos críticos en el dataset de entrenamiento BETH para asegurar que el modelo de Machine Learning no esté determinado por variables sesgadas, transformándolo de una "caja negra" a un sistema interpretable y operable. Dada la complejidad no lineal de Random Forest, se requiere la implementación de SHAP para la validación global del sesgo mitigado y LIME para la auditoría forense local.

### Objetivo general identificado

Este proyecto se enfoca en la identificación temprana y proactiva de posibles vulnerabilidades y patrones anómalos dentro del sector de la ciberseguridad haciendo uso de un dataset de BETH, a través de la implementación y el análisis avanzado del modelo de aprendizaje supervisado como Random Forest, así como el uso de técnicas de explicabilidad XAI, SHAP (Shapley Additive Explanations) como técnica principal de explicabilidad global debido a su consistencia basada en la teoría de juegos y LIME (Local Interpretable Model-agnostic Explanations) para la auditoría forense a nivel local.

### Objetivos especificos detectados

1.-Análisis Exploratorio: Analizar el dataset BETH e identificar las características de los accesos más comunes y sus métricas.

2.- Descubrimiento de Patrones: Identificar patrones relevantes de actividad sospechosa, como la frecuencia, el horario, tipo de ataques, etc.

3.- Modelado Supervisado: Implementar y entrenar el modelo de Machine Learning supervisado basados en el dataset para que puedan reconocer de forma exitosa los diferentes actividades y anomalías en la infraestructura de TI.
	
### Análisis Comparativo entre Modelos

#### ¿Qué tipo de perfiles se pueden identificar?
Entre los perfiles mas notables podemos identificar los siguientes:
Ataques cibernéticos realizados en horarios diurnos
Ataque por apertura de archivos
Ataque iniciados por procesos de sistema
Ataque por apertura de conexión

#### ¿Que resultados se obtuvieron al analizar si existia sesgo en el dataset?
Dentro de los analisis, se pudo evidenciar que el dataset mostraba tendencia a overfiting en ciertos cumulos de informacion como los son: el processName, y el userId, en el siguiente grafico podremos observar un sesgo detectado por proceso
como evento benigno siempre, o cual claramente va a entrenar de forma errada el modelo escogido, en este caso un random forest:
![Texto alternativo](images/analisisSesgoXproceso.png)


#### ¿Qué resultados se obtuvieron al aplicar los metodos de fairness SHAP y LIME?
Dentro del metodo shap, podemos entender de mejor forma porque el modelo actua o predice los valores y tendencias de una forma u otra, y esto lo aplica basandose en el peso de relevancia que tiene una variable con respecto a una tendencia encontrada
esto lo podremos apreciar de mejor forma en el siquiente diagrama donde, se no indica que la variable processName, es la mas relevante al momento de detectar una anomalia o evento en el dataset.
![Texto alternativo](images/TopIndicadoresAtaqueXproceso.png)


De la misma forma, LIME, pretende explicar como las perturbaciones hacia un unico registro tomado de la muestra, cambia sus resultados hacia el test realizado a el, esto no permite encontrar como los cambios en las entradas del modelo se traducen
en cambios sutiles o abruptos como resultado del estrato general de informacion. A continuacion podremos observar como el analisis LIME, detecta que processName entra dentro de las reglas de decision por ser altamente relevante a diferencia del 
resto como eventName o args.
![Texto alternativo](images/explicabilidadLime.png)

### Conclusiones y recomendaciones
- El proceso de desarrollo de la solución de Detección de Anomalías en Ciberseguridad es ejemplar y metodológicamente robusto. Se seleccionó y validó de forma estratégica el modelo Random Forest como un balance óptimo entre capacidad predictiva frente a la no linealidad de las amenazas e interpretabilidad intrínseca.

- La decisión crítica de implementar el Feature Blinding (eliminación de userId y processId) para forzar la generalización de patrones de comportamiento en lugar de memorizar identidades fue fundamental para mitigar el "Data Leakage" y el sesgo de contexto, lo que transformó el modelo de un "perfilador de usuarios" a un verdadero "detector de anomalías" con portabilidad garantizada a diferentes entornos.

- La integración de las técnicas de explicabilidad SHAP visión global y validación del sesgo mitigado y LIME visión local y soporte forense para el SOC es la principal fortaleza del proyecto. Esta dualidad de herramientas demostró ser indispensable, no solo como un requisito académico de transparencia, sino como una herramienta de robustecimiento de seguridad al exponer fallos de diseño como la dependencia inicial del userId y mitigar riesgos éticos y operativos como el sesgo contra herramientas administrativas. Las visualizaciones basadas en SHAP y LIME actúan como la prueba irrefutable de la validez y coherencia del modelo.

<img width="1040" height="407" alt="Recomendaciones" src="https://github.com/user-attachments/assets/bde27fcf-e174-410a-8a45-730e3e77505d" />



