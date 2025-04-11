# Aprende Git y Control de Versiones en una Hora

Este es un resumen práctico del tutorial original publicado por Juan C. Guaña en freeCodeCamp:  
🔗 [Ver tutorial completo](https://www.freecodecamp.org/espanol/news/aprende-git-y-control-de-versiones-en-una-hora/)

## Contenido

- [¿Qué son Git y el control de versiones?](#qué-son-git-y-el-control-de-versiones)
- [Configurando tu Git Bash](#configurando-tu-git-bash)
- [Inicializando tu repositorio](#inicializando-tu-repositorio)
- [Haciendo tu primer commit](#haciendo-tu-primer-commit)
- [Creando una rama](#creando-una-rama)
- [Regresando a un commit](#regresando-a-un-commit)
- [Repositorio remoto y sincronización](#repositorio-remoto-y-sincronización)

---

## ¿Qué son Git y el control de versiones?

Git es un sistema de control de versiones distribuido que permite gestionar los cambios realizados en archivos y colaborar con otros.

## Configurando tu Git Bash

```bash
git config --global user.name "Tu Nombre"
git config --global user.email "tu@email.com"

# Verificar configuración
git config --global user.name
git config --global user.email
```

## Inicializando tu repositorio

```bash
mkdir primerospasosgit
cd primerospasosgit
touch index.html
git init
```

## Haciendo tu primer commit

```bash
git add .
git commit -m "Primer commit"
git status
```

## Creando una rama

```bash
git branch nueva-rama
git checkout nueva-rama

# O ambas en una línea
git checkout -b nueva-rama
```

## Regresando a un commit

```bash
git log           # Ver historial
git log --oneline # Ver resumen
git revert <commit-id>
```

## Repositorio remoto y sincronización

```bash
# Crear repositorio en GitHub, luego:
git remote add origin https://github.com/usuario/repositorio.git
git push -u origin master

# Para sincronizar cambios futuros:
git pull origin master
```

## 
```bash
git stash           # Guardar cambios temporales
git stash list      # muestra una lista de todos los cambios que has guardado temporalmente en el stash.
git stash apply     # aplica los cambios guardados en el stash al área de trabajo actual.
git stash clear     # elimina todos los stashes almacenados en el repositorio.
git stash pop       # revierte los cambios guardados en el stash

```

---
📚 **Créditos**: Este resumen está basado en el tutorial original publicado en freeCodeCamp por Juan C. Guaña.  
Consulta el artículo completo para más detalles y explicaciones:  
👉 [https://www.freecodecamp.org/espanol/news/aprende-git-y-control-de-versiones-en-una-hora/](https://www.freecodecamp.org/espanol/news/aprende-git-y-control-de-versiones-en-una-hora/)
