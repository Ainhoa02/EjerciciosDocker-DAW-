## Ejercicios de Repaso-Docker

1. Instala docker en una máquina y configúralo para que se pueda usar con un usuario sinprivilegios.
````
usermod -aG docker usuario
````
![](Img1.png)

2. Ejecuta un contenedor a partir de la imagen hello-word. Comprueba que nos devuelve lasalida adecuada. Comprueba que no se está ejecutando. Lista los contenedores que estánparado. Borra el contenedor.

- Ejecutar contendor con imagen hello-world
````
docker run hello-world
````
![](Img2.png)
- Comprobacion de que no se está ejecutando, se ejecuta una vez y cuando esta deja de estar activa, se apaga automaticamente, comprobacion:
````
docker ps
````
![](Img3.png)
- Lista de los contenedores
````
docker ps -a
````
![](Img4.png)
- Eliminar el contenedor , en este caso elegi por su ID, aunque tambien se puede por su nombre
````
docker rm a8b2baeae079
````
![](Img5.png)

3. Crea un contenedor interactivo desde una imagen debian. Instala un paquete (por ejemplonano). Sal de la terminal, ¿sigue el contenedor corriendo? ¿Por qué?. Vuelve a iniciar elcontenedor y accede de nuevo a él de forma interactiva. ¿Sigue instalado el nano?. Sal delcontenedor, y bórralo. Crea un nuevo contenedor interactivo desde la misma imagen. ¿Tiene el nano instalado?

- Creacion del contenedor
````
docker run -it --name contenedorInteractivo debian bash 
````
![](Img6.png)
-Instalación nano
````
docker exec contenedorInteractivo apt-get install nano
````
![](Img7.png)

- Borramos el contendor, y comprobamos en la lista que ya no aparece
````
docker rm -f contenedorInteractivo
docker ps -a
````
![](Img14.png)

Preguntas:
- ¿sigue el contenedor corriendo?, ¿por que ? -> No, una vez fuera de la terminal el contenedor se apaga
- ¿Sigue instalado el nano? -> Si, se mantienen las descargas ejecutadas


4. Crea un contenedor demonio con un servidor nginx, usando la imagen oficial de nginx. Alcrear el contenedor, ¿has tenido que indicar algún comando para que lo ejecute? Accede alnavegador web y comprueba que el servidor esta funcionando. Muestra los logs del contenedor.

- Creacion del contendor demonio
Ejecutamos el contenedor a partir de la imagen con docker container run 
````
docker container run --name my-nginx -p 80:80 nginx
````
![](Img8.png)
````
https://127.0.0.1
````
![](Img9.png)
- Mostrar los logs del contenedor 
````
docker logs my-nginx
````
![](Img10.png)
![](Img12.png)

5. Crea un contenedor con la aplicación Nextcloud, mirando la documentación en docker Hub,para personalizar el nombre de la base de datos sqlite que va a utilizar.

- Descargamos nextcloud
````
docker pull nextcloud
````
![](Img11.png)
````
docker run -d -p 8080:80 nextcloud
````
````
docker ps -a
````
![](Img13.png)