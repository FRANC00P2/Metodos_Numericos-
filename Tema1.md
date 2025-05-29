# Tema 1: Introducción a Métodos Numéricos

## 📌 Descripción del método
Los métodos numéricos son técnicas que permiten encontrar soluciones aproximadas a problemas matemáticos que no se pueden resolver analíticamente. Se utilizan en ingeniería, física, economía, etc.

## 🧮 Fórmula del método (Ejemplo: Método de Bisección)
El método de bisección se basa en el teorema de Bolzano:
Si `f(a) * f(b) < 0`, entonces existe al menos una raíz en el intervalo `[a, b]`.

Iterativamente:
c = (a + b)/2
Si `f(c) = 0`, c es la raíz.  
Si `f(a) * f(c) < 0`, la raíz está en `[a, c]`.  
Si `f(b) * f(c) < 0`, la raíz está en `[c, b]`.

## 🧾 Pseudocódigo
Entrada: función f, intervalo [a, b], tolerancia tol
Mientras (b - a)/2 > tol:
c = (a + b)/2
Si f(c) == 0:
retornar c
Sino si f(a)*f(c) < 0:
b = c
Sino:
a = c
Retornar (a + b)/2

## 🐍 Código en Python

```python
def biseccion(f, a, b, tol=1e-6):
    while (b - a)/2 > tol:
        c = (a + b) / 2
        if f(c) == 0:
            return c
        elif f(a)*f(c) < 0:
            b = c
        else:
            a = c
    return (a + b) / 2

📊 Ejemplo de aplicación
Queremos encontrar una raíz de la función f(x) = x^2 - 2 en el intervalo [0, 2]:
resultado = biseccion(lambda x: x**2 - 2, 0, 2)
print("Raíz aproximada:", resultado)

## Salida esperada:
Raíz aproximada: 1.4142...
