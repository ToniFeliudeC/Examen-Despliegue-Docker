# Despliegue de aplicación usando Docker

## Introducción

Nuestra aplicación dispone de una base de datos MYSql, de la cual un código java recoge e inserta datos para que nuestro front-end pueda proporcionar un servicio.

Todas estas tecnologías se almacenan en contenederos de docker.

## Comienzo del despliegue

1. Partiendo desde una máquina Ubunto, crearemos un directorio cuyo contenido será nuestro proyecto.
2. Dentro de dicho directorio, creamos el directio "mysql-dump" el cual contendrá el script de creación de nuestra base de datos.
3. De nuevo dentro del mismo directorio, creamos una nueva carpeta en la que introduciremos el .war de nuestro proyecto.


## Configuración del archivo docker-compose.yml

Deberemos de modificar el archivo .yml para que se funcione bien con nuestro proyecto.

Como bien se muestra en la imagen, dejamos "root" como valor de la contraseña de root de MySQL, ponemos el nombre de nuestra base de datos "publicClassHamburguesa" en el campo "MYSQL_DATABASE", "root" en "MYSQL_USER" y la misma contraseña que pusimos en nuestro Dynamic Web Project de java, "Namiki1223", en el apartado "MYSQL_PASSWORD".

<img src="https://i.gyazo.com/142f12745561b3df7c87e43f17d2bd4c.png">

A continuación se observan ambos puertos, tanto del docker como de la base de datos.

<img src="https://i.gyazo.com/be05340a9afdb1a84fdb573b643aee7d.png">

El apartado de phpmyadmin lo dejamos con los valores por defecto.

<img src="https://i.gyazo.com/143d8a5529ed845c3ce47a0803e65f1f.png">

En el apartado de web, nos aseguramos de que "image" tenga la versión de tomcat que hemos usado, y no una superior inferior, puesto que eso haría que todo el proceso dejase de funcionar. En nuestro caso usamos Tomcat 10.0.21, por lo tanto indicamos "tomcat:10.0".

<img src="https://i.gyazo.com/d806f4d23b11678781f3761a7452f9c8.png">

También, en el apartado volumes, nos aseguramos de introducir la ruta hasta el .war que contiene todo nuestro proyecto.

<img src="https://i.gyazo.com/ce027424b5cd117ba97dc38d5942641d.png">

Señalamos, en este caso, el puerto de Tomcat.

<img src="https://i.gyazo.com/655bca4b9880369498fcb327f1c944b5.png">

Y por último volvemos a introducir los datos de inicio de usuario de nuestra base de datos para que la web pueda acceder a la misma.

<img src="https://i.gyazo.com/ccd57dcd3d0fb985092aba5019af0681.png">

Lanzamos el comando docker-compose up -d como administradores y esperamos hasta que se monten las imagenes

<img src="https://i.gyazo.com/459e9f586c387c19515a5095a5a677d5.png">

Finalmente, al ingresar a nuestro localhost en el puerto 8080, especificando la ruta de nuestro proyecto, se debería de poder apreciar el proyecto desplegado.

## Conclusiones

Docker es una tecnología de virtualización ligera que se basa en la utilización de contenedores y el despliegue de aplicaciones capsuladas en los mismos.

Los contenedores de Docker ayudan a empaquetar y desplegar de forma rápida y sencilla nuestros proyectos.

<img src="https://maximo.codes/docker/1_Introduccion/Docker_(container_engine)_logo.png">
