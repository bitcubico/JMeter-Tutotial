# JMeter-Tutorial
Tutorial para usar JMeter

## Módulos

 1. Introducción a las **Pruebas de Performance**
    - Sobre el curso
    - Pruebas de Performance
    - Herramientas para Pruebas de Performance
    - Introducción a Apache JMeter
    - Guía de instalación
    - Elementos principales de JMeter
    - Herramientas de soporte
 2. Creación de **SCRIPTS** con ejemplos reales
    - Resumen de protocolos HTTP (Cliente - Servidor) ¿Qué son y cómo se usan?
    - Grabación de script (HTTP proxy record - Recursos embebidos)
    - Cookies - Cache - HTTP Request Default
    - Correlaciones usando Expresiones Regulares
    - Debug Postprocesor
    - Parametrización (CSV Data Set)
    - Assertion Timer Controller
    - Grupo de hilos
    - Listener
3. Creando **SCRIPTS COMPLEJOS**
    - Plan de pruebas para JDBC
    - Plan de pruebas para Webservices
    - Plan de pruebas para REST API
    - Plan de pruebas para Aplicaciones Móviles
    - Monitorización
    - Integración con SELENIUM
    - JMeter en modo Non-GUI
    - Uso de JMeter en la nube
5. Documentando las Pruebas de Performance
    - Plan de pruebas
    - Informe de resultados
    - Casos de pruebas (guiones de pruebas)
    - Buenas prácticas
    - Ejercicios
    
##  1. Introducción a las Pruebas de Performance

### Sobre el curso

### Pruebas de Performance

Las pruebas de performace es una investigación técnica para determinar o validar la **velocidad, escalabilidad y/o estabilidad** de un sistema bajo condiciones específicas que permitan analizar su desempeño en situación de carga.

Técnicamente las pruebas de performance están categorizadas como una característica de calidad de la **norma ISO 25010**. Dentro de esta, podemos identificar 3 características de gran relevancia:

 1. **Comportamiento del tiempo:** Tiempos de respuesta de la aplicación
 2. **Utilización de los recursos**: Tiene que ver con el comportamiento de los recursos del servidor y como se ven afectados cuando la aplicación está sometida a las pruebas de performance.
 3. **Capacidad**: Capacidad del sistema para soportar cierta cantidad de usuarios por tiempos prolongados

