# Aprende Git y Control de Versiones en la tercera  hora

Guia practica de comandos utilices para aprender en git.

## Contenido

- [Comando restore](#comando-restore)


---


## Comando restore

Objetivo es para deshacer los cambios en un archivo.

Tenemos cambios en un archivo ya en el area de staged y queremos sacarlo de nuevo a to staging
```bash
$ git restore  --staged nombre_archivo.py
```

## Comando grep

Si necesitamos buscar coincidencias de una palabra en el repositorio entonces se usa grep.
Supongamos que queremos buscar la definicion de una funcion llamada  obtener_promedio entonces:

```bash
$ git grep obtener_promedio
```
nos va a devolver una lista con todos las ocurrencias en el repositorio apra esta palabra.

En este ejemplo buscara todas las ocurrancias para la palabra help con espacios antes y despues de la palabra.
```bash
$ git grep -i '\shelp\s'
```
## Comando Blame

Sirve para obtener información en el repositorio de quien y cuando hizo un cambio.


```bash
$ git blame ./presentaciones.md
```
La respuesta nos muestra linea a linea en numero de commit el nombre del quien hizo el cambio, la fecha, el numero de linea del archivo y el cambio que se hizo en esa linea, como se muestra:

```bash
885f6310 (puroh  2025-04-21 00:43:14 -0500 196) ### [Puroh](https://github.com/p
uroh)
```

Con estos argumentos me trae la información de el commit  885f6310, y si quiero traer la información que habia en el commit anterior entonces al hash id le agrego ~1

```bash
$ git blame 885f6310~1 ./presentaciones.md
```
