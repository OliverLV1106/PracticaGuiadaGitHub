# Práctica guiada de Git

## 1. Creación de la carpeta y archivos

Creamos la carpeta `prueba_git`.

![Creación de la carpeta](image.png)

Creamos el archivo `texto.txt` con `nano` e introducimos las tres palabras. Para guardar, pulsamos `Ctrl + O` y, para salir, `Ctrl + X`.

![Edición de texto.txt](image-1.png)

![Contenido de texto.txt](image-2.png)

También creamos un script con el código necesario para listar el contenido del directorio.

![Creación del script](image-3.png)

Le damos permiso de ejecución y lo probamos. El script muestra el listado del directorio en el que nos encontramos.

![Permiso y ejecución del script](image-4.png)

## 2. Inicialización del repositorio: `init` y `status`

Dentro de la carpeta que hemos creado, inicializamos Git. Se crea el directorio oculto `.git`, que contiene la información del repositorio.

Con `git status` podemos comprobar que los dos archivos todavía no están siendo gestionados por Git.

![Inicialización y estado del repositorio](image-5.png)

Podemos cambiar el nombre de la rama principal para que, en lugar de aparecer `master`, aparezca el nombre que queramos. Para volver al nombre anterior, basta con ejecutar de nuevo el comando correspondiente.

![Cambio del nombre de la rama](image-6.png)

## 3. Añadir y confirmar archivos: `add` y `commit`

Añadimos el script con `git add` y consultamos el estado del repositorio. El script ya aparece preparado para ser confirmado, mientras que el archivo de texto todavía no está añadido. Si aparece un mensaje de error al ejecutar el comando, comprobamos que hemos escrito correctamente la orden y la ruta.

![Añadir el script](image-7.png)

Si volvemos a ejecutar `git status`, veremos que el archivo de texto sigue pendiente de añadir. Los commits se registran con el nombre de usuario y el correo electrónico configurados en Git.

![Estado y configuración del usuario](image-8.png)

Realizamos un `commit` para guardar una versión del estado actual de los archivos en el repositorio.

![Confirmación de los cambios](image-9.png)

Si hay muchos cambios o queremos escribir un mensaje más largo, podemos utilizar el método mostrado en la captura.

![Mensaje de commit más largo](image-10.png)

Añadimos correctamente `texto.txt` al repositorio y comprobamos que ya está preparado o sincronizado con el estado confirmado, según el comando utilizado.

![Añadir el archivo de texto](image-11.png)

## 4. Modificación de archivos

Modificamos el archivo y ejecutamos `git status`. Git nos avisa de que se han realizado cambios que todavía no se han añadido a la siguiente confirmación.

![Estado después de modificar un archivo](image-12.png)

Volvemos a ejecutar `git add` para preparar los cambios y poder guardarlos en un nuevo commit.

![Añadir los cambios](image-13.png)

## 5. Consultar información: `log`, `show` y `status`

Estos comandos permiten consultar información sobre el repositorio y sus versiones.

Con `git log` podemos ver el historial de commits. Con `git show` podemos consultar los detalles de un commit concreto, incluidos los cambios realizados.

![Información de un commit](image-14.png)

También podemos consultar información adicional sobre las fechas, las versiones y el autor de los cambios.

![Más información del repositorio](image-15.png)

## 6. Consultar diferencias: `diff`

Modificamos el archivo y ejecutamos `git diff` para ver las diferencias entre el contenido actual y la versión registrada. Habitualmente, las líneas añadidas aparecen en verde y las eliminadas en rojo; las líneas de contexto ayudan a localizar los cambios.

![Diferencias entre versiones](image-16.png)

Después de ejecutar el commit, Git muestra un resumen de los cambios, como el número de archivos modificados y las líneas añadidas o eliminadas.

![Resumen del commit](image-17.png)

Si volvemos a modificar el archivo y ejecutamos `git diff`, veremos las diferencias que todavía no se han añadido al área de preparación.

![Nuevas diferencias](image-18.png)

## 7. Ignorar archivos: `.gitignore`

