# Aprende Git y Control de Versiones en la segunda hora

Guia practica de comandos utilices para aprender en git.

## Contenido

- [Comando Bisect](#comando-bisect)
- [Guía de cómo deshacer el último commit con git](#guía-de-cómo-deshacer-el-último-commit-con-git)
- [Comando cherry-pick](#cherry-pick)
- [Comando diff](#comando-diff)
- [Comando show](#comando-show)

---


## Comando Bisect
¿Hay un bug en tu código y no sabes qué commit lo introdujo?

¡Aprende a utilizar git bisect! Pasos:

1. Inicia el proceso
2. Marca un commit con el error
3. Busca un commit sin bug(hay que hacer un rango de commmits)
4. Automatiza ir probando commits
5. Y al final te dice el commit que introdujo el problema:

```bash
# iniciamos el proceso para encontrar el commit culpable
$ git bisect start

# marcamos si el commit actual tiene el error y nos movemos al siguiente
$ git bisect bad

# indicamos el commit que no tenia el fallo y marcamos el rango para verificar commits
$ git bisect good 587d364d

# se inicia el proceso
Bisecting: 16 revisions left to test after this (roughly 4 steps)
[92e11f055a73eb61ca5c17657d84587d364d] Update toutube count
```


## Guía de cómo deshacer el último commit con git

Si no has hecho push:

• Para conservar cambios:
```bash
$ git reset –soft HEAD~1 # deshace el commit, pero mantiene los cambios realizados en el area de staging
```
• Para descartar cambios:
```bash
$ git reset –hard HEAD~1 # desaparece totalemnte y son irrecuperables los cambios
```
• Para modificar el commit (mensaje o agregar cambios):
```bash
$ git commit –amend -m “Nuevo mensaje”
```
### Si ya has hecho push:

• git revert para crear un nuevo commit que deshace los cambios. Si hay conflictos, prepárate para resolverlos.

• git log para obtener el hash del commit que deseas revertir.

### Más avanzado:

• git rebase -i para modificar tu historial de commits localmente. Puedes reorganizar, combinar, editar o eliminar commits.

• Luego ejecuta git push –force-with-lease

• ⚠️ Precaución: Sólo usa rebase y push forzado en ramas donde seas el único colaborador o en situaciones donde todos los colaboradores estén informados y de acuerdo con reescribir la historia.



```bash
# con ~4 se devuelve 4 commits, -i significa interactivo, se parte desde 4 commits atras y se puede seleccionar los commits que se quieren para la nueva rama
$ git rebase -i HEAD~4 
```

```bash
# Se mueve tres commits atras desde el HEAD actual
$ git branch -f main HEAD~3
```


```bash
# para devolver una rama local
$ git reset HEAD~1 
```
```bash
# para devolver una rama remota
$ git revert HEAD 
```

## Cherry-pick
El comando git cherry-pick copia uno o más commits específicos de una rama a otra. Esto permite aplicar cambios seleccionados sin fusionar ramas completas. Es útil para trasladar correcciones o características puntuales entre ramas.

```bash
# añade los commits a la rama donde estoy parado
$ git cherry-pick <Commit1> <Commit2> <...> 
```


## Comando diff

Partiendo del coamndo diff
```bash
# añade los commits a la rama donde estoy parado
$ git diff
```
Se obtiene como respuesta:

```bash
diff --git a/1-aprende-git-en-una-hora.md b/1-aprende-git-en-una-hora.md
index 3e40ad3..40474b2 100644
--- a/1-aprende-git-en-una-hora.md
+++ b/1-aprende-git-en-una-hora.md
@@ -61,7 +61,10 @@ git checkout -b nueva-rama
 
 ```bash
 git log           # Ver historial
+git log -n 5      # ver los ultimos 5 commits
 git log --oneline # Ver resumen
+git log --oneline -n 3 # combinacion y resumen
+git log --format=[short full medium] # elegir uno segun cuanta inofrmación se necesita
 git revert <commit-id>
 ```

En esta linea se tiene en staged el archivo a/1-aprende-git-en-una-hora.md, y se tienen nuevos cambios en b/1-aprende-git-en-una-hora.md
```bash
 diff --git a/1-aprende-git-en-una-hora.md b/1-aprende-git-en-una-hora.md
```

Estos son los identificadores de la rama que se van a fusionar
```bash
index 3e40ad3..40474b2 100644
```

Con los --- esta el archivo staged en git y con +++ es el archivo que contiene los cambios para hacer commit
```bash
--- a/1-aprende-git-en-una-hora.md
+++ b/1-aprende-git-en-una-hora.md
```

En el archivo a se tiene que en la linea 61 le siguen 7 lineas, pero git ha detectado cambios entonces detecta que en el archivo b despues de la linea 61 hay 10 lineas, es decir 3 extra.
```bash
@@ -61,7 +61,10 @@ git checkout -b nueva-rama
```


## Comando show

Nos devuelve informacion de un commit, si lo pasamos sin argumentos nos devuelve la inforamción del ultimo commit.

Muestra información como si fuera un [diff](#comando-diff)
```bash
git show 3fd578da9449b679cbb10a63041a0a655684d1b5
```

## Solucioanr conflictos

Una forma para solucionar conflictos es el comando checkout mas una de las dos opciones: --ours, --theirs.

El error tiene dos opciones, persistir los cambios de la rama padre (HEAD) o de la rama hijo, entonces se revisa el codigo y se elige que cambios dejar.

En este comando se persinten los cambios del hijo en el archivo nombre_archivo.py
```bash
git checkout --theirs nombre_archivo.py
```

Despues agregar los cambios con un commit.

