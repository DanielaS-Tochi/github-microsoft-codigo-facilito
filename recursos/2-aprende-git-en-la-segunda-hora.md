# Aprende Git y Control de Versiones en la segunda hora

Guia practica de comandos utilices para aprender en git.

## Contenido

- [Comando Bisect](#comando-bisect)
- [Guía de cómo deshacer el último commit con git](#guía-de-cómo-deshacer-el-último-commit-con-git)
- [Comando cherry-pick](#cherry-pick)

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
$ git reset –soft HEAD~1
```
• Para descartar cambios:
```bash
$ git reset –hard HEAD~1
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