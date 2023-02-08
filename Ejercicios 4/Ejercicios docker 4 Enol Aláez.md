# Ejercicios docker 4 Enol Aláez
#### Trabajando con redes docker

1. Vamos a crear dos redes de ese tipo (BRIDGE) con los siguientes datos:
Red1
Nombre: red1
Dirección de red: 172.28.0.0
Máscara de red: 255.255.0.0
Gateway: 172.28.0.1
Red2
Nombre: red2
Es resto de los datos será proporcionados automáticamente por Docker.
* ![1](Caps%20docker%204/Parte%201/1.1.PNG) 
```
docker network create "nombre red" --subnet "subred" --gateway "puerta de enlace"
```
* ![1](Caps%20docker%204/Parte%201/1.2.PNG) 
```
docker network create "nombre red"
```

2. Poner en ejecución un contenedor de la imagen ubuntu:20.04 que tenga como hostname
host1 , como IP 172.28.0.10 y que esté conectado a la red1. Lo llamaremos u1 .
* ![1](Caps%20docker%204/Parte%201/2.1.PNG) 
```
docker run --name contenedor4 --network "nombr red" --ip "direccion ip" --hostname "nombre contenedor host" ubuntu:20.04
```
3. Entrar en ese contenedor e instalar la aplicación ping ( apt update && apt install
inetutils-ping ).
* ![1](Caps%20docker%204/Parte%201/3.1.PNG) 
```
"despues de crear "contenedor4""
docker exec -it contenedor4 bash
```

* ![1](Caps%20docker%204/Parte%201/3.2.PNG) 
```
"despues de hacer apt-update y apt-upgrade"
apt install inetutils-ping
```
4. Poner en ejecución un contenedor de la imagen ubuntu:20.04 que tenga como hostname
host2 y que esté conectado a la red2. En este caso será docker el que le de una IP correspondiente
a esa red. Lo llamaremos u2 .
* ![1](Caps%20docker%204/Parte%201/4.1.PNG) 
5. Entrar en ese contenedor e instalar la aplicación ping ( apt update && apt install
inetutils-ping ).
El documento debe contener, además, los siguientes pantallazos:<br>
·Pantallazo donde se vea la configuración de red del contenedor u1(red1).<br>
* ![1](Caps%20docker%204/Parte%201/6.1.PNG)
```
docker network inspect "nombre red" 
```
·Pantallazo donde se vea la configuración de red del contenedor u2(red2).<br>
* ![1](Caps%20docker%204/Parte%201/6.2.PNG) 
·Pantallazo donde desde cualquiera de los dos contenedores se pueda ver que no podemos hacer ping al
otro ni por ip ni por nombre.<br>
* ![1](Caps%20docker%204/Parte%201/6.3.PNG) 
* ![1](Caps%20docker%204/Parte%201/6.4.PNG) <br>
·Pantallazo donde se pueda comprobar que si conectamos el contenedor u1 a la red2 (con docker
network connect ), desde el contenedor u1, tenemos acceso al contenedor u2 mediante ping, tanto
por nombre como por ip.
* ![1](Caps%20docker%204/Parte%201/6.6.PNG)
```
docker network connect "nombre red" "nombre contenedor"
```
* ![1](Caps%20docker%204/Parte%201/6.7.PNG) 
* ![1](Caps%20docker%204/Parte%201/6.8.PNG) 


### Despliegue de Nextcloud + mariadb/postgreSQL
Vamos a desplegar la aplicación nextcloud con una base de datos (puedes elegir mariadb o PostgreSQL)
(NOTA: Para que no te de errores utiliza la imagen mariadb:10.5 ). Te puede servir el ejercicio que
hemos realizado para desplegar Wordpress . Para ello sigue los siguientes pasos:
1. Crea una red de tipo bridge.
![2](Caps%20docker%204/Parte%202/1.1.PNG)

2. Crea el contenedor de la base de datos conectado a la red que has creado. La base de datos se debe
configurar para crear una base de dato y un usuario. Además el contenedor debe utilizar
almacenamiento (volúmenes o bind mount) para guardar la información. Puedes seguir la
documentación de mariadb o la de PostgreSQL .
![2](Caps%20docker%204/Parte%202/2.1.PNG)
```
"docker run -d --name "nombre contenedro mariadb" --env MARIADB_USER="nombre usuario" --env MARIADB_PASSWORD="contraseña" --env MARIADB_ROOT_PASSWORD="contraseña del root" -v volumensql:/var/mysql --network "nombre red" -p "puerto (8080:80)" mariadb:10.5
```
3. A continuación, siguiendo la documentación de la imagen nextcloud , crea un contenedor conectado a
la misma red, e indica las variables adecuadas para que se configure de forma adecuada y realice la
conexión a la base de datos. El contenedor también debe ser persistente usando almacenamiento.
![2](Caps%20docker%204/Parte%202/3.1.PNG)
```
docker run -d -v nextcloud1:/var/www/html --netowrk "nombre red" --env MYSQL_DATABASE="nombre contenedro database" -p "puerto" nextcloud:latest
```
4. Accede a la aplicación usando un navegador web.
El documento debe contener, además, los siguientes pantallazos:<br>
·Pantallazo donde se ve el acceso a la aplicación desde un navegador web.<br>
![2](Caps%20docker%204/Parte%202/4.1.PNG)
![2](Caps%20docker%204/Parte%202/4.2.PNG)