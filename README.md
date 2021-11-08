# wiki-sensores-y-actuadores
Experiencia adquirida por la asignatura de sensores y actuadores.

Alumno: Adrián Madinabeitia Portanova.


## Experiencia en el [proyecto 0](https://github.com/clases-julio/p0-welcome-amadinabeitia2020)
Durante este proyecto nos familiarizamos con git, haciendo varias pruebas como eliminar y añadir archivos o directorios, crear commits o añadir imagenes y links a nuestro README. 

### Creación de un token
En este proyecto tuve que crear un token en git para poder subir cambios al repositorio:
1. Entramos a nuestra cuenta de git.
2. Hacemos click arriba a la derecha donde esta nuestra foto de perfil desplegando un menú.
3. Seleccionamos "Settings".
4. Buscamos en el menú de la izquierda "Developer settings" y le accemos click.
5. De nuevo en el menú de la izquierda hacemos click en "Personal access tokens".
6. Hacemos click en "Generate new token".
7. Seleccionamos el nombre y la fecha de expiración que deseemos.
8. Damos los permisos que queramos al usuario que use el token (En mi caso le di a todos).
9. Clickeamos en "Generate token".
10. Guardamos nuestro token en un sitio seguro ya que no se nos volverá a mostrar en git.


### Atajo
El token es prácticamente imposible de memorizar, para no introducirlo cada vez que subamos un commit creé un alias que guardara en caché el usuario y el token (comado dicho por el profesor en clase)
```bash
git config --global alias.tok 'config --global credential.helper cache --timeout=3600'

# Después para ejecutar el comando:
git tok
```
<br></br>
## Experiencia en el [proyecto 1](https://github.com/clases-julio/p1-introrpi3-led-amadinabeitia2020)
En este proyecto tuvimos que instalar nuestra tarjeta Raspbi con su respectivo sistema operativo y encender un led con ella, ya que cuando realizé el proyecto 1 no se había empezado esta wiki, en el README de este proyecto podemos ecnontrar mi experencia adquirida en el mismo.

<br></br>
## Experiencia en el [proyecto 2](https://github.com/clases-julio/p2-introgpio-ledrgb-amadinabeitia2020)

### Descripción del proyecto:
En el primer ejercicio el RGB pasa de un color a otro desvaneciendose entre los valores intermedios de los colores primarios.

En el segundo ejercicio el usuario introduce uno de los colores disponibles como entrada y el RGB luce en el color indicado.

### Problemas a resaltar:
<div align="center"> 1. </div>
  
En la primera prueba del RGB me dí cuenta de que este no funcionaba como en el manual, tenía la polaridad cambiada (había que conectar el ánodo a 3.3 V) por lo que las instrucciones de HIGH y LOW había que ponerlas a la inversa para que luciera. De todos modos los prgramas están hechos con un RGB que tiene la polaridad estandar.

<div align="center"> 2. </div>
Al trabajar sin cambiar los ciclos de cada componente RGB (ejercicio 2) me encontré con el problema de que al combinar algún color con el rojo, predominaba el rojo. Entonces puse una resitencia para cada componente RGB en vez de 1 solo para el ánodo. Probé con varias pero rebajaban demasiado la corriente en el rojo. La solución fué poner la misma resistencia a las 3 componentes por separado. Al realizar esto los colores secundarios dieron una calidad más que aceptable.

<div align="center"> 3. </div>
Durante la práctica hay un fallo, me refiero al ánodo como el cátodo. 
<br></br>

## Experiencia en el [proyecto 3](https://github.com/clases-julio/p3-interrupciones-amadinabeitia2020)

### Descripción del proyecto:
En este proyecto practicamos con el concepto de interrupciones, concepto que nunca había trabajado y es interesante.


### Conceptos repasados
- Programación concurrente: Ejecución de varias tareas a la vez (distintos hilos de ejecución)
- Programación secuencial: Ejecuta el programa linea a linea (msimo hilo de ejecución)

### Comprobación de sobrecarga de memoria:
Pude comprobar como al no poner un time.sleep aunque sea mínimo se puede sobrecargar la memoria:

