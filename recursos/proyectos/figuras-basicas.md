# Figuras Basicas

modulo que graficara figuras basicas con `prints`

## objetivo

tratar de realizar las siguientes tareas:
crear o usar `pull-request`, `issues`, `github-actions`, `proyects`, `labels`, `milestones`, `workflows`, `tokens` entre otros

link del proyecto: [Figuras basicas](https://github.com/tomySinCodigo/practica_figuras_basicas/projects?query=is%3Aopen) vista **BOARD**

![Image](https://github.com/user-attachments/assets/af0072eb-a26f-4ef6-b8b3-f3c22e5b182d)

mas informacion del proyecto en la [wiki](https://github.com/tomySinCodigo/practica_figuras_basicas/wiki)


## Modulo - como usar

primero importamos la clase `Draw` del modulo `figures`

```python
from figures import Draw
draw = Draw()
```

para dibujar un rectangulo de largo 7 y de alto 3

```python
fig = draw.rectangle(width=7, height=3)
print(fig)
```

produce:

```python
* * * * * * *                            
*           *
* * * * * * *
```

para que este lleno usamo el parametro `outline=False`

```python
fig2 = draw.rectangle(7, 3, outline=False)
print(fig2)
```

produce:

```python
* * * * * * *
* * * * * * *
* * * * * * *
```

---

## Tareas

- [X] crear un proyecto
	- [x] agregar colaboradores
	- [x] asignar issues
	- [x] cerrar issues
	- [x] crear vistas (layouts)
	- [x] crear campos adicionales para la tabla del proyecto
- [x] crear issues
	- [x] linea (horizontal, vertical y oblicua)
	- [x] rectangulo
	- [x] cuadrado
	- [x] crear template para los issues
		- [x] para nueva caracteristica
		- [x] para corregir errores
- [x] crear `milestones` para  lineas
- [x] crer un test de la salida de las funciones
- [x] hacer el uso de alguna libreria de marketplace
- [x] crear un PAT
- [x] crear workflows
	- [x] para realizar el test
	- [x] crear un `artifact`
	- [x] crear una `discussion` usando un workflow y PAT
- [x] agregarle una wiki


## workflows realizados
### ejecutar `test` y generar como `artifact`

![Image](https://github.com/user-attachments/assets/bc9566d5-8092-48e7-89f6-32bb9d45411f)

generando el siguiente resultado del `test` en el archivo `salida_test.txt`

```cmd
TEST
autor: tomySinCodigo

Linea horizontal:
++++++++

Linea vertical:
+
+
+
+
+
+
+
+

Rectangulo:
+ + + + + + + + + + 
+ + + + + + + + + + 
+ + + + + + + + + + 
+ + + + + + + + + + 

Cuadrado:
+ + + + + + + + 
+             + 
+             + 
+             + 
+             + 
+             + 
+             + 
+ + + + + + + + 

Linea diagonal ascendente:
    +
  +
+

Linea diagonal descendente:
+
  +
    +
      +
        +

```

### ejecutando el workflow para generar una `discussion`

el cual generara una discusion con los ultimos 5 commits

![Image](https://github.com/user-attachments/assets/e05ef955-f6f7-46c9-a8b4-536df913b84a)

