# image-test
## Descripción
Es un repositorio que almacena una estructura de ficheros que permiten disponibilizar una imagen en el registro base de imágenes docker de forma automática. 

Los ficheros fundamentales son los siguientes:
```sh
* Dockerfile - descriptor de la imagen

* image.details - fichero de texto que contiene:

  * NAME=<nombredelaimagen>
  * VERSION=<versiondelaimagen>

```  
## Beneficios
En el estado del arte actual, la solución introduce los siguientes beneficios:
```sh
* Automatización del flujo que permite la disponibilización de imagenes en el registro de imágenes base (tanto de imágenes nuevas como de nuevas versiones)

* Simplifica la configuracion en puestos locales al evitar la instalación de certificados como la gestión de usuarios en servidor 
  (en escenarios donde no se utiliza una solucion enterprise de registro de imágenes docker)

* Solución reutilizable COMPLETA para todo los proyectos de creación de imágenes docker

```

## Casos de uso
   A continuacion se muestran algunos ejemplos de los casos de uso:
 ```sh
   * Gestión del ciclo de vida de la imagen. 
          * Con cada commit sobre gitlab, se dispara un trigger que disponibiliza la imagen en el registro privado Docker.
          * Aceptaciones de pull requests por parte del propietario del repositorio, generaran automáticamente una nueva versión de la imagen 
            (atendiendo a la informacion existente en el fichero image.details)
   
   * Creación de repositorio en gitlab para un nuevo tipo de proyecto de "Creación de imagen Docker" con la estructura de ficheros y la integración 
     con Jenkins (web hook)  para poder disparar automaticamente el proceso de generación de imagen en el registro privado  docker de imágenes base.
   ```

## Nuevas funcionalidades
Se trata de una version en modo PoC con objeto de mostrar las capacidades. La versión "Enterprise" debería mejorar los siguientes aspectos:
 ```sh
  * Gestión avanzada de excepciones
  
  * Inclusión del enlace a gitlab en la información de la imagen que se disponibilza en el registro Docker con objeto de poder linkar ambos sistemas.
  
  * Inclusion de nuevos metadatos en el fichero image.details (url gitlab, etc)
  
  * TBD
  ```