---
layout: post
title: Gestión de permisos en Linux.
---

# Permisos en Linux

Los permisos en Linux permiten compartir o restringir información y acceso a los recursos de nuestro sistema. Un mal manejo de permisos puede hacer que algo no funcione como debería.

Si utilizamos el comando **ls -l** para ver los permisos de un archivo o directorio, un ejemplo sería:

![Ejemplo de permisos en un archivo en Linux](https://github.com/sifefor/sifefor.github.io/blob/master/images/ejemplo_permisos.jpeg)

Observa el carácter señalado con la etiqueta "Tipo de archivo". Aquí pueden aparecer cualquiera de las siguientes opciones:

* d --> directorio.
* l --> enlace simbólico.
* c --> dispositivo de caracter.
* b --> dispositivo de bloques.
* c --> conexiones locales.
* p --> conexiones.


A continuación aparecen los permisos marcados por las letras **rwx**. Cada letra tiene el siguiente significado y valor:

| Código             | Permiso    | Valor Octal |  
|-------------------|:-------------|---------------:|
| r                 | lectura     | 4            | 
| w                 | escritura   | 2            | 
| x                 | ejecución   | 1            | 

Además aparecen repetidos para cada una de las siguientes opciones: el usuario, el grupo y el resto de los usuarios. 

El valor octal puede utilizarse para representar combinaciones de permisos, por el ejemplo, si el usuario tiene permisos de lectura escritura y ejecución, el valor correspondiente es 7 (4 + 2 + 1).

### **1. Crear directorios especificando permisos**
-----------

Cuando se crea un directorio con el mandato **mkdir**, éste asigna permisos por defecto.

![Ejemplo creación directorio con permisos](https://github.com/sifefor/sifefor.github.io/blob/master/images/ejemplo_permisos_1.jpeg)

En el ejemplo anterior se utiliza **mkdir test** para crear un directorio llamado test. Luego utilizamos **ls -l** para mostrar los permisos. Vemos que el directorio test tiene los permisos **rwxrwxr-x**, lo que representa lectura, escritura y ejecución para el usuario y el grupo, y de lectura y ejecución para el resto de usuario. En el sistema octal, sería el permiso 775.

Al crear un directorio, podemos especificar los permisos que necesitamos realmente.

