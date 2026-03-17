1. Estructura del Repositorio 

El proyecto está organizado de la siguiente manera: 

├── data/                         # Archivos CSV (Dataset de 150k filas)
├── notebooks/                    # Jupyter Notebook (.ipynb) con el análisis
├── docker-compose.yml            # Configuración de la infraestructura Spark
├── Dockerfile                    # Personalización de la imagen de Jupyter/Spark
└── README.md                     # Documentación general y pasos de ejecución

2. Contexto y Descripción

¿De qué trata la base de datos?: Trabajamos con un dataset masivo de 150,000 registros que recopila información vital sobre empleados del sector tecnológico. Incluye variables demográficas (edad, género), laborales (rol, horas extra, modalidad de trabajo) y métricas psicológicas validadas (niveles de ansiedad, depresión y burnout).

El Problema: En la industria del software, el "Burnout" o síndrome del trabajador desgastado es una realidad que afecta la productividad y la vida personal. Queremos entender si este agotamiento es culpa del exceso de código (horas extra), de la falta de interacción (trabajo remoto) o si ciertos roles como el Backend sufren más que otros.

¿Qué esperábamos encontrar? (Hipótesis Iniciales):
H1: Los empleados en modalidad presencial tienen mayor satisfacción por el contacto social.
H2: A mayor cantidad de horas extra, el nivel de burnout sube de forma lineal.
H3: Los roles con mayor responsabilidad técnica (DevOps/Backend) presentan niveles de ansiedad más altos.


3. Objetivos de la Consultoría
El objetivo principal es procesar este volumen de datos usando PySpark para:

Identificar patrones: Ver qué grupos de empleados están en mayor riesgo (Outliers).

Validar realidades: Confirmar si el género o el rol influyen realmente en el estrés.

Sugerir mejoras: Basados en los datos, proponer cuál es la mejor modalidad de trabajo (Híbrido vs Remoto vs Onsite) para mantener al equipo sano.


4. Aclaraciónes del proceso. 

¿Qué es version y para qué sirve?: Básicamente indica la versión de la API de Docker Compose que vamos a usar (en este caso puse la 3.8). Es super importante porque define que funciones y que sintaxis son compatibles con el motor de Docker que tenga instalado la profe en su maquina.


¿Qué hace la sección services?: Es donde definimos los contenedores que vamos a levantar para nuestra infraestrucura. En este proyecto, el servicio principal se llama pyspark-jupyter, que es el que levanta todo nuestro entorno de trabajo con las librerias.


¿De dónde viene la imagen jupyter/pyspark-notebook?: Esta imagen se descarga directamente de Docker Hub, que es como el registro oficial de imagenes de Docker. Es una imagen mantenida por la comunidad de Jupyter y ya viene con Spark, Hadoop y Python listos para usar sin tener que instalar nada raro.


¿Qué significa el mapeo de puertos 8888:8888?: Significa que vamos a conectar el puerto 8888 de mi compu con el puerto 8888 que esta adentro del contenedor. Esto es lo que permite que, cuando yo escriba localhost:8888 en el chrome, pueda ver la interfaz de Jupyter que esta corriendo en el Docker.


¿Qué hacen los volumes y por qué son importantes?: Los volumenes lo que hacen es "amarrar" carpetas de mi PC (data y notebooks) con las carpetas que estan dentro del contenedor. Son vitales porque los contenedores se borran al apagarlos; si no tubieramos volumenes, todo el analisis que haga en el notebook se perdería para siempre.


¿Para qué sirve la variable de entorno JUPYTER_ENABLE_LAB?: Al ponerla en yes, le estamos diciendo al contenedor que queremos entrar por JupyterLab en lugar de la vista de notebooks viejita. Es mucho mejor para manejar barios archivos al tiempo y tener la terminal a la mano.