Creamos el archivo `.gitignore` para indicar qué archivos debe ignorar Git. En este caso, configuramos reglas para ignorar los archivos que terminan en `.class` y los que terminan en `~`.

![Creación del archivo .gitignore](image-19.png)

Creamos dos archivos nuevos y movemos el archivo `Hola.java`.

![Creación y movimiento de archivos](image-20.png)

Comprobamos que los archivos que coinciden con las reglas de `.gitignore` no aparecen como archivos pendientes en el estado del repositorio.

![Comprobación de archivos ignorados](image-21.png)

Añadimos los archivos pendientes. Lo hacemos en dos fases porque había un pequeño error en el archivo `.gitignore`.

![Primera fase de la corrección](image-22.png)

![Segunda fase de la corrección](image-23.png)

Al final, comprobamos qué archivos quedan en el repositorio.

![Resultado final de los archivos](image-24.png)

## 8. Etiquetas y gestión de versiones: `tag`, `log` y `checkout`

Ejecutamos `git log`, copiamos el identificador de uno de los commits y utilizamos `git show` para consultar la información de esa versión.

![Consultar un commit del historial](image-25.png)

Con `git tag` podemos asignar un nombre a un commit. Si no especificamos un commit, la etiqueta se asigna normalmente al commit actual (`HEAD`).

![Crear una etiqueta](image-26.png)

Ahora podemos consultar el commit utilizando el nombre de la etiqueta en lugar de escribir su identificador completo.

![Consultar un commit mediante una etiqueta](image-27.png)

Podemos cambiar a una versión anterior utilizando `git checkout` y el nombre de la etiqueta o el identificador del commit. Para volver a trabajar en la rama principal, debemos cambiar a esa rama. En versiones actuales de Git también se puede utilizar `git switch`.

![Cambiar entre versiones](image-28.png)

## 9. Trabajo con ramas

Creamos una rama nueva llamada `prueba`.

![Crear una rama](image-29.png)

Listamos las ramas para comprobar que se ha creado correctamente.

![Listar las ramas](image-30.png)

Al mostrar las ramas, podemos ver `prueba` y un asterisco junto a la rama en la que estamos trabajando actualmente.

![Identificar la rama activa](image-31.png)

Utilizamos `git switch` para cambiar de rama. El asterisco indica en cuál estamos trabajando.

![Cambiar de rama](image-32.png)

A partir de este momento, los nuevos commits se realizarán en la rama seleccionada.

![Rama seleccionada](image-33.png)

Modificamos el archivo `Hola.java`.

![Modificar Hola.java](image-34.png)

Después de modificar el archivo, realizamos el commit y añadimos una etiqueta. Al ejecutar `git log`, podemos comprobar que el commit se ha creado en la rama `prueba`.

![Commit en la rama prueba](image-35.png)

Volvemos a la rama principal y comprobamos que `Hola.java` no contiene la línea que añadimos en la rama `prueba`. Esto demuestra que los cambios de cada rama se mantienen separados hasta que se combinan.

![Comprobar el contenido de la rama principal](image-36.png)

Si queremos conservar los cambios de `prueba` en la rama principal, podemos fusionarlas con `git merge`.

![Fusionar las ramas](image-37.png)

## 10. Eliminar archivos y dejar de seguirlos

Con `git rm` podemos eliminar un archivo del directorio de trabajo y preparar su eliminación para el próximo commit. Después, confirmamos el cambio con `git commit`.

![Eliminar archivos](image-38.png)

Si queremos que Git deje de seguir un archivo sin borrarlo del directorio de trabajo, podemos utilizar `git rm --cached` y confirmar el cambio.

![Dejar de seguir un archivo](image-39.png)

## 11. Repositorios remotos: GitHub

Para clonar un proyecto alojado en GitHub, utilizamos `git clone` seguido de la URL del repositorio. Git descarga el proyecto y crea una carpeta local con su contenido.

En este ejemplo, aparece el directorio `HolaED`.

![Clonar un repositorio de GitHub](image-40.png)
