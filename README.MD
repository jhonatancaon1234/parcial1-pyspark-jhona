¿Qué es version y para qué sirve?: Básicamente indica la versión de la API de Docker Compose que vamos a usar (en este caso puse la 3.8). Es super importante porque define que funciones y que sintaxis son compatibles con el motor de Docker que tenga instalado la profe en su maquina.


¿Qué hace la sección services?: Es donde definimos los contenedores que vamos a levantar para nuestra infraestrucura. En este proyecto, el servicio principal se llama pyspark-jupyter, que es el que levanta todo nuestro entorno de trabajo con las librerias.


¿De dónde viene la imagen jupyter/pyspark-notebook?: Esta imagen se descarga directamente de Docker Hub, que es como el registro oficial de imagenes de Docker. Es una imagen mantenida por la comunidad de Jupyter y ya viene con Spark, Hadoop y Python listos para usar sin tener que instalar nada raro.


¿Qué significa el mapeo de puertos 8888:8888?: Significa que vamos a conectar el puerto 8888 de mi compu con el puerto 8888 que esta adentro del contenedor. Esto es lo que permite que, cuando yo escriba localhost:8888 en el chrome, pueda ver la interfaz de Jupyter que esta corriendo en el Docker.


¿Qué hacen los volumes y por qué son importantes?: Los volumenes lo que hacen es "amarrar" carpetas de mi PC (data y notebooks) con las carpetas que estan dentro del contenedor. Son vitales porque los contenedores se borran al apagarlos; si no tubieramos volumenes, todo el analisis que haga en el notebook se perdería para siempre.


¿Para qué sirve la variable de entorno JUPYTER_ENABLE_LAB?: Al ponerla en yes, le estamos diciendo al contenedor que queremos entrar por JupyterLab en lugar de la vista de notebooks viejita. Es mucho mejor para manejar barios archivos al tiempo y tener la terminal a la mano.