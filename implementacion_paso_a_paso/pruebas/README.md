# Manejando el arduino desde un API


![](https://files.realpython.com/media/mvc_diagram_with_routes.e12c5b982ac8.png)

## Parte 1 - Creacion del API usando flask

### Codigo:

```python
from flask import Flask, flash, redirect, render_template, request, session, abort, jsonify

app = Flask(__name__)

# Resourse
lights = [
    {"id": "1", "name": "Lampara 1", "status": 0},
    {"id": "2", "name": "Lampara 2", "status": 0},
    {"id": "3", "name": "Lampara 3", "status": 0},
]

def _find_light_index(id):
    index = None    
    for i in range(len(lights)):                
        if lights[i]["id"] == id:
            index = i
            break            
    return index
        
@app.route("/", methods=["GET"])
def index():
    return "Test", 200

# /lights
@app.route("/lights",  methods=["GET"])
def get_lights():
    return jsonify(lights), 200

# /lights/info/<light_id>
@app.route("/lights/info/<string:light_id>/", methods=["GET"])
def get_light_info(light_id):   
    info = "Light not Found..."
    index = _find_light_index(light_id)             
    if index == None:
        return info, 404
    else:        
        return jsonify(lights[index]), 200
   
# /lights/status/<light_id>
@app.route("/lights/status/<string:light_id>", methods=["GET"])
def get_light_status(light_id):    
    info = "Light not Found..."
    index = _find_light_index(light_id)             
    if index == None:
        return info, 404
    else:        
        return jsonify(lights[index]["status"]), 200

@app.route("/lights", methods=["POST"])
def add_light():
    if request.is_json:
        light = request.get_json()
        index = _find_light_index(light["id"])
        if index != None:
            return "Invalid Operation", 400
        else:
            lights.append(light)
            return light, 201
    else:
        return {"error": "Request must be JSON"}, 415


# /lights/<light_id>/<status> 
@app.route("/lights/<string:light_id>/<int:status>", methods=["GET"])
def light_change_status(light_id, status):    
    info = "Light not Found..."
    index = _find_light_index(light_id)             
    if index == None:
        return info
    else:      
        lights[index]["status"] = status
        return jsonify(lights[index]["status"])


if __name__ == "__main__":
    app.run()
```

### Prueba del API con curl

TODO (Poner comandos con curl)

### Prueba del API con Postman

TODO (Poner figuras)


TODO - Fecha de mañana
1. Ver: https://www.giacomodebidda.com/posts/mvc-pattern-in-python-introduction-and-basicmodel/
2. https://www.pythontutorial.net/tkinter/tkinter-mvc/
3. https://realpython.com/the-model-view-controller-mvc-paradigm-summarized-with-legos/
4. https://www.pythontutorial.net/tkinter/tkinter-mvc/
5. https://learn.sparkfun.com/tutorials/using-flask-to-send-data-to-a-raspberry-pi/all#hardware-hookup
6. http://repository.unipiloto.edu.co/bitstream/handle/20.500.12277/6046/Anexo%202%20-%20maual%20t%C3%A9cnico.pdf?sequence=3&isAllowed=y
7. http://fab.cba.mit.edu/classes/863.14/people/juliana_nazare/project12.html
8. https://github.com/AashiDutt/Arduino_Python_Flask_Dashboard
9. https://www.instructables.com/Controlling-Arduino-with-python-based-web-API-No-p/
10. https://create.arduino.cc/projecthub/albyciancio/desk-weatherstation-with-esp8266-and-python-flask-58247b?ref=part&ref_id=10308&offset=20
11. https://github.com/eacandelas/arduFlask
12. https://getbootstrap.com/docs/4.0/components/buttons/
13. https://books.google.com.co/books?id=XINcDgAAQBAJ&pg=PA470&lpg=PA470&dq=bootstrap+button+arduino&source=bl&ots=GA27Z_Lt43&sig=ACfU3U1T9J7kXBHD2uWRjqTfhVVDYdBANQ&hl=es&sa=X&ved=2ahUKEwi5k6nk2OP4AhVHZTABHaJ5APkQ6AF6BAgaEAM#v=onepage&q=bootstrap%20button%20arduino&f=false
14. https://startingelectronics.org/articles/arduino/switch-and-web-page-button-LED-control/
15. https://forum.arduino.cc/t/html-arduino-coding-for-single-on-off-button/245175
16. https://randomnerdtutorials.com/esp32-web-server-arduino-ide/
17. https://books.google.com.co/books?id=XINcDgAAQBAJ&pg=PA470&lpg=PA470&dq=bootstrap+button+arduino&source=bl&ots=GA27Z_Lt43&sig=ACfU3U1T9J7kXBHD2uWRjqTfhVVDYdBANQ&hl=es&sa=X&ved=2ahUKEwi5k6nk2OP4AhVHZTABHaJ5APkQ6AF6BAgaEAM#v=onepage&q=bootstrap%20button%20arduino&f=false
18. https://randomnerdtutorials.com/esp32-esp8266-input-data-html-form/
19. https://involt.github.io/
20. http://involt.github.io/examples/blink.html
21. https://create.arduino.cc/projecthub/ErniW/easy-interaction-prototyping-with-html-arduino-and-involt-bdf25c
22. https://www.instructables.com/How-to-communicate-with-Arduino-using-HTML-Chrome/   (Este es el que necesito)
23. https://docs.microsoft.com/es-es/learn/paths/web-development-101/
24. https://github.com/microsoft/Web-Dev-For-Beginners
25. https://learn.sparkfun.com/tutorials/blynk-board-bridge-widget-demo
26. https://www.hackster.io/onedeadmatch/esp32-web-server-with-bootstrap-b80105
27. https://arduinolearn.github.io/button.html
28. https://randomnerdtutorials.com/esp32-web-server-spiffs-spi-flash-file-system/
29. https://mui.com/
30. https://materializecss.com/
31. https://getmdl.io/
32. https://getmdl.io/index.html
33. https://www.joshwcomeau.com/
34. https://overapi.com/javascript



   


## Parte 2 - Agregar la interacción con Python y el arduino





## Parte 3 - Agregar una interfaz bonita



## Enlaces

* https://realpython.com/the-model-view-controller-mvc-paradigm-summarized-with-legos/
* https://realpython.com/python-web-applications-with-flask-part-i/
* https://realpython.com/python-web-applications-with-flask-part-ii/
* https://realpython.com/python-web-applications-with-flask-part-iii/
* https://www.pythontutorial.net/tkinter/tkinter-mvc/
* https://www.giacomodebidda.com/posts/mvc-pattern-in-python-introduction-and-basicmodel/
* https://openclassrooms.com/en/courses/6900866-write-maintainable-python-code/7009312-structure-an-application-with-the-mvc-design-pattern
* https://github.com/williamniemiec/MVC-in-Python
* https://learn.sparkfun.com/tutorials/using-flask-to-send-data-to-a-raspberry-pi/all#hardware-hookup
* https://flask.palletsprojects.com/en/2.1.x/
* https://pythonspot.com/flask-web-app-with-python/
* https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world
* https://medium.com/swlh/python-oop-mvc-data-science-tkinter-23c3e8dab70f
* https://www.tutorialspoint.com/python_design_patterns/python_design_patterns_model_view_controller.htm
* https://realpython.com/learning-paths/object-oriented-programming-oop-python/
* https://realpython.com/python3-object-oriented-programming/
* https://python-course.eu/python-tutorial/
* https://www.mischianti.org/2020/05/16/how-to-create-a-rest-server-on-esp8266-and-esp32-startup-part-1/
* https://www.mischianti.org/2020/05/24/rest-server-on-esp8266-and-esp32-get-and-json-formatter-part-2/