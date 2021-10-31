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
  
En la primera prueba del RGB me dí cuenta de que este no funcionaba como en el manual, tenía la polaridad cambiada (había que conectar el cátodo a 3.3 V) por lo que las instrucciones de HIGH y LOW había que ponerlas a la inversa para que luciera. De todos modos los prgramas están hechos con un RGB que tiene la polaridad estandar.

<div align="center"> 2. </div>
Al trabajar sin cambiar los ciclos de cada componente RGB (ejercicio 2) me encontré con el problema de que al combinar algún color con el rojo, predominaba el rojo. Entonces puse una resitencia para cada componente RGB en vez de 1 solo para el cátodo. Probé con varias pero rebajaban demasiado la corriente en el rojo. La solución fué poner la misma resistencia a las 3 componentes por separado. Al realizar esto los colores secundarios dieron una calidad más que aceptable.

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
<br></br>
## Edición de la wiki
Para editar la wiki también se necesitaron conocimientos básicos de HTML

1. Comando usado fué para alinear en el centro elementos:
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

<br></br>
## Curiosidades 
### Visión estereo

### Como funciona un airbag


<br></br>
## Bibliográfia
- [Etiquetas HTML para README.md](https://github.com/MineiToshio/CursosPlatzi/blob/master/Curso%20de%20Desarrollo%20Web%20Online/README.md)
- [Como funciona un airbag](https://www.hella.com/techworld/es/Informacion-Tecnica/Electricidad-y-electronica-del-automovil/Sistema-airbag-3083/)
- [Página del grandchallenge](http://www.grandchallenge.org/)
- [Links en HTML](https://www.yoseomarketing.com/blog/crear-hipervinculos-html-links-enlaces/)
