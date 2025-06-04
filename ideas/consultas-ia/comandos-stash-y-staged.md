## Comandos stash y staged (Gemini Advanced 2.0)

Vamos a hablar de los comandos stash y staged de Git con algunos ejemplos para que quede bien claro.

### git stash
El comando ```git stash``` se utiliza para guardar temporalmente los cambios que tienes en tu directorio de trabajo y en el área de staging, pero que aún no quieres commitear. Es útil cuando necesitas cambiar de rama rápidamente para trabajar en otra cosa, pero no quieres hacer un commit de un trabajo a medio hacer.

### ¿Qué guarda ```git stash```?

Por defecto, ```git stash``` guarda:

- **Cambios realizados en archivos rastreados:** Modificaciones que has hecho en archivos que Git ya está controlando.
- **Cambios que ya están en el área de staging:** Archivos que has añadido con git add.

Opcionalmente, puedes configurar git stash para que también guarde archivos nuevos no rastreados o incluso archivos ignorados.

### Ejemplos:

1. Guardar cambios sin commitear:

Supongamos que estás trabajando en un archivo llamado ```mi_archivo.txt``` y has hecho algunas modificaciones. También has añadido este archivo al área de staging con ```git add mi_archivo.txt```. De repente, necesitas cambiar a otra rama para corregir un error urgente. Puedes usar ```git stash``` para guardar tus cambios:

```
Bash

git stash
```

Esto guardará tus cambios y tu directorio de trabajo volverá al estado del último commit en la rama actual. Puedes verificarlo con ```git status```, que debería mostrar un directorio de trabajo limpio.

2. Listar los stashes guardados:

Puedes tener múltiples stashes guardados. Para ver una lista de ellos, usa:

```
Bash

git stash list
```

Verás una lista como esta:

```
stash@{0}: WIP on main: 5c1abff Mi trabajo en progreso
stash@{1}: WIP on develop: 234defg Otro cambio
```

Cada stash tiene un identificador (como ```stash@{0}```) y una descripción (por defecto, incluye la rama y el commit en el que se creó). Puedes añadir una descripción personalizada al crear el stash.

3. Aplicar un stash:

Para recuperar los cambios guardados, puedes usar ```git stash apply```. Por defecto, aplica el stash más reciente (```stash@{0}```):

```
Bash

git stash apply
```

Si quieres aplicar un stash específico, puedes usar su identificador:

```
Bash

git stash apply stash@{1}
```

Esto intentará aplicar los cambios guardados en el stash seleccionado a tu directorio de trabajo actual. Los cambios se aplicarán, pero el stash se mantendrá en la lista.

4. Aplicar y eliminar un stash:

Si estás seguro de que ya no necesitas el stash después de aplicarlo, puedes usar ```git stash pop```. Esto aplica el stash más reciente (o el especificado) y luego lo elimina de la lista de stashes:

```
Bash

git stash pop
```

O para un stash específico:

```
Bash

git stash pop stash@{0}
```

5. Guardar cambios con un mensaje:

Para que sea más fácil recordar qué contiene un stash, puedes añadir un mensaje al crearlo:

```
Bash

git stash save "Mi trabajo en progreso antes de cambiar de rama"
```

Este mensaje aparecerá en la lista de stashes.

### git staged

El término ```staged``` en Git se refiere a los cambios que han sido añadidos al área de staging (también conocida como el "índice"). El área de staging es una capa intermedia entre tu directorio de trabajo y el repositorio Git. Aquí es donde preparas tus cambios para el próximo commit.

### ¿Qué significa que un archivo esté "staged"?

Cuando modificas un archivo rastreado o creas un archivo nuevo, estos cambios inicialmente están en tu directorio de trabajo y no están rastreados (en el caso de archivos nuevos) o están marcados como modificados. Para incluir estos cambios en tu próximo commit, necesitas moverlos al área de staging usando el comando ```git add```.

### Ejemplos:

1. Ver el estado de los archivos:

El comando ```git status``` te muestra qué archivos están staged, cuáles no lo están y cuáles no están rastreados:

```
Bash

git status
```

Verás secciones como "Changes to be committed" (archivos staged) y "Changes not staged for commit" (archivos modificados no staged).

2. Stagear un archivo modificado:

Si has modificado un archivo llamado ```otro_archivo.txt```, ```git status``` lo mostrará en la sección "Changes not staged for commit". Para stagearlo, usa:

```
Bash

git add otro_archivo.txt
```

Después de esto, ```git status``` mostrará ```otro_archivo.txt``` en la sección "Changes to be committed".

3. Stagear todos los cambios:

Para stagear todos los cambios en archivos rastreados y cualquier archivo nuevo, puedes usar:

```
Bash

git add .
```

Sin embargo, ten cuidado con este comando, ya que stageará todo lo que no esté ignorado por tu archivo ```.gitignore```.

4. Ver los cambios staged:

Para ver exactamente qué cambios has stageado, puedes usar:

```
Bash

git diff --staged
```

Esto mostrará las diferencias entre el último commit y lo que está actualmente en el área de staging.

5. Unstagear un archivo:

Si has stageado un archivo por error y quieres removerlo del área de staging, puedes usar ```git reset HEAD <archivo>```:

```
Bash

git reset HEAD otro_archivo.txt
```

Esto dejará los cambios en tu directorio de trabajo, pero los removerá del área de staging.

**En resumen:**

- ```git stash``` es para guardar temporalmente cambios no commiteados para poder trabajar en otra cosa y volver a ellos más tarde.
- ```staged``` describe el estado de los cambios que han sido preparados (con ```git add```) para ser incluidos en el próximo commit.

Piensa en el área de staging como una sala de espera para tus cambios antes de que sean oficialmente guardados en la historia de tu repositorio con un commit. ```git stash``` es como poner tus cambios actuales en un cajón para poder limpiar tu espacio de trabajo temporalmente.
