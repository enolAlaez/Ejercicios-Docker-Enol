# Ejercicios docker 2 Enol Alvarez

<br>

###### 1.- Descarga las siguientes images: ubuntu:18.04, httpd, tomcat:9.0.39-jdk11, jenkins/jenkins:lts, php:7.4-apache.

![1](Caps%20docker%202/1.1.PNG)
![1](Caps%20docker%202/1.2.PNG)
![1](Caps%20docker%202/1.3.PNG)
![1](Caps%20docker%202/1.4.PNG)
![1](Caps%20docker%202/1.5.PNG)
```
docker pull "nombre de la imagen"
```

<br>

###### 2.- Muestra todas las ramas
![1](Caps%20docker%202/2.1.PNG)
```
docker images
```

##### 3.- Crear un contenedor demonio con la imagen php:7.4-apache
![1](Caps%20docker%202/3.3.PNG)
```
docker run -d --name "onmbre contenedor" php:7.4-apache
docker ps -a
```


###### 4.- Comprueba el tamaño del contenedor en el disco duro.
![1](Caps%20docker%202/4.1.PNG)
```
docker ps -s
```

