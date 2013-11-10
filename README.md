# Documentación Práctica 2: Aislamiento de una aplicación web

## Juan Antonio Pérez Maldonado

## Licencia de la aplicación: GPLv3


### Explicación de la práctica

El principal objetivo de esta práctica es familiarizarse con este tipo de infraestructura virtual que se usa generalmente para dar un acceso limitado a una aplicación o un servicio tal como un servidor web o a un usuario, que pueda acceder por ejemplo sólo para depositar ficheros.

El objetivo secundario es el que el alumno tenga instaladas las herramientas necesarias para crear jaulas chroot y tenga claro en qué casos son la mejor y más eficiente opción; también en qué casos conviene usarlas por motivos de seguridad. Estas herramientas se añadirán a la panoplia de herramientas de un administrador que al terminar la asignatura tendría que tener el alumno.

El énfasis de esta práctica es en el despliegue en una jaula. por lo que no será necesario hacer una aplicación específica para la misma. Sin embargo, es posible que sea más fácil crear la aplicación para esta jaula usando cualquier lenguaje de scripting (tal como Python, PHP, Perl o Ruby) que enjaular una aplicación ya creada, con todas sus dependencias; posiblemente, en todo caso, merezca la pena hacerlo. Si se desea, se puede usar la misma aplicación que en la primera práctica.

### Realización de la práctica

Para realizar la práctica como ya se ha realizado en los ejercicios del tema, necesitamos tener instalado
el paquete debootstrap, que se instalaba con el comando:

> sudo apt-get install debootstrap

Una vez instalado debootstrap, vamos a usar la distribución quantal ya creada en el ejercicio 3 de los ejercicios
del Tema 2, ubicado en /home/jaulas/quantal

Para recordar cómo crear la distribución quantal podemos dirigirnos a
la dirección: 

https://github.com/jpm88/IV-Ejercicios/wiki/Ejercicios-25-de-octubre

Ahora entramos a la jaula con el siguiente comando:

> sudo chroot /home/jaulas/quantal

(imagen)

Si intentamos ejecutar top para comprobar que funciona correctamente, nos saldrá este mensaje:

(imagen)

Para arreglarlo tenemos que escribir el siguiente comando:

> sudo mount -t proc proc /proc

Entonces ya si ejecutamos top y como se muestra en la siguiente imagen funciona correctamente:

(imagen)

Ahora instalamos el servidor apache con el siguiente comando:

> sudo apt-get install apache2

Después instalamos php5:

> sudo apt-get install php5 libapache2-mod-php5

Para que se apliquen los cambios tenemos que reiniciar apache con el siguiente comando:

> /etc/init.d/apache2 restart

Ahora tenemos que añadir la aplicación web, en este caso se ha usado una versión simplificada de la
aplicación web utilizada en la Práctica 1, para añadirla tenemos que copiarla al directorio /var/www de
la máquina quantal con el siguiente comando:

> sudo cp -r web/* /home/jaulas/quantal/var/www

Por último reiniciamos otra vez apache.

En la siguiente imagen se muestra el paso de la copia de los archivos a /var/www y el reinicio de apache:

(imagen)

Una vez hecho todo esto escribimos en el navegador localhost y nos saldrá la aplicación web:

(imagen)


### Repositorio

https://github.com/jpm88/Practica2-IV

### Bibliografía

http://jj.github.io/IV/documentos/temas/Tecnicas_de_virtualizacion

http://jj.github.io/IV/documentos/practicas/2.Jaula
