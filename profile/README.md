# Organización del proyecto Veritas del ISA Group

## Descripción del proyecto

El proyecto Veritas es un trabajo del grupo ISA de la Universidad de Sevilla, cuyo objetivo es facilitar la labor de estudio de denominaciones de origen otorgadas en España a los productores de distintas materias agrícolas, mediante el uso de un dispositivo de espectrografía óptica.

## Seguimiento del Versionado

### Version 2

#### Arquitectura del proyecto

Durante la segunda versión del software se ha buscado otorgar una herramienta de control de las muestras tomadas, que facilite tanto la creación de nuevos modelos, el análisis de los datos obtenidos y el estudio de los modelos creados. Para ello la nueva arquitectura divide el proyecto en 3 componentes diferenciadas. Se procede a resumir los mismos en adelante.

##### Veritas Dispositive [(link al repositorio)](https://github.com/veritas-analytics/VeritasDispositive)

Este proyecto es una API Python que funciona como un wrapper de toda la funcionalidad que aporta el dispositivo de OceanOptics. Hay que tener en cuenta que el paquete de OceanOptics que se aporta en el proyecto está diseñado para un sistema con arquitectura aarch64, la instalación de estos paquetes así como la configuración de los mismos, tratados en este proyecto, pueden no funcionar en otros equipos. El Wrapper en sí al ser diseñado en Python debería funcionar en otros equipos aunque las instalaciones y comandos podrían depender del sistema operativo. Al menos en esta versión se recomienda que la instalación y el uso se haga en una Raspberry que es el dispositivo en el que se ha asegurado el funcionamiento.

Este proyecto sirve una API directamente en localhost que maneja la interacción con el dispositivo OceanOptics. Para más referencias sobre esta API y sobre el proyecto visitese el repositorio del mismo.

#### Veritas Sampling [(link al repositorio)](https://github.com/veritas-analytics/VeritasSampling)

Este proyecto es una aplicación full stack diseñada en Nextjs para ser servida en un dispositivo Veritas y que se puedan tomar y guardar muestras El lado servidor de la aplicación se encarga de la comunicación con la API de [(Veritas Dispositive)](https://github.com/veritas-analytics/VeritasDispositive) y con la base de datos del [(Veritas Management)](https://github.com/veritas-analytics/VeritasManagement), por otro lado el frontend es un diseño sencillo que permite realizar las operaciones de tomar muestras y etiquetar. 
Para más información sobre en que consiste un dispositivo Veritas se puede consultar [el siguiente documento](https://github.com/veritas-analytics/VeritasSampling.git). En resumen son tres dispositivos hardware funcionando dentro de una carcasa que los protege. Los dispotivos en cuestión son:

- Una Raspberry
- Una pantalla táctil
- Un dispositivo OceanOptics

El proyecto incluye también un manual de instalación y configuración de forma que se pueda poner en marcha un nuevo dispositivo Veritas correctamente configurado, para la toma de muestras. 

La aplicación es una simplificación que permite crear sesiones de muestreo y de testeo de modelos, ofreciendo una conexión por detrás en forma de caja negra con otro de los componentes del proyecto para permitir guardar y etiquetar muestras en una base de datos persistente. 

#### Veritas Management [(link al repositorio)](https://github.com/veritas-analytics/VeritasManagement)

Este último proyecto es el componente principal de la aplicación de gestión de muestras. Es una segunda aplicación Full Stack desarrollada en NextJs y desplegada en Vercel. Es el componente que permite al usuario gestionar realmente sus muestras, categorías de etiquetado, modelos, etc...
En el lado servidor se ofrecen las funcionalidades necesarias y se sirven dos APIs:

- Una API CRUD para el manejo de muestras, etiquetas y modelos desde el propio frontend
- Una API con CORS Policy que permite realizar algunas funciones CRUD sobre las etiquetas y las muestras, pensada para ser consumida por un dispositivo Veritas. Esta API permite leer las etiquetas definidas y crear nuevas muestras con un etiquetado concreto.

En el lado frontend es una aplicación con bastante rutas para permitir un cómodo manejo de toda la funcionalidad.

<br>

Para todos estos proyectos, este documento sirve solo como resumen y no busca ser una documentación extensa que se puede encontrar en los enlaces ofrecidos para el caso.

<br> 
<br>

### Version 1

La primera versión del software busca dar un sistema integral para un dispositivo Veritas con capacidad para medir muestras y predecir su denominación de origen. Su campo de acción son solo un subconjunto de denominaciones de origen de vinagre y cuenta con un modelo realizado para tal fin que no es modificable. Este sistema no busca guardar las muestras tomadas ni ser de más utilidad que la de disponer de un dispositivo sin conexión que cualquiera sin conocimientos sobre su implementación pueda usar para hacer pruebas relativamente fiables sobre un vinagre propio.

Esta versión sirve como apertura del proyecto, pero se cerró con evidentes carencias sobre todo en la fiabilidad del sistema de predicciones y con pocas funcionalidades implementadas.
