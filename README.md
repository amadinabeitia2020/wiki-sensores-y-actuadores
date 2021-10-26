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
git conifg --global alias.tok 'config --global credential.helper cache --timeout=3600'

# Después para ejecutar el comando:
git tok
```



## Experiencia en el [proyecto 1](https://github.com/clases-julio/p1-introrpi3-led-amadinabeitia2020)
En este proyecto tuvimos que instalar nuestra tarjeta Raspbi con su respectivo sistema operativo y encender un led con ella, ya que cuando realizé el proyecto 1 no se había empezado esta wiki, en el README de este proyecto podemos ecnontrar mi experencia adquirida en el mismo.




## Experiencia en el [proyecto 2](https://github.com/clases-julio/p2-introgpio-ledrgb-amadinabeitia2020)

### Descripción del proyecto:
En el primer ejercicio el RGB pasa de un color a otro desvaneciendose entre los valores intermedios de los colores primarios.

En el segundo ejercicio el usuario introduce uno de los colores disponibles como entrada y el RGB luce en el color indicado.

### Problemas a resaltar:
<div align="center"> 1. </div>
  
En la primera prueba del RGB me dí cuenta de que este no funcionaba como en el manual, tenía la polaridad cambiada (había que conectar el cátodo a 3.3 V) por lo que las instrucciones de HIGH y LOW había que ponerlas a la inversa para que luciera. De todos modos los prgramas están hechos con un RGB que tiene la polaridad estandar.

<div align="center"> 2. </div>
Al trabajar sin cambiar los ciclos de cada componente RGB (ejercicio 2) me encontré con el problema de que al combinar algún color con el rojo, predominaba el rojo. Entonces puse una resitencia para cada componente RGB en vez de 1 solo para el cátodo. Probé con varias pero rebajaban demasiado la corriente en el rojo. La solución fué poner la misma resistencia a las 3 componentes por separado. Al realizar esto los colores secundarios dieron una calidad más que aceptable.




## Experiencia en el [proyecto 3](https://github.com/clases-julio/p3-interrupciones-amadinabeitia2020)

### Descripción del proyecto:
En este proyecto practicamos con el concepto de interrupciones, concepto que nunca había trabajado y es interesante.


### Conceptos repasados
- Programación concurrente: Ejecución de varias tareas a la vez (distintos hilos de ejecución)
- Programación secuencial: Ejecuta el programa linea a linea (msimo hilo de ejecución)

### Comprobación de sobrecarga de memoria:
Pude comprobar como al no poner un time.sleep aunque sea mínimo se puede sobrecargar la memoria:

![alt text](https://github.com/amadinabeitia2020/wiki-sensores-y-actuadores/blob/main/src/1-recursos.png?raw=true)

### Implementación vía hardware
Hablando con un compañero (Ivan Porras) legamos a la conclusión que debido a la naturaleza del prgrama sería mucho mas sencilla una implementación hardware.

Por el funcionamiento del botón cuando este se presiona deja pasar la corriente y enciende el led, una vez que se suelte el led dejará de lucir, esto nos quitaría la necesidad de tener que implementarlo de manera software.

[Funcionamiento](https://urjc-my.sharepoint.com/:v:/g/personal/a_madinabeitia_2020_alumnos_urjc_es/EQpbP2tNFgVFgbS7c79JxwEBTr5HWIcARMGrjuCxDGB-7g?e=bB2fnM)


### Montaje
Si conectamos una patilla de cada botón a negativo y la otra directamente a la parte negativa del led (con su respectiva resistencia) y el led a 3.3 V. Sin necesidad de código, haciendo la función(encender leds con el botón) mucho mas eficiente

![alt text](https://github.com/amadinabeitia2020/wiki-sensores-y-actuadores/blob/main/src/2-montaje.jpg?raw=true)


## Experiencia en el [proyecto 4](https://github.com/clases-julio/p4-threads-amadinabeitia2020)




## Curiosidades 
### Visión estereo

### Como funciona un airbag




## Bibliográfia
- [Etiquetas HTML para README.md](https://github.com/MineiToshio/CursosPlatzi/blob/master/Curso%20de%20Desarrollo%20Web%20Online/README.md)
- [Como funciona un airbag](https://www.hella.com/techworld/es/Informacion-Tecnica/Electricidad-y-electronica-del-automovil/Sistema-airbag-3083/)
- [Página del grandchallenge](http://www.grandchallenge.org/)

