# Ejercicios docker 3 Enol Aláez
#### Trabajando con volumenes docker

<br>

###### 1.- Crea un volumen docker que se llame miweb .
![1](Caps%20docker%203/1.1.PNG)
```
docker volume create miweb
```

<br>

###### 2.- Crea un contenedor desde la imagen php:7.4-apache donde montes en el directorio
```

```

/var/www/html (que sabemos que es el DocumentRoot del servidor que nos ofrece esa
imagen) el volumen docker que has creado.
3. Utiliza el comando docker cp para copiar un fichero index.html en el directorio
/var/www/html .
4. Accede al contenedor desde el navegador para ver la información ofrecida por el fichero
index.html .
5. Borra el contenedor
6. Crea un nuevo contenedor y monta el mismo volumen como en el ejercicio anterior.
7. Accede al contenedor desde el navegador para ver la información ofrecida por el fichero
index.html . ¿Seguía existiendo ese fichero?
<br>