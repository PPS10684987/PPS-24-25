# Tarea 2 - Integración Continua con Jenkins y GitHub

## Descripción

En esta tarea hemos implementado un sistema de integración continua utilizando Jenkins para automatizar la ejecución de pruebas en un proyecto de Python. El código fuente y los tests están alojados en un repositorio de GitHub, y Jenkins está configurado para monitorizar dicho repositorio y ejecutar un pipeline cada vez que se produce un cambio.

## Pasos realizados

### 1. Clonación del repositorio

El primer paso fue clonar el repositorio de GitHub que contiene el proyecto. Dentro del repositorio se encuentra el código de una calculadora y un archivo de pruebas llamado `test_calculator.py`, además de un `Jenkinsfile` para definir el pipeline.

### 2. Configuración del proyecto en Jenkins

Creamos un nuevo proyecto tipo "Pipeline" en Jenkins. En la configuración del proyecto indicamos la URL del repositorio de GitHub y la ruta al `Jenkinsfile`, ubicado en:  
`RA5/RA5_1_JENKINS/Tarea_1_2_Github/codigo/jenkinsfile`.

### 3. Definición del Jenkinsfile

El `Jenkinsfile` está compuesto por tres etapas principales:

- **Checkout**: Jenkins clona el repositorio y accede al código fuente.
- **Test**: Se ejecuta el archivo de pruebas usando el comando `python3 -m unittest test_calculator.py`.
- **Post**: Se muestra un mensaje indicando si las pruebas han sido exitosas.

### 4. Ejecución automática del pipeline

Cada vez que se realiza un cambio en el repositorio, Jenkins detecta el evento y ejecuta automáticamente el pipeline configurado. Esto permite verificar de forma inmediata que el código sigue funcionando correctamente.

### 5. Validación de las pruebas

Cuando Jenkins ejecuta el pipeline, realiza las pruebas definidas en `test_calculator.py`. En nuestro caso, se han definido 4 pruebas unitarias para validar las operaciones básicas de la calculadora (suma, resta, multiplicación y división). Las pruebas se ejecutan correctamente, lo que indica que el proyecto es estable.

## Resultado

El resultado final es un sistema de integración continua funcional, que permite validar automáticamente los cambios en el código mediante la ejecución de pruebas unitarias. Esto mejora la calidad del software y facilita el mantenimiento del proyecto.

