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

     * `git log --graph --oneline`: Genera un gráfico del historial de los commits del repositorio, permitiendo ver el flujo de trabajo. 

    ```
    *   c5e96c9 (origin/styled) Resolucion de conflictos, mantenemos styled
    |\
    | * 0d59323 (tag: htmlify, origin/htmlify) style: Cambia el formato a estilo HMTL en git-nuestro.md
    * | 4dc63c8 docs: Puntos 11, 12 y 13 del enunciado
    * | c76ee25 (tag: styled) style: Cambio de estilo en el formato de palabras claves
    |/
    * 312b635 (tag: inicial) first commit
    ```

- El merge del paso 26, ¿Podría ser fast forward? ¿Por qué?
    
    * Sí, porque la rama main no se había modificado nuevamente desde el ultimo merge con styled. Aunque un `merge --no-ff` ofrece claridad en el historial al tener que hacer un commit ya que el fast forward no crea un commit.

- ¿Qué comando o comandos utilizaste en el paso 27?

    * `git reset --soft HEAD~1`: deshace el merge y mantiene los cambios en el working copy.

- ¿Qué comando o comandos utilizaste en el paso 28?

    * `git restore --stage y git restore <archivo>`

- ¿Qué comando o comandos utilizaste en el paso 29?

    * `git branch -D title`

- ¿Qué comando o comandos utilizaste en el paso 30?

    * `git reflog`
    * `git checkout <hash>`
    * `git switch -c title` 
    * `git checkout main` 
    * `git merge --no-ff title`

    Con `git reset --hard <hash>` para rehacerlo podría haberlo hecho pero no quedaría ningún commit como referencia en el historial.

- ¿Qué comando o comandos usaste en el paso 32?

    * `git log --oneline` para buscar el hash
    * `git checkout <hash>` para mover el HEAD.

- ¿Qué comando o comandos usaste en el punto 33?

    * `git switch -` para llevar el HEAD al estado actual.
