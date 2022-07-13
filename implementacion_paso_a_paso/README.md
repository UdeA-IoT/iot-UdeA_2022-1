# Ejemplo de una implementacion IoT muy sencilla por pasos

El objetivo de esta sesión es explicar paso a paso como se construye una aplicación sencilla que conecta la placa de desarrollo con una aplicación a la medida que corre desde un PC o una tarjeta RPi. Para este caso, el desarrollo se hizo en un PC.

## Enunciado de la aplicación

Desarrolle una aplicación que permita encender y apagar un Led para el siguiente hardware:

![hw](hardware_bb.png)

La aplicación se conectara mediante el serial enviando dos comandos basicos para modificar el estado del led:
* **H**: Comando empleado para encender el Led.
* **L**: Comando empleado para apagar el Led.

El resultado final (si todo sale bien) de la aplicación de control es el siguiente:

![interfaz](ui_python.png)

## Pasos seguidos - Parte 1

El proceso de construcción de la aplicación se lleva a cabo mediante los siguientes pasos:
1. Desarrollo de la aplicación en la herramienta ([link](paso1/README.md)).

   ![paso1](paso1/serial_output.png)
2. Desarrollo de la aplicación en python (Texto) ([link](paso2/README.md))

   ![paso2](paso2/app_python.png)
3. Desarrollo de la aplicación en python (Interfaz grafica) ([link](paso3/README.md))
    
    ![paso3](paso3/ui_python.png)

## Pasos seguidos - Parte 2

Como se pudo evidenciar, ya fue posible la interación de un dispositivo sencillo implementado usando el ESP32 y una aplicación (inicialmente de texto y despues grafica) en python que se ejecuta en un PC o RPi mediante comunicación serial. 

En esta parte nos encargaremos adaptar el problema anterior de modo que la comunicación, sea en este caso, sea mediante el el protocolo MQTT. 

Antes de seguir, verifique que tiene instaladas las siguientes herramientas en su maquina:
1. MQTT Explorer ([link](http://mqtt-explorer.com/)).
2. Mosquito ([link](https://mosquitto.org/)). Para mas información ver [Mosquitto MQTT Broker](http://www.steves-internet-guide.com/mosquitto-broker/).

El modo de trabajo sera similar al anterior, se iniciara partiendo del caso mas basico que es la implementación del firmware que se encargara del control del hardware (**Cosa**); luego, se realizará una aplicación de escritorio sencilla (implementacion en consola) y finalmente, se implementará una aplicación de escritorio igualmente sencilla, pero esta sera grafica. Respecto a la implementación inicial (Parte 1 - sin IoT), esta aplicación ya implementará, aunque de manera muy sencilla el concepto de IoT al hacer uso del protocolo MQTT el cual, hace posible la comunicación entre las cosas.

A continuación se detallan los pasos:
1. Implemente el programa (firmware) del microcontrolador ([link](mqtt_paso1/))




## REferencias

* http://downonearthtutorials.blogspot.com/2014/09/real-time-serial-data-monitor-with.html
* https://learn.sparkfun.com/tutorials/introduction-to-mqtt/introduction
* https://learn.sparkfun.com/tutorials/using-home-assistant-to-expand-your-home-automations/example-1-mqtt--esp32
* https://randomnerdtutorials.com/esp32-mqtt-publish-subscribe-arduino-ide/
