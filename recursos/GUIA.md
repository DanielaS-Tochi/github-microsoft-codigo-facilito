# Guía rápida para usar Git y colaborar en este repositorio 🚀

Lo ideal es participar del bootcamp y aprender los pasos básicos de Git y GitHub. Sin embargo, si ya tienes conocimientos previos, aquí tienes una guía rápida para empezar a usar Git y colaborar en este repositorio:

## Clonar, modificar y actualizar

### 1. Clonar el repositorio (solo la primera vez)
En la terminal: 

```shell
git clone https://github.com/DanielaS-Tochi/github-microsoft-codigo-facilito.git
```

También puedes clonarlo desde Visual Studio Code o el IDE que prefieras.

### 2. Entrar a la carpeta del proyecto

```shell
cd github-microsoft-codigo-facilito
```

### 3. Crear una rama nueva con tu nombre

```shell
git checkout -b rama-tu-nombre
```

### 4. Agregar tus cambios

```shell
git add .
```

### 5. Hacer un commit (guardar cambios)

```shell
git commit -m "Escribí aquí qué hiciste"
```

### 6. Subir tu rama al repositorio

```shell
git push origin rama-tu-nombre
```

### 7. Crear un Pull Request (PR)

Entrá al repo:
👉 https://github.com/DanielaS-Tochi/github-microsoft-codigo-facilito

Te va a aparecer un cartel para hacer un Pull Request.

Completá el formulario y enviá.

### 8. Actualizar tu copia local con los cambios nuevos
Antes de empezar a trabajar:

```shell
git checkout main
git pull origin main
```

Si querés actualizar tu rama con lo último de main:

```shell
git checkout rama-tu-nombre
git merge origin/main
```

## ¿Y si mi copia es un _fork_?
Si en vez de clonar el repositorio original, has clonado un _fork_, tu copia tendrá configurada la dirección de seguimiento remoto apuntando a __tu__ repositorio.

> Un _fork_ es una versión independiente del repositorio original que suele utilizarse para crear proyectos que seguirán su propio rumbo. Un _fork_ crea un nuevo repositorio en GitHub que vivirá junto a los demás repositorios en tu cuenta.

Puedes verlo haciendo:

```shell
git remote -v
```

Lo que producirá una salida similar a:

```shell
origin	git@github.com:TU_USR/github-microsoft-codigo-facilito.git (fetch)
origin	git@github.com:TU_USR/github-microsoft-codigo-facilito.git (push)
```

¡Allí no existe ninguna referencia al repositorio original en `git@github.com:DanielaS-Tochi/github-microsoft-codigo-facilito.git`!
Tendremos que agregarla manualmente. 

Por convención, se mantiene el identificador `origin` para el fork y `upstream` para el repositorio del cual el fork proviene. Entonces haremos...

```shell
git remote add upstream git@github.com:DanielaS-Tochi/github-microsoft-codigo-facilito.git
```

Puedes volver a ejecutar `git remote -v`para corroborar que la nueva referencia ha sido establecida.

Ahora ya puedes actualizar el cLoN-dE-tU-fOrK con lo que hemos ido añadiendo, cambiando y eliminando por aquí. Sigue las instrucciones del paso __(8)__ reemplazando `origin`por `upstream`. El mismo reemplazo deberás hacer si deseas enviar los cambios de tu rama (solicita los permisos para hacerlo si te encuentras con que no los tienes, ya que no es habitual el _push_ desde un _fork_) como se explica en el paso __(6)__. ¡Ah!, por cierto, también debes actualizar el _fork_.


## Tips 🧠

Siempre trabajá en tu propia rama.

No pasa nada si te equivocás. Puedes borrar tu rama y volver a empezar.

Estamos para aprender entre todos 🙌