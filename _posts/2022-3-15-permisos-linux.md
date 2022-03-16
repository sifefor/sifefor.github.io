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

