---
layout: post
title: Comandos básicos en Linux.
---

# Operaciones con archivos y directorios en Linux.

Sistemas Operativos Monopuesto - 1SMR 


## 1. Visualización, creación y cambio de directorio.

### 1.1 pwd

El comando pwd muestra cuál es el directorio de trabajo actual, en otras palabras, le dice al usuario dónde se encuentra dentro de la estructura de directorios de sistema. ***Es muy útil cuando estamos perdidos.***

```
simfor@Server1CFGM:~$ pwd
/home/simfor
```
Nos esta indicando que estamos situados en el directorio /home/simfor




### 1.2 ls

El comando le muestra el contenido de la carpeta actual. Por defecto, los  archivos ocultos no se muestran. Éste es seguramente el comando que  más se utiliza.

```
simfor@Server1CFGM:~$ ls
 Applications   Compartit_de_grups   Escriptori    Selecció_001.png  'VirtualBox VMs'
 Baixades       Dades_Alumnes        Pictures      Selecció_002.png
 Compartit      Documents            Professorat   snap
```
En este ejemplo nos lista todos los ditectorios dentro del directorio inicial del usuario simfor.



Los parámetros del comando ***ls*** son:

![Parámetros y descripción del comando ls](/images/imagen1.png)



Si añadimos el parámetro **l** al comando **ls**, nos mostrará datos adicionales, como por ejemplo los permisos:

```
simon@simfor:~$ ls -l
total 40
drwxr-xr-x 2 simon simon 4096 mar  9 13:10  Descargas
drwxr-xr-x 2 simon simon 4096 feb 20 18:58  Documentos
drwxr-xr-x 4 simon simon 4096 mar  8 16:05  Escritorio
drwxr-xr-x 2 simon simon 4096 mar  9 13:13  Imágenes
drwxr-xr-x 2 simon simon 4096 feb 20 18:58  Música
drwxr-xr-x 2 simon simon 4096 feb 20 18:58  Plantillas
drwxr-xr-x 2 simon simon 4096 feb 20 18:58  Público
drwx------ 3 simon simon 4096 feb 20 18:58  snap
drwxr-xr-x 2 simon simon 4096 feb 20 18:58  Vídeos
drwx------ 5 simon simon 4096 mar  7 17:17 'VirtualBox VMs'
simon@simfor:~$ 
```

### 1.2 cd 

El comando ***cd*** (change dir) es capaz de cambiar de directorio. Si se utiliza tal cual, sin ningún tipo de argumento, cambia a directorio de trabajo personal. Si se utiliza seguido de una ruta, cambia a directorio que se indica.

```
simon@simfor:~$ pwd
/home/simon
simon@simfor:~$ cd /etc
simon@simfor:/etc$ pwd
/etc
```

En ese caso, el usuario estaba en su directorio de trabajo, y ha "saltado" a directorio /etc.


### 1.3 mkdir


Se pueden crear directorios con el comando ***mkdir***. Por ejemplo, para crear una estructura de carpetas donde un estudiante guardará información sobre sus asignaturas según el siguiente esquema (parte en negrita):

![Estructura creada con el comando mkdir](/images/imagen2.png)



![Ejemplo de creación de un árbol de directorios en Linux](/images/imagen3.png)



## 5.2 Visualización de archivos.


Los comandos ***cat***, ***more*** y ***less*** sirven para mostrar el contenido de archivos de texto. La diferencia radica en cómo se muestra el contenido. A todos estos comandos hay que pasar como argumento el archivo que se quiere mostrar.
Se puede indicar una ruta, en caso de que el archivo que se desee mostrar no esté en el directorio actual.
***cat*** muestra por pantalla el contenido de un archivo y, cuando termina, el usuario está otra vez de vuelta a la línea de comandos. Por ejemplo:

```
simon@simfor:/etc$ cat /var/log/dmesg
```

Si se prueba el comando, se observará que es imposible ver todo el contenido de este archivo, porque ha pasado por pantalla muy rápido. Por eso cat se suele utilizar para visualizar el contenido de archivos pequeños.


