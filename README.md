
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
