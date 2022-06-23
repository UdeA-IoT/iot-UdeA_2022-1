# Ejemplo de una implementacion por pasos

El objetivo de esta sesión es explicar paso a paso como se construye una aplicación sencilla que conecta la placa de desarrollo con una aplicación a la medida que corre desde un PC o una tarjeta RPi. Para este caso, el desarrollo se hizo en un PC.

## Enunciado de la aplicación

Desarrolle una aplicación que permita encender y apagar un Led para el siguiente hardware:

![hw](hardware_bb.png)

La aplicación se conectara mediante el serial enviando dos comandos basicos para modificar el estado del led:
* **H**: Comando empleado para encender el Led.
* **L**: Comando empleado para apagar el Led.

El resultado final (si todo sale bien) de la aplicación de control es el siguiente:

![interfaz](ui_python.png)

## Pasos seguidos

El proceso de construcción de la aplicación se lleva a cabo mediante los siguientes pasos:
1. Desarrollo de la aplicación en la herramienta ([link](paso1/README.md)).

   ![paso1](paso1/serial_output.png)
2. Desarrollo de la aplicación en python (Texto) ([link](paso2/README.md))

   ![paso2](paso2/app_python.png)
3. Desarrollo de la aplicación en python (Interfaz grafica) ([link](paso2/README.md))
    
    ![paso3](paso3/ui_python.png)


## REferencias

* http://downonearthtutorials.blogspot.com/2014/09/real-time-serial-data-monitor-with.html
