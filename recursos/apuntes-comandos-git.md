<img src="https://www.freecodecamp.org/news/content/images/size/w2000/2024/04/freecodecampl-github.png" alt="¿Qué es un commit?" style="height:120px; width:100%; object-fit:cover;">

# 🧠 Comandos básicos de Git

Guía rápida con los comandos esenciales para trabajar con Git de forma eficiente.


## 📚 Índice de Contenidos

1. [¿Qué es un commit?](#-qué-es-un-commit)
2. [Estado y seguimiento](#-estado-y-seguimiento)
3. [Añadir archivos](#-añadir-archivos)
4. [Realizar commits](#-realizar-commits)
5. [Ver historial](#-ver-historial)
6. [Ramas](#-ramas)
7. [Repositorios remotos](#-repositorios-remotos)
8. [Reset y limpieza](#-reset-y-limpieza)
9. [Inicialización de repositorios](#-inicialización-de-repositorios)
10. [Guardar cambios temporalmente (stash)](#-guardar-cambios-temporalmente-stash)
---

## 📄 ¿Qué es un commit?

Un **commit** en Git es una instantánea de los cambios realizados en el proyecto en un momento específico. Representa un punto en el historial del repositorio al que puedes regresar si es necesario.

Cada commit incluye:

- Un mensaje descriptivo ✏️
- Un identificador único (`hash`) 🔐

> 💡 **Consejo:** Escribe mensajes claros y específicos para que tus commits sean útiles a largo plazo.

---

## 📂 Estado y seguimiento

| Comando                     | Descripción                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| `git status`               | Muestra el estado actual del repositorio: archivos modificados o no seguidos |
| `git diff`                 | Muestra los cambios entre el working directory y el área de staging         |
| `git diff --staged`        | Muestra los cambios ya en staging antes del commit                          |

---

## ➕ Añadir archivos

| Comando                        | Descripción                                                                 |
|-------------------------------|-----------------------------------------------------------------------------|
| `git add <archivo>`           | Añade un archivo específico al área de staging                             |
| `git add .`                   | Añade todos los cambios del directorio actual al staging                   |
| `git add -A` / `--all`        | Añade archivos modificados, nuevos o eliminados al área de staging         |

---

## ✅ Realizar commits

| Comando                     | Descripción                                                                 |
|----------------------------|-----------------------------------------------------------------------------|
| `git commit -m "mensaje"`  | Crea un commit con un mensaje descriptivo                                  |
| `git commit --amend`       | Modifica el último commit (mensaje o contenido) ⚠️ si aún no hiciste `push` |
| `git show [hash]`          | Muestra detalles de un commit específico (por defecto, el último)          |

---

## 🕓 Ver historial

| Comando                          | Descripción                                          |
|----------------------------------|------------------------------------------------------|
| `git log`                        | Muestra el historial completo de commits             |
| `git log --oneline`             | Muestra el historial en formato compacto             |
| `git log --oneline --graph`     | Muestra el historial como un gráfico de ramas        |

---

## 🌱 Ramas

| Comando                             | Descripción                                             |
|------------------------------------|---------------------------------------------------------|
| `git branch`                       | Lista todas las ramas y muestra la rama actual         |
| `git checkout <rama>`             | Cambia a otra rama existente                            |
| `git checkout -b <nueva-rama>`    | Crea y cambia a una nueva rama                          |
| `git merge <rama>`                | Fusiona la rama indicada con la rama actual             |

---

## 🌀 Repositorios remotos

| Comando                    | Descripción                                                        |
|---------------------------|--------------------------------------------------------------------|
| `git clone <url>`         | Clona un repositorio remoto                                       |
| `git remote -v`           | Muestra las URLs de los remotos (fetch y push)                    |
| `git push`                | Envía los commits locales al repositorio remoto                   |
| `git pull`                | Descarga y fusiona los últimos cambios del repositorio remoto     |

---

## 🧼 Reset y limpieza

| Comando                  | Descripción                                                                     |
|-------------------------|---------------------------------------------------------------------------------|
| `git reset <archivo>`   | Quita el archivo del staging sin perder los cambios locales                    |
| `git reset --hard`      | Restaura el working directory al último commit (⚠️ se pierden los cambios no guardados) |

---

## 🚀 Inicialización de repositorios

| Comando      | Descripción                                             |
|--------------|---------------------------------------------------------|
| `git init`   | Inicializa un nuevo repositorio Git en el directorio actual |

---

## 💾 Guardar cambios temporalmente (stash)

| Comando              | Descripción                                                              |
|----------------------|--------------------------------------------------------------------------|
| `git stash`          | Guarda cambios temporales no listos para commit                          |
| `git stash list`     | Muestra los cambios guardados en el stash                                |
| `git stash apply`    | Aplica los últimos cambios guardados sin eliminarlos                     |
| `git stash pop`      | Aplica y elimina los últimos cambios guardados                           |
| `git stash drop`     | Elimina una entrada específica del stash                                 |
| `git stash clear`    | Borra todas las entradas del stash                                       |

---

> ✨ Esta guía está pensada como referencia rápida. ¡Personalízala según tu flujo de trabajo!
