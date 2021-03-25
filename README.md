# ¿Cómo trabajar con todo esto?

La primera parte es la instalación y la creación de las dependencias necesarias. La segunda parte es el trabajo propiamente dicho.

A continuación una guía corta de todo lo que tiene que hacerse.

## Creación de una cuenta de Github
Lo primero es crear una cuenta en [Github](https://github.com/). Es recomendable elegir un nombre de usuario que luzca profesional.



## Instalación de Git y uso desde RStudio


Para la parte de instalación de Git en la computadora así como el establecimiento de las conexiones necesarias con Github puede consultar el excelente manual que aparece [aquí](https://cfss.uchicago.edu/setup/what-is-git/). Fue usado en un curso donde no se esperaban fuertes conocimientos previos de programación, por lo cual es muy completo y se puede seguir en orden sin ningún problema. La parte más complicada quizá sea el uso de la consola, pero no es tan diferente del uso habitual que ha hecho con la consola en *R* y *RStudio*. Si procede tal como se indica en el _manual_ mencionado, será capaz de crear y modificar repositorios de Github de manera local. El cómo se hace esto último desde RStudio se explica en la siguiente sección.



## Trabajo colaborativo

Una de las ventajas de usar esta herramienta es la posibilidad de tener control sobre los cambios que se hacen en trabajos colaborativos ya sea de manera sincrónica o asíncrona. Para ello, es conveniente seguir pautas que aseguren los mejores resultado, así que a continuación se indican los pasos a seguir para trabajar localmente una vez que se ha obtenido acceso al repositorio principal, habitualmente `main`. Ya que nos interesa incluir código ``LaTeX``, recomendamos visitar este [libro](https://bookdown.org/yihui/rmarkdown-cookbook/install-latex.html) donde se recomienda instalar Miktex y autorizar la instalación de paquetes _al vuelo_ ( _on the fly_) para que no haya errores de compilación.


### Pasos a seguir
  1. Abrir RStudio
  2. Abrir el proyecto en el cual se está trabajando. De preferencia use `File -> Open Project in New Session...` para trabajar en el directorio correcto que únicamente tiene cargados los documentos que necesitará.
  3. Ya que estamos en un proyecto enlazado a Github (esto se explica en el [Paso 2](https://cfss.uchicago.edu/setup/git-with-rstudio/)) del manual, pinchamos la flecha azul que aparece en la pestaña *Git* para hacer _pull_ de la última versión en línea de nuestro proyecto, es decir, descargamos los últimos cambios disponibles en el repositorio de Github.
  4. *Importante*. Pinchamos en el símbolo morado para crear una rama local en la cual trabajaremos.
  ![ramalocal01](images/ramalocal01.jpeg)
  
  La cual configuramos únicamente para trabajar de manera local como se muestra en la siguiente imagen.
  ![ramalocal02](images/ramalocal02.jpeg)
  
  Este paso lo hacemos para evitar problemas cuando haya cambios en la rama principal `main`. De preferencia, realizamos esta acción cada vez que iniciamos un nuevo proyecto. Para evitar errores más adelane, el nombre de nuestra rama no debe contener símbolos especiales, ni puntos, ni acentos ni espacios: se sugiere usar un nombre del tipo `rama_local` o bien `RamaLocal`.
  
  5. Realizamos todas las acciones y actualizaciones dentro de esta rama local.
  6.  Para hacer `commit` de los cambios realizados tenemos dos opciones.
 
      - La primera es hacerlo mediante la interfaz: Pinchamos a `Commit` dentro de la pestaña *Git* y escribimos los comentarios necesarios para explicar nuestro trabajo realizado en la ventana que se abre. Debemos asegurarnos de _seleccionar_ solo los archivos que deseemos actualizar.
      - La segunda opción es hacerlo mediante línea de comandos. Esto puede ser más rápido cuando hay muchos cambios. Para ello, en el menú `Tools -> Shell` abrimos una consola. En ella, primero escribimos
        ```
        git add .
        ```
       y damos enter para agregar todos los cambios. También se puede escribir el nombre de cada archivo cuyos cambios queremos añadir en lugar del punto, para ello escribiríamos un comando del tipo
       ```
       git add nuevo_archivo.pdf
       ```
       
       A continuación, describimos en qué consisten los cambios realizados (el `commit` propiamente) y para ello usamos el siguiente comando
       ```
       git commit -m "Mensaje de ejemplo"
       ```
       
  7. Junto al nombre de nuestra rama local `rama_local` en la pestaña *Git* aparece un triángulo que apunta hacia abajo, lo pinchamos y cambiamos a la rama principal `main`. Esto nos abrirá un mensaje que, si no hay errores, indicará que hemos cambiado a la rama principal.
  8. Abrimos una consola a partir del menú `Tools -> Shell`.
  9. Nuevamente hacemos _pull_ porque podría haber actualizaciones realizadas por otro colaborador. Para ello escribimos `git pull` en la consola que abrimos, o bien, pinchamos en la flecha verde que apunta hacia abajo (que dice `Pull`) de la pestaña `Git`.
  10. En la consola escribimos el siguiente comando
  ```
  git merge rama_local
  ```
  donde `rama_local` es el nombre que le asignamos a la rama local en la cual trabajamos. Esto se hace para _combinar_ nuestro trabajo local con la rama principal `main` antes de subir nuestras actualizaciones al repositorio. Ya podemos cerrar la consola.
  
  11. En caso de que haya actualizaciones después de _descargar_ la última versión del repositorio y de hacer `merge`, nuevamente hacemos ``Commit`` (ver Paso 6.) de los cambios que se hayan producido (también corregimos lo qe sea necesario). Note que estamos en la rama principal `main` del proyecto.

  12. A continuación, hacemos _push_ de nuestro trabajo. Esto se logra ejecutando en la consola el comando `git push`, o bien, pinchando la flecha verde que apunta hacia arriba (que dice `Push`) en la pestaña `Git`. Esto termina la actualización del repositorio.
  13. Eliminamos la rama local ejecutando en la consola el siguiente comando
  ```
  git branch -d rama_local
  ```
  Una vez hecho esto, cerramos la consola. Hacemos esto porque en la rama local se guardan los cambios y si por alguna actualización descargada en el paso 9 no coinciden con lo obtenido en la rama principal después del paso 12, podríamos obtener versiones no compatibles y generar errores en la versión final.
  
  14. Para concluir, cerramos el proyecto desde `File -> Close Project` antes de cerrar RStudio para evitar errores al cargar la interfaz en una próxima ocasión.
  15. Cuando reabra el proyecto una próxima vez, repita a partir del paso 4 para asegurar el mejor desempeño.



Hay manera de incluir `Python` dentro del reporte. Debe tener instalado `Python` en su equipo y utilizar la librería `reticulate`. Vea [aquí](https://bookdown.org/yihui/rmarkdown-cookbook/eng-python.html) por ejemplo.