#### Tipos de Pruebas Fundamentales
Existen muchos tipos de pruebas que se pueden aplicar. Dentro de estas existen algunas que son fundamentales en un proceso de pruebas:

 - **Pruebas de Carga**: Nos permite determinar la capacidad de procesos o solicitudes que puede soportar un sistema en un intervalo de tiempo.
 ![Medición de la capacidad de carga de un puente](https://lh3.googleusercontent.com/BmxGBbj9ytNfLdBXPZTqhe760lAMKY66Uzgtj_PDrrDbcVDZluz0nX1pxEbVosaUTtYKpPJ2r1pZSQ "Prueba de carga")
 - **Pruebas de Estrés**: Estas se enfocan es sobrepasar la capacidad determinada en la prueba anterior.
 ![Estresando un puente recargandolo para identificar su punto de quiebre](https://lh3.googleusercontent.com/jrYrkFKdjFfB9WFjuXYlETe8XuETM-C0eVg3VgUJdUyMPsIvkeoCBMWMkIT9YsRq2_1fj86oLMfuGg "Prueba de estrés")
 - **Pruebas de Endurance o resistencia**:  Estas se usan para identificar cómo se comporta el sistema en intervalos de tiempo donde se ha detectado que hay mayor concurrencia o mayor exigencia al mismo.
 ![Medición del comportamiento de un puente en los momentos donde hay más tráfico](https://lh3.googleusercontent.com/UgoPgk3yEtG0t3Uuxai9DtZsltghM8vOw86vrfBa15KGq5m74AJ7qGazFAIiVJQzH2bCubFXdFbpNg "Prueba de resistencia")
 - **Pruebas de Escalabilidad**: Se usan para identificar la estructura requerida para que el sistema se conserve estable.
 ![Medición de la capacidad de carga de un puente reforzando sus cimientos](https://lh3.googleusercontent.com/Mh8Tzrh44RTPxHCezDKTf8ColGVAXZPZMbZuZHrr5JqZLcE5C1C-pDTL1m6iTLS4Ddjbz89zI13fHg "Prueba de escalabilidad")

###  Introducción a Apache JMeter

JMeter es una herramienta ***gratuita***, es de fácil uso, cuenta con una interfaz de usuario amigable, existe una comunidad en crecimiento que ayuda a potenciar la herramienta, entre otras características.

### Cómo funciona JMeter
![enter image description here](https://lh3.googleusercontent.com/OWjs8zfcgNAdzUTFHoc83eiRAcb6-sEdYRCxTt5D_lEilHLz_75BGNp-riTKzdQ0koYZ3C5il7mqhg "Gráfico del funcionamiento de JMeter")

JMeter se ejecuta desde un **cliente** y su labor consiste en enviar peticiones **request** a un **servidor de aplicaciones** y evaluar las respuestas del servidor para así recopilar información del funcionamiento de la aplicación con cada uno de los **request**. Esta característica de JMeter, nos permite evaluar el comportamiento de una aplicación simulando uno o muchos usuarios de forma concurrente.

### Guía de Instalación

Es recomendable descargar JMeter desde la página oficial [jmeter.apache.org](https://jmeter.apache.org/) en la sección de [descargas](https://jmeter.apache.org/download_jmeter.cgi). Un requisito principal para que JMeter se ejecute correctamente es tener instalada la ***máquina virtual*** o el [JDK](https://www.oracle.com/technetwork/java/javase/downloads/index.html) de Java. Después de descargar los binarios de JMeter, la forma de iniciarlo es ejecutando el archivo ***ApacheJMeter.jar*** ubicado en el directorio ***bin***.

### Elementos principales de JMeter

 - **Plan de pruebas**: Es el objeto que representa una prueba
 - **Grupos de hilos**: Son elementos que definen el número de hilos de ejecución que definirán el número de usuarios a simular
 - **Elementos de configuración**: Son los tipos de elementos destinados a labores de configuración, en muchos casos, valores por defecto como cookies, tokens, cache, etc.
 - **Temporizadores**: Son los elementos destinados a controlar los espacios relativos de tiempo entre los diferentes hilos, es decir, los tiempos de espera entre cada acción realizada por un usuario.
 - **Receptores**: Son los elementos que nos permiten tener acceso a los datos recopilados por las pruebas. Estos pueden ser desde datos estadísticos hasta gráficas de evolución.
 - **Aserciones**: Son un conjunto de elementos encargadde la verificación de los datos provenientes de los servidores. Con estos podemos identificar cuando una ejecución tuvo o no problemas.
 - **Postprocesadores**: Estos ejecununa acción después de la ejección de un ***muestreados los binarios de JMeter, se debe ir al directorio ***bin*** y ejecutar el archivo llamado ***ApacheJMeter.jar***.or**. Es decir, toma datos dloresultados y los lmacena en variables, que podrán ser usadas por otras pruebas, o verifica su contenido para validar que todo esté correcto.
 - **Controladores lógicos**: Son los elementos lógicos que nos permiten controlar el comportamiento de las pruebas. Esto se refiere a los elementos de un lenguaje de programación que nos permiten ejecutar fracciones de código de forma repetitiva o evaluar cuándo ingresar o no a realizar una prueba (for, while, if, do, etc) y así darle sentido a la ejecución de un script.

## 2. Creación de **SCRIPTS** con ejemplos reales

En esta sección realizaremos paso a paso grabaciones y ejecuciones de scripts junto con el análisis de los datos arrojados por los mismos.

### Grabación de script (HTTP proxy record - Recursos embebidos)

#### Pasos del Script 1
Plan de pruebas: El sitio [blazedemo.com](http://blazedemo.com/) requiere garantizar las siguientes características y funcionalidades:

##### Pruebas de carga


##### Funcionalidades
|Id|Descripción|Url|
|--|--|--|
| 1 | El home debe  |  |


1. **Agregamos un Test Script Recorder o Servidor Proxy HTTP**: Su función es escuchar por un puerto específico todo el tráfico que pase por ahí.
2. **Agregamos el grupo de hilos**: Este grupo de hilos guardará todos los datos de los request que se envíen por JMeter en las pruebas.
3. **Configurar el proxy del navegador**: Se debe configurar el navegador para que establezca la comunicación por medio del proxy y el puerto que usa el Test Script Recorder
4. **Aceptamos el certificado que genera JMeter**: este certificado es generado automáticamente por JMeter
5. **Grabamos** todas las funcionalidades de la página que nos interesa probar
6. **Agregamos los listener** que nos ayudarán a interpretar lo que está sucediendo:
         - ***View Results Tree***: Este nos muestra el estado de la petición, lo que se envió y lo que se recibió del servidor
         - ***Gráfico o Aggregate Graph***: Este nos muestra los tiempos de respuesta del servidor durante la prueba. Con este determinamos cómo se comporta el servidor durante el tiempo que ejecutamos la prueba.
         - ***Active Threads Over Time***: Este nos muestra la cantidad de usuarios activos a lo largo de la prueba en cada intervalo de tiempo.
         - ***View Results in Table***: Este nos muestra el estado de la petición, tiempos de respuesta, peso de estas.
         - ***Transactions per Second***: Este nos muestra las cantidad de transacciones por segundo que se ejecutan y a que control se le está haciendo.
7. **Agregar Temporizadores**: Estos nos permiten simular las interacciones de los usuarios con la aplicación lo más cercano posible a los tiempos en que estas se dan. Un usuario por lo general no ejecuta las acciones como un robot, que es el caso de JMeter, las ejecuta en tiempos irregulares y dependiendo de muchos factores y las aplicaciones no responden siempre en tiempos fijos, estos también dependen de muchas variables. 
Existen varios tipos de temporizadores, estudiemos los que más se usan:
         - ***Temporizador CONSTANTE***: Este se usa para agregar un tiempo de espera entre peticiones. Se puede configurar a nivel general o para una petición en particular. Generalmente este temporizador se usa cuando se desea dar una espera a la aplicación para que cargue todos sus componentes.
Estos tiempos deben tenerse en cuenta al finalizar las pruebas ya que altera el tiempo total de la ejecución.
         - ***Temporizador ALEATORIO UNIFORME***:  Este pausa las peticiones en cada hilo durante un tiempo aleatorio. Este puede acercarnos más a lo que son las interacciones de los usuarios con las aplicaciones ya que las interacciones no se dan en tiempos constantes.
Estos tiempos deben tenerse en cuenta al finalizar las pruebas ya que altera el tiempo total de la ejecución.
8. **Agregamos las ASERCIONES**: Estas son ***validaciones*** que nos permiten evaluar si la respuesta del servidor a una petición se puede considerar como correcta o no. Existen muchas aserciones y entre esas las más usadas son:
          - ***Aserciones de RESPUESTA***: Estas nos permiten buscar la respuesta del servidor identificadores que me permitan validar si la respuesta es correcta o no.
          - ***Aserciones de DURACIÓN***: Estas nos permiten identificar las peticiones que duran más del tiempo del especificado en esta.
9. **Agregamos PARAMETRIZACIONES**: Las parametrizaciones nos permiten enviar datos dinámicos en cada ejecución del test.
10. **Configuramos los datos de CARGA**: Esta configuración se realiza en el grupo de hilos del escenario a evaluar y se configuran los siguientes elementos:
           - ***Número de hilos (usuarios)***: En esta especificamos el número de usuarios que van a interactuar con la aplicación en el intervalo de tiempo especificado. 
           - ***Ramp-Up Period***: En esta especificamos el tiempo que tienen los usuarios indicados para realizar todo el test.
           - ***Loop Count***: Este me permite especificar cuantas veces se debe repetir el ciclo o si va a ejecutarse por siempre.

Con esto ya definido, podemos entonces parametrizar la prueba, usando datos dinámicos definidos por nosotros, de modo que la prueba se asemeje los más posible a la realidad.

Programamos la prueba para que se ejecute desde consola:

    jmeter -E https -n -t SATAdmin.jmx -l log.txt
