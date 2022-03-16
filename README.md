
# Practica-docker-nginx
Creando una imagen personalizada en docker: Nginx


## Instalación


Primero ejecutar la imagen llamada nginx, lo que hará que la descargue y la guarde en la caché de docker (las siguientes veces ya no la descarga)



![cap 1 ](https://user-images.githubusercontent.com/91556752/157688531-67bc2188-e521-4f5d-ba4a-512409bb0f3d.jpg)

      docker run --rm -d -p 8080:80 --name web nginx
      

---------------

#### Con el comando anterior, comienza la ejecución del contenedor como un demonio (-d) y publica el puerto 8080 en la red del host. También llamó web al contenedor usando la opción --name.

#### Ya sólo tienes que visitar http://localhost:8080 y a funcionar!



<img width="891" alt="cap2 Navegador" src="https://user-images.githubusercontent.com/91556752/157688562-d1edfbcc-e653-4e9d-8296-aba9d6a3c8e5.png">


----------

#### Lo que vemos es la página por defecto de Nginx. Pero ahora vamos a servir una hecha por nosotros.

Primero paramos el contenedor, llamado web.


      docker stop web

<img width="510" alt="cap 3: stop web" src="https://user-images.githubusercontent.com/91556752/157688586-8997203e-2faa-400e-9024-9dc259602d93.png">


## Agregar HTML personalizado




Crea un directorio en Documentos llamado nginx y dentro otro directorio llamado site-content. En este directorio, agrega un archivo index.html e introduce el siguiente html:


<img width="525" alt="cap4 crear directorios" src="https://user-images.githubusercontent.com/91556752/157688636-09a0102a-a26b-4c7e-b895-ff402fbec41e.png">



---------------





<img width="793" alt="cap 5 crear-html" src="https://user-images.githubusercontent.com/91556752/157688686-b2b91149-4542-4f35-b050-8ebf35f3a21d.png">




------


Ejecutamos el siguiente comando.

            docker run --rm -d -p 8080:80 --name web -v ~/Desktop/Documentos/nginx/site-content//:/usr/share/nginx/html nginx



<img width="1101" alt="cap correcta" src="https://user-images.githubusercontent.com/91556752/157726876-e6a3edd3-5085-43b0-8dc2-52c6f7c618dd.png">



<img width="573" alt="captura html web" src="https://user-images.githubusercontent.com/91556752/157728630-1a282440-57c7-4801-bfc6-121fda7425f4.png">


## Crea una imagen personalizada

--------------

Para crear una imagen personalizada, necesitaremos crear un Dockerfile y agregarle nuestros comandos.

En el mismo directorio, crea un archivo llamado Dockerfile y pega los siguientes comandos.


<img width="993" alt="dokerfile creado" src="https://user-images.githubusercontent.com/91556752/158366609-1c3b62bb-36cd-4375-8763-b1bc23d11497.png">


    FROM nginx:latest
    COPY ./site-content/index.html /usr/share/nginx/html/index.html


A continuación, copiamos nuestro archivo index.html en el directorio /usr/share/nginx/html dentro del contenedor, sobrescribiendo el archivo index.html predeterminado proporcionado por nginx.



<img width="780" alt="sobrescribiendo archivo index" src="https://user-images.githubusercontent.com/91556752/158366691-b2835c7f-eee8-4439-b309-78db517a0424.png">



### Para construir nuestra imagen, ejecuta el siguiente comando:


      docker build -t webserver .



El comando de compilación le dirá a Docker que ejecute los comandos ubicados en nuestro Dockerfile. Verás una salida similar en tu terminal a la siguiente:



<img width="777" alt="cap correcta imagen creada" src="https://user-images.githubusercontent.com/91556752/158571087-c7a3c3ec-01cb-43fd-89d6-3e34757acce7.png">


#### Ahora podemos ejecutar nuestra imagen en un contenedor, pero esta vez no tenemos que crear un volumen para incluir nuestro html pues ya lo hacemos en el Dockerfile al copiar el archivo.


      docker run --rm -d -p 8080:80 --name web webserver
      
 
### El resultado tiene que ser similar al siguiente:
 
  ##### En consola:
  
  
<img width="777" alt="ultima docker run rm" src="https://user-images.githubusercontent.com/91556752/158572669-fbdfa139-da44-442a-b5d2-3798465f8ed8.png">

##### En el navegador:

<img width="849" alt="ultima captura web localhost" src="https://user-images.githubusercontent.com/91556752/158572704-efc52050-50e2-4af7-b627-796c8244f65b.png">

## PARTE B:

 ## ¿Es posible publicar la web de pruebas mediante Microsoft Azure? Describe tu proceso de investigación.
 

La respuesta es que si,para ello desde nuestra máquina accedemos a redes y Agregar regla de puerto de entrada.


<img width="877" alt="parteb CAP1" src="https://user-images.githubusercontent.com/91556752/158659612-638b901d-0197-4066-92cc-248ba9dd69cd.png">

Cambiamos el servicio a HTTP o HTTPS, en este caso he elegido HTTPS y hacemos click en agregar.





<img width="877" alt="ParteB cap2" src="https://user-images.githubusercontent.com/91556752/158659641-dc856603-167a-4f11-b3fb-d8fc297ca07f.png">


#### Ahora ya podriamos publicar la web de pruebas desde Azure.