El comando ***more*** hace lo mismo que cat, a diferencia que muestra el archivo pantalla a pantalla, es decir, llena de texto la pantalla y se espera a que el usuario pulse la tecla <espacio>

![Ejemplo de creación de un árbol de directorios en Linux](/images/imagen4.png)


El comando ***less*** es el más versátil de los tres, ya que permite mover hacia delante y hacia atrás dentro del archivo, utilizando los cursores o las teclas de

![](/images/imagen5.png)

En cualquier momento se puede interrumpir la visualización y volver al símbolo de sistema pulsando la letra **"q"**.

***head*** y ***tail*** permiten mostrar de forma parcial el contenido de un archivo. Como su nombre indica, ***head*** muestra las primeras líneas del archivo (la cabecera) y ***tail*** muestra las últimas líneas (la cola).



## 5.3 Edición de archivos.

El comando ***touch*** permite crear un archivo vacío. Por ejemplo, para crear el archivo prueba.txt dentro de muestro directorio:

![](/images/imagen6.png)


### Caracteres comodin
El carácter **"*"** se puede colocar en cualquier sitio. Por ejemplo, para mostrar todos los archivos que comienzan por la letra a y terminan por la letras s dentro del directorio / usr / bin:

```
$ ls /usr/bin/a*s
```


El símbolo **"?"** representa un carácter cualquiera. De este modo, la siguiente sentencia muestra todos los archivos de directorio /usr/bin cuyo nombre comienza por g, sigue cualquier carácter, a continuación sigue una o y termina con cualquier cadena de caracteres incluida la cadena vacía:

```
$ ls /usr/bin/g?o*
```


Los **[ ]** se utilizan de un modo parecido al carácter **"?"** aunque, a diferencia de éste, permiten especificar algo más. Por ejemplo **[adfg]** significa cualquiera de los caracteres **a, d, f o g**. **[a-z] *** representa cualquier cadena de caracteres que comienza con una letra en minúsculas.

![](/images/imagen7.png)



## 5.4 Copia y borrado de archivos

El comando ***cp*** sirve para copiar archivos. Se puede copiar un único archivo o muchos. Se pueden copiar tanto archivos como directorios. Por supuesto, se pueden utilizar los símbolos comodín. En el proceso de copia intervienen tres factores: el que se copia, la ruta de origen y la ruta de destino. No está de más recordar que las rutas pueden ser tan absolutas como relativas. La ruta de origen se especifica junto con lo que se desea copiar. Veamos un ejemplo:

```
cp /etc/hosts  /home/alumno/pruebas/

```
 
La sentencia anterior copia el archivo hosts, que se encuentra en el directorio **/etc** en directorio **/home/alumno/pruebas/**.



El comando ***mv*** sirve para dos cosas, para mover y cambiar de nombre. Se puede hacer cualquiera de las dos cosas por separado o ambas cosas al mismo tiempo. Por ejemplo:

```
$ mv mi_texto.txt carta.txt
```
le cambia el nombre a mi_texto.txt y pasa a llamarse carta.txt.

```
$ mv carta.txt  Documentos/
```

mueve el archivo carta.txt al directorio Documentos.

---

Se pueden hacer ambas cosas a la vez, mover y cambiar el nombre:

```
$ cd Documentos/
/Documentos$ mkdir correspondencia
/documentos$ mv carta.txt correspondencia/carta01.txt
```
En este caso, el archivo carta.txt se ha movido a la carpeta ~ / Documentos /correspondencia y además se le ha cambiado el nombre a carta01.txt

---

El comando rm: se utiliza para borrar archivos. Es importante destacar que estos archivos no se envían a una papelera así que **NO SE PUEDEN RECUPERAR UNA VEZ BORRADO.**

Ejemplo:

```
rm *.txt
```

Esta sentencia borra todos los archivos con la extensión txt de directorio actual.

Si queremos borrar el directorio y todos sus archivos añadiremos el parámetro **-r**

```
rm -r nombre_del_directorio
