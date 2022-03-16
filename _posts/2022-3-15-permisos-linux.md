---
layout: post
title: Gestión de permisos en Linux.
---

# Permisos en Linux

Los permisos en Linux permiten compartir o restringir información y acceso a los recursos de nuestro sistema. Un mal manejo de permisos puede hacer que algo no funcione como debería.

Si utilizamos el comando **ls -l** para ver los permisos de un archivo o directorio, un ejemplo sería:

![Ejemplo de permisos en un archivo en Linux](/images/ejemplo_permisos.jpeg)

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

![Ejemplo creación directorio con permisos](/images/ejemplo_permisos_1.jpeg)

En el ejemplo anterior se utiliza **mkdir test** para crear un directorio llamado test. Luego utilizamos **ls -l** para mostrar los permisos. Vemos que el directorio test tiene los permisos **rwxrwxr-x**, lo que representa lectura, escritura y ejecución para el usuario y el grupo, y de lectura y ejecución para el resto de usuario. En el sistema octal, sería el permiso 775.

Al crear un directorio, podemos especificar los permisos que necesitamos realmente.

![Ejemplo creación directorio especificando permisos](/images/ejemplo_permisos_2.jpeg)

En el ejemplo anterior, vemos cómo se crea un directorio *test2* con la opción **-m** (para especificar permisos) y el valor 700 que representa: lectura, escritura, ejecución para el usuario (4 + 2 + 1), y no le da permisos ni al grupo, ni a los demás usuarios: **rwx--**


Luego creamos otro directorio *test3* especificando permisos, pero utilizando otro método, y es indicando uno por uno los permisos necesarios. En directorio test3 se le crea con los siguientes permisos: **u = rwx, g = rx, o =** (tenga en cuenta la falta de espacios entre los valores). Es decir, le estamos diciendo que el usuario tiene los tres permisos, lectura, escritura y ejecución, pero el grupo sólo tiene el permiso de lectura y ejecución, mientras que los demás usuarios no tienen permiso alguno.

### **2. Cambiar los permisos de los archivos o directorios**
-----------

Se utiliza el comando **chmod**. Hay dos formas de utilizar chmod: especificando el valor octal, o indicando uno por uno los permisos a modificar.

En el ejemplo de arriba, creamos el directorio test2 con los siguientes permisos:

rwx--

Vimos que en octal, esto es el valor 700.
Si quisiéramos los siguientes permisos: rw-rr- el valor octal sería 644
Teniendo esto en cuenta , aplicaríamos el comando chmod:

![Ejemplo cambio permisos](/images/ejemplo_permisos_3.jpeg)

Observamos que se escribe **chmod 644 test2**, y el resultado sería el deseado.


También pudimos haber especificado los permisos uno por uno, es decir escribir:
**chmod u = rw, g = r, o = r test2** y el resultado sería el mismo.

### **3. Cambiar solo un permiso**
-----------

Si sólo necesitamos cambiar un permiso y que el resto de permisos permanezcan igual, lo más conveniente es indicar sólo el permiso que necesitamos cambiar.

Por ejemplo, si queremos sacar el permiso de ejecución al grupo en el directorio *test3*:

![Ejemplo cambio un solo permiso](/images/ejemplo_permisos_4.jpeg)

Lo que se hizo fue ejecutar el pedido:


``` 
chmod -c gx test3
```



Esto quita (-) el permiso de ejecución (x) al grupo (g) en directorio *test3*.

### **4. Ejercicios**
-----------

4.1 Cambie los permisos en el archivo **Linux.pdf** a **r--r-----**.

Sol:

```
chmod ug=r,o= Linux.pdf
```

4.2 Cambie los permisos en el archivo **Linux.pdf** a **r--r-----** usando notación octal.

Sol:

```
chmod 440 Linux.pdf
```

4.3 Cree un directorio **~/newdir** con permisos 700.

Sol:

```
mkdir -m 700 ~/newdir
```

Más ejemplos de comandos Linux en la [web de Paul Cobbaut](http://linux-training.be
)


### **ANEXO I: Tabla de permisos**
-----------

| Binario rwx       | Valor Octal    | Permiso |  
|-------------------|:-------------|---------------:|
| 001                 | 1           | Ejecución          | 
| 010                 | 2           | Lectura          | 
| 011                 | 3           | Escritura y ejecución           | 
| 100                 | 4           | Lectura        | 
| 101                 | 5           | Lectura y ejecución      | 
| 110                 | 6           | Lectura y escritura        | 
| 111                 | 7           | Lectura, escritura y ejecución        | 



### **ANEXO II: Beneficios de aprender sobre la interfaz de línea de comandos**

Uno de los principales beneficios de aprender la línea de comandos es el mayor control que obtienes sobre cualquier sistema operativo, ya se trate de Windows o Linux. Gracias a la línea de comandos puedes realizar desde tareas sencillas hasta operaciones más complicadas, que tal vez al realizarlas de manera manual te llevarían mucho más tiempo.

Los primeros comandos que aprenderás probablemente serán a revisar el contenido de un directorio o cambiar los permisos de cierto archivo. Comandos más complejos se pueden emplear para administrar servidores locales, por ejemplo. Así que, como ves, la interfaz de línea de comandos posee diversos usos, todo depende de qué tanto conocimiento poseas sobre esta interfaz.

Aparte de tener mayor control sobre tu sistema operativo, la interfaz de línea de comandos podría ser necesaria para otras herramientas que un desarrollador simplemente necesita. Así que aprender los comandos para poder controlar esta interfaz te traerá muchos beneficios.

Más información [aquí](https://blog.aulaformativa.com/beneficios-aprender-interfaz-de-linea-de-comandos/)


