
<div align="center">
  <h1>Statistical programming with Python</h1>
</div>

<div align="center"> 
  <img src="https://raw.githubusercontent.com/karlbehrensg/programacion-dinamica-y-estocastica/master/readme_img/python.png" width="250">
</div>

# Itroduction

Statistical programming topics.

# Table of contents
- [Dynamic programming](#Dynamic-programming)
    - [Introduction to Dynamic Programming](#Introduction-to-Dynamic-Programming)
    - [Fibonacci optimization](#Fibonacci-optimization)
- [Statistics](#Statistics)
    - [Combinatorial analysis](#combinatorial-analysis)

# Dynamic programming

## Optimización de Fibonacci

La serie de _Fibonacci_ se representa como `Fn = Fn-1 + Fn-2` y es muy simple implementarla de forma recursiva en código. Sin embargo es muy ineficiente hacerlo simplemente recursivo, ya que repetimos varias veces el mismo computo.

<div align="center"> 
  <img src="https://github.com/karlbehrensg/programacion-dinamica-y-estocastica/blob/master/readme_img/fibonnaci-algoritmo.jpeg" width="80%">
  <p>Algoritmo de Fibonnaci</p>
</div>

Si te fijas en la imagen te darás cuenta de que repetimos varias veces el calculo para `f(4), f(3), f(2), f(1) y f(0)`, esto significa que nuestro algoritmo crece de forma **exponencial** `O(2^n)`.

Para optimizar nuestro algoritmo implementaremos en primer lugar la **función recursiva** para luego dar paso a la **memorización**, con esto las mejoras serán realmente sorprendentes.

```py
# Importamos la librería sys para subir el limite de recursividad de Python.
import sys

# La función recursiva realiza varias veces los mismos cálculos.
def fibonacci_recursivo(n):
    if n == 0 or n == 1:
        return 1

    return fibonacci_recursivo(n - 1) + fibonacci_recursivo(n - 2)


# En cambio en la función dinámica vamos a utilizar la técnica de la
# memorización, guardando los resultados ya hechos en un diccionario.
def fibonacci_dinamico(n, memo = {}):
    if n == 0 or n == 1:
        return 1


    # Primero intentamos buscar el resultado en memoria.
    try:
        return memo[n]

    # En caso de no existir realizamos el cálculo.
    except KeyError:
        resultado = fibonacci_dinamico(n - 1, memo) + fibonacci_dinamico(n - 2, memo)
        memo[n] = resultado

        return resultado

if __name__ == '__main__':
    sys.setrecursionlimit(10002)
    n = int(input('Escoge un numero: '))
    resultado = fibonacci_dinamico(n)
    print(resultado)
```
# Statistics
## Combinatorial analysis
Una permutación de un conjunto de elementos, es una disposición de dichos elementos teniendo en cuenta el orden. Una combinación de un conjunto de elementos, es una selección de dichos elementos sin tener en cuenta el orden.

La diferencia entre permutaciones y combinaciones, es que en las permutaciones importa el orden de los elementos, mientras que en las combinaciones no importa el orden en que se disponen los elementos (solo importa su presencia).

Veamos algunos conceptos adicionales, ejemplos y ejercicios resueltos.

Permutaciones
Una permutación de un conjunto de elementos, es una disposición de dichos elementos teniendo en cuenta el orden. El número de permutaciones de “n” elementos tomados de “k” en “k” se calcula con la fórmula:

<img href= "https://matemovil.com/wp-content/uploads/2018/10/permutaciones-f%C3%B3rmula.jpg" alt="permutaciones">