![alt text](https://github.com/amadinabeitia2020/wiki-sensores-y-actuadores/blob/main/fig/1-recursos.png?raw=true)

### Implementación vía hardware
Hablando con un compañero (Ivan Porras) llegamos a la conclusión de que debido a la naturaleza del programa sería mucho mas sencilla una implementación hardware.

Por el funcionamiento del botón cuando este se presiona pasa la corriente y enciende el led, una vez que se suelte el led dejará de lucir, esto nos quitaría la necesidad de tener que implementarlo de manera software.

[Funcionamiento](https://urjc-my.sharepoint.com/:v:/g/personal/a_madinabeitia_2020_alumnos_urjc_es/EQpbP2tNFgVFgbS7c79JxwEBTr5HWIcARMGrjuCxDGB-7g?e=bB2fnM)


### Montaje
Si conectamos una patilla de cada botón a negativo y la otra directamente a la parte negativa del led (con su respectiva resistencia) y el led a 3.3 V. Sin necesidad de código. Podemos realizar la función de encender leds con el botón de una manera mucho mas eficiente.

<div align = center>
  <img src = "https://github.com/amadinabeitia2020/wiki-sensores-y-actuadores/blob/main/fig/2-montaje.jpg?raw=true"
     alt="Montaje" height="80%" width="80%"
     />
 </div>

<br></br>
## Experiencia en el [proyecto 4](https://github.com/clases-julio/p4-threads-amadinabeitia2020)

### Distribución carpetas git
Se empezó a hacer una correcta distribución en los reposistorios de git:
- fig = Recursos como imágenes
- src = codigo
- doc = documentacion

### Buenas prácticas de programación
Al empezar con proyectos mas complejos se emplean otras tećnicas de programación:
- Programación modular
- Constantes con mayusculas
- No usar variables globales

### POO
Analizamos el primer fragmento de código:
```python3
# Creamos una clase llamada "Hilo" que hereda de la clase "threading.Thread"
class Hilo (threading.Thread): 

  # Cuando generamos __init__ se ejecuta resciviendo los parámetros necesarios
    def __init__(self, boton, led):
      threading.Thread.__init__(self)
      # Los variables dentro de una clase se llaman atributos
      self.btn = boton
      self.led = led
      self.tim = 10 # ms
```
Además cuando escribimos (self.ALGO) estamos comunicando al programa que estamos invocando a un método o atributo del mismo objeto. Si no lleva self, es una función o variable fuera del dominio del objeto.
```python3
# Aquí implementamos un método heredado de Threading.Thread y lo ajustamos a nuestro código
def run(self): # implementamos interfaz run heredado de Thread
        while True:
            self.noPressedBtn()
```
La programación orientada a objetos nos permite crear estrucutras de código mucho más sofisticadas además de ser una herramienta muy útil para hacer más visual y reutilizable nuestro código.


### Conflicto git
En la realización de este proyecto tuve un conflicto en git y me parece interesante redactar como solucionar un conflicto:
1- Creamos una rama:
```bash
git branch error
```
2- Traemos los cambios subidos a git
```bash
git pull
```
3- Combinamos ambas ramas 
```bash
git merge main error
```
Solucionando lo que tengamos que juntar (en mi caso eran dos archivos distintos por lo que no tuvo dificultad). Ya tendremos un commit con todos nuestros cambios realizados.
### UMlet
Esta herramienta nos permite crear un diagrama de nuestro código para poder ver de forma mas clara lo que hace nuestro programa.

Para instalar umlet usamos el comando:
```bash
sudo apt install umlet
```
Sus elementos tienen la siguiente nomenclatura
<div align = center>
  <img src = "https://github.com/amadinabeitia2020/wiki-sensores-y-actuadores/blob/main/fig/3-umlet_basics.png?raw=true"
     alt="umlet_basics"
     />
 </div>
 
Durante la explicación del profesor de esta herramienta, también hicimos nuestro primer diagrama. Es bastante util ya que podemos exportar los diagramas como imágenes, pdfs...
<div align = center>
  <img src = "https://github.com/amadinabeitia2020/wiki-sensores-y-actuadores/blob/main/fig/4-UMLBasic.png?raw=true"
     alt="UML basic"
     />
 </div>
 
<br></br>
## Experiencia en el [proyecto 5](https://github.com/clases-julio/p5-encoder-amadinabeitia2020)
### Conectarse por ssh a raspbi
Por ciertos motivos necesité manejar la raspberry de foma remota ya que no disponía de monitor, así conseguí conectarme a la placa por ssh:

### Problema-solución de sensor infrarrojos estropeado
En este proyecto tuve el problema de que el sensor requerido no me funcionaba por lo que utilicé uno que tenía de proyectos anteriores. Esto a su vez me permitió mayor libertad para distribuir los componentes. Todas las especificaciones del sensor y su funcionamiento están en el proyecto.

En el caso del emisor desmonté un mando a distancia para quitarle su led infrarrojo y enviar mis propias señales, no conseguí un resultado estable por lo que opté por terminar el proyecto con el mando normal. 

Este es el mando desmontado:
INSERTAR IMAGENES DE AMBOS MANDOS

Su funcionamientoes sencillo, la alimentación se conecta por las dos patillas de abajo. Las teclas poseen elementos conductores que al presionarse cierran un circuito, este circuito dependiendo de la tecla que sea transmite una señal infrarroja u otra.

Además se intentó hacer girar las aspas con un motor pero este producía interferencias al sensor y este tomaba falsas lecturas infrarojas por el motor (mo llegué a saber por que), por lo que hice un mecanismo manual para girar el aspa. 
<br></br>

 ### Fritzing
 Utilizamos el software de fritzing para empezar a representar nuestros circuitos.

## Experiencia en el [proyecto 6](https://github.com/clases-julio/p6-distanciaus-amadinabeitia2020)


<br></br>
## Edición de la wiki
Para editar la wiki también se necesitaron conocimientos básicos de HTML

1. Alineación de elementos:
```html
  <div align="center"> TEXTO </div>
```

2. Insertar imágenes:
```html
<img src="Dirección imagen" alt="nombre" height="altura" width="ancho"/>
```

3. Espacio en blanco  
```html
<br></br>
```

4. Añadir un link 
```html
<a href=”url” target="">name</a>
```
Targets:
- _self: Abre en enlace en la misma pestaña. Es la opción por defecto.
- _blank: Abre el enlace en una nueva pestaña o ventana.
- _parent: Abre el enlace en el marco padre
- _top: Abre el enlace ocupando toda la pantalla
- Framename: Abre el enlace en un frame determinado.

<br></br
## Componentes electrónicos:
### Funcionamiento de un potenciómetro
Un potenciómetro suele tener 2 resistencias en serie y su funcionamiento se da en base a la caida de la tensión como ocurre en una resistencia
<div align="center">
  <img src="INSERTAR IMAGEN DEL PROYECTO 5" 
     alt="Potenciometro por dentro"
     /> </div>
     
- La terminal 1 es la entrada de voltaje.
- La terminal 2 es la salida de voltaje.
- La terminal 3 es la toma a tierra.

La corriente entra por la terminal 1, pasa por el material resistivo la distancia que haya configurado el usuario y sale por la terminal 2.

## Funcionamiento de un sensor infrarrojo (práctica 5)

<br></br>
## Curiosidades 
### Sensores de un airbag
Su número depende del nº de airbags disponibles. Los sensores de accidente y aceleración se suelen encontrar directamente en la unidad de control.

Los sensores frontales suelen trabajar según el sistema masa-resorte. Dentro del mismo se encuentra una polea con bastante peso. Esta misma está rodeada por una abrazadera de bronce, cuyo extremo va fijado a la polea de peso y a la carcasa del sensor. Así solo se podrá sensar fuerza en una dirección.

Si se aplica la fuerza, la polea de peso gira contra la abrazadera de bronce haciendo contacto y cerrando el circuito. El sensor tiene una impedancia muy elevada para evitar que los airbags salten sin necesidad.

También se emplean sensores con masa de silicio, sensores de presión(en las puertas).

El umbral de activación de los sensores suele ser de 3 - 5 g. Se usan 2 sensores que trabajan de manera independite de nuevo para evitar falasas lecturas. 


<br></br>
## Bibliográfia
- [Etiquetas HTML para README.md](https://github.com/MineiToshio/CursosPlatzi/blob/master/Curso%20de%20Desarrollo%20Web%20Online/README.md)
- [Como funciona un airbag](https://www.hella.com/techworld/es/Informacion-Tecnica/Electricidad-y-electronica-del-automovil/Sistema-airbag-3083/)
- [Página del grandchallenge](http://www.grandchallenge.org/)
- [Links en HTML](https://www.yoseomarketing.com/blog/crear-hipervinculos-html-links-enlaces/)
- [Conectarse a raspberrypi por ssh](https://tonyteaches.tech/raspberry-pi-ssh/)
- [Repo fritzing en github](https://github.com/fritzing/fritzing-app)
