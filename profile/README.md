# Organización del proyecto Veritas del ISA Group

## Descripción del proyecto

El proyecto Veritas es un trabajo del grupo ISA de la Universidad de Sevilla, cuyo objetivo es facilitar la labor de estudio de denominaciones de origen otorgadas en España a los productores de distintas materias agrícolas, mediante el uso de un dispositivo de espectrografía óptica.

## Seguimiento del Versionado

### Version 2

#### Arquitectura del proyecto

Durante la segunda versión del software se ha buscado otorgar una herramienta de control de las muestras tomadas, que facilite tanto la creación de nuevos modelos, el análisis de los datos obtenidos y el estudio de los modelos creados. Para ello la nueva arquitectura divide el proyecto en 3 componentes diferenciadas.

##### [VeritasDispositive](https://github.com/veritas-analytics/VeritasDispositive.git)

Este proyecto es un Wrapper de toda la funcionalidad que aporta el dispositivo de OceanOptics y a la vez es un manual de implementación de un dispositivo Veritas tal y como se detalla a continuación
