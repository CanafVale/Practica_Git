#Práctica GIT - Ana B.F.
Este repo contiene la práctica de Git.

- ¿Qué comando utilizaste en el paso 11? ¿Por qué?

    * `git reset --hard HEAD~1` :  Este comando se utiliza para deshacer el último commit y así perder los últimos cambios realizados desde dicho commit. 
    Indicamos `HEAD~1` para volver exactamente 1 paso hacia atrás. El número indica el número de pasos. Finalmente `--hard` es un modificador de `git reset` que hace que cualquier modificación no guardada se borre. 

- ¿Qué comando o comandos utilizaste en el paso 12? ¿Por qué?

    * `git reflog`: para poder obtener del historial el hash del commit borrado, que usaremos después en el `reset`
    * `git reset --hard <hash>` : indicamos el hash localizado para así poder recuperar el commit y recuperando su contenido y su estado.

- El merge del paso 13, ¿Causó algún conflicto? ¿Por qué?

    * Realizamos `git merge main`
    * No causa conflicto porque desde el último commit no hemos realizado cambios en main, y main a su vez ya tenía lo mismo que styled.

- El merge del paso 19, ¿Causó algún conflicto? ¿Por qué?

    * Sí, este `merge` sí que genera conflicto. Hemos hecho un merge de `htmlify` en `styled` (es decir, `styled` absorbe a `htmlify`)
    * Como hemos creado `htmlify` desde `main` y a su vez `styled` tenía las mismas líneas que `main`, ahora esas líneas están duplicadas y causa conflicto.

- El merge del paso 21, ¿Causó algún conflicto? ¿Por qué?

    * No, porque hemos creado la nueva rama desde `main`, que tiene las mismas líneaws que `styled` y ahora mismo `styled` tiene ya lo mismo que `htmlify`. 
    Ese `merge` no genera conflictos.

- ¿Qué comando o comandos utilizaste en el paso 25?

    * He usado `git log --oneline --graph --all`. 
    
    * `git log` muestra el historial de commits. 
    El modificador `--oneline` muestra cada commit en una línea; `--graph` dibuja el gráfico de ramas y de merges y `--all` muestra todas las ramas, no solo aquella en la que actualmente estamos.

    * Recibo en la consola:
    ```
    *2cca9e7 (title) Añadido título
    *cbb23d7 (HEAD -> main, styled) Aplicar cursivas al git-nuestro
    | *d6ef94b (htmlify) Paso 18
    | *333d6c8 Poner formato HTML a fichero git-nuestro.md
    |/
    *5ab850a (origin/main) Initial git con poema
    ```
    * Las ramas se indican entre paréntesis y los merges con `|` y `\`.

- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
    
    * Sí, porque la rama main no se había vuelto a modificar desde el ultimo merge con styled. 
    * Sin embargo, como el fast forward no genera un commit, mejor un no fast forward. 
    
- ¿Qué comando o comandos utilizaste en el paso 27?

    * `git reset --soft HEAD~1`: a diferencia del `HARD` que hemos hecho en el paso 11, utilizar el modificador `--soft` deshace el merge y mantiene los cambios en el working copy.

- ¿Qué comando o comandos utilizaste en el paso 28?

    * `git reset --hard`: no tenía claro qué había que descartar, porque solo pone "Descartar los cambios", así que voy a suponer que se quiere descartar todo, tanto los cambios en el fichero como lo que no se haya hecho un commit ya

- ¿Qué comando o comandos utilizaste en el paso 29?

    * `git branch -D title`

- ¿Qué comando o comandos utilizaste en el paso 30?

    * Como en el paso 27 deshicimos el merge con `git reset --soft HEAD~1`, ahora podemos volver a hacerlo.

    * `git reflog`, y listamos para encontrar el hash
    * `git checkout <hash>`, en mi caso `git checkout -b title 2cca9e7`
    Pero me da este error:

    ```
    $ git checkout -b title 2cca9e7
    error: The following untracked working tree files would be overwritten by checkout:
        README.md
    Please move or remove them before you switch branches.
    Aborting
   ```
    Tenemos que hacer un commit de README.md para no perder los cambios y luego ya seguimos.

    * `git switch -c title` 
    * `git checkout main` 
    * `git merge --no-ff title`
    
    Se me queda en estado `MERGING` así que forzamos:
    * `git commit -m "Rehacer el merge`

- ¿Qué comando o comandos usaste en el paso 32?

    * `git log --oneline --rever` para buscar el hash, pero empezando por el más antiguo
    * `git checkout <hash>` para mover el HEAD.

- ¿Qué comando o comandos usaste en el punto 33?

    * `git checkout main` para volver a la situación actual.
