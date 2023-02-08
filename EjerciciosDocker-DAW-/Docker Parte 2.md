## Ejercicios Docker: Parte 2 (Imágenes)

1. Descarga las siguientes imágenes: ubuntu:18.04, httpd, tomcat:9.0.39-jdk11,jenkins/jenkins:lts, php:7.4-apache.
````
docker pull nombreDeLaImagen
````
![](file:///C:/Users/ainho/OneDrive/Escritorio/docker/Img15.png)


2. Muestras las imágenes que tienes descargadas.
````
docker image ls
````
![](file:///C:/Users/ainho/OneDrive/Escritorio/docker/Img16.png)`

3. Crea un contenedor demonio con la imagen php:7.4-apache.
````
docker run -d --name php php:7.4-apache bash 
````
![](file:///C:/Users/ainho/OneDrive/Escritorio/docker/Img17.png)

4. Comprueba el tamaño del contenedor en el disco duro.
````
docker system df
````
![](docker/Img18.png)

5. Con la instrucción docker cp podemos copiar ficheros a o desde un contenedor. Puedes encontrar información es esta página. Crea un fichero en tu ordenador, con el siguientecontenido:Copia un fichero info.php al directorio /var/www/html del contenedor con docker cp.

Creamos el fichero en el nano, el cual guardaremos como  info.php
````
nano
````
![](Img19.png)
![](Img20.png)
Una vez guardado, copiamos el fichero en el directorio 
````
docker cp infoo.php php:/var/www/html
````
![](Img21.png)

6. Vuelve a comprobar el espacio ocupado por el contenedor.
````
docker system df
````
![](Img22.png)

7. Accede al fichero info.php desde un navegador web.
