
# Tema 2: Solución de Ecuaciones

En este tema abordamos diferentes métodos numéricos para encontrar raíces de funciones.

---

## 📈 1. Método Gráfico

### 📌 Descripción
Consiste en graficar la función y observar dónde cruza el eje X. No es preciso pero útil para obtener una estimación inicial de la raíz.

### 🧾 Pseudocódigo
```
1. Elegir intervalo [a, b]
2. Evaluar f(x) en varios puntos
3. Graficar f(x) contra x
4. Observar el punto donde f(x) ≈ 0
```

### 🐍 Código en Python

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.linspace(-5, 5, 400)
f = lambda x: x**3 - x - 2
y = f(x)

plt.plot(x, y)
plt.axhline(0, color='black')
plt.title("Método Gráfico")
plt.grid()
plt.show()
```

---

## ✂️ 2. Método de Bisección

### 📌 Descripción
Se basa en dividir el intervalo [a, b] en dos y seleccionar el subintervalo donde cambia el signo de f(x).

### 🧮 Fórmula
```
xₙ = (a + b) / 2
```

### 🧾 Pseudocódigo
```
1. Calcular f(a) y f(b)
2. Mientras |b - a| > tolerancia:
    x = (a + b)/2
    Si f(a)*f(x) < 0: b = x
    Si f(b)*f(x) < 0: a = x
3. Retornar x
```

### 🐍 Código en Python

```python
def biseccion(f, a, b, tol=1e-6):
    while abs(b - a) > tol:
        c = (a + b) / 2
        if f(a) * f(c) < 0:
            b = c
        else:
            a = c
    return (a + b) / 2

print("Raíz:", biseccion(lambda x: x**3 - x - 2, 1, 2))
```

---

## 📏 3. Método de la Regla Falsa (False Position)

### 📌 Descripción
Similar a bisección pero usa una línea recta entre los puntos para estimar mejor la raíz.

### 🧮 Fórmula
```
xₙ = b - f(b)*(b - a)/(f(b) - f(a))
```

### 🧾 Pseudocódigo
```
1. Calcular f(a) y f(b)
2. Mientras |f(x)| > tolerancia:
    x = b - f(b)*(b - a)/(f(b) - f(a))
    Si f(a)*f(x) < 0: b = x
    Si f(b)*f(x) < 0: a = x
3. Retornar x
```

### 🐍 Código en Python

```python
def regla_falsa(f, a, b, tol=1e-6):
    while True:
        x = b - f(b)*(b - a)/(f(b) - f(a))
        if abs(f(x)) < tol:
            return x
        if f(a) * f(x) < 0:
            b = x
        else:
            a = x

print("Raíz:", regla_falsa(lambda x: x**3 - x - 2, 1, 2))
```

---

## 📍 4. Método del Punto Fijo

### 📌 Descripción
Transforma la ecuación f(x)=0 en x = g(x), y se repite la iteración xₙ₊₁ = g(xₙ).

### 🧮 Fórmula
```
xₙ₊₁ = g(xₙ)
```

### 🧾 Pseudocódigo
```
1. Escoger función g(x)
2. Iniciar con x₀
3. Mientras |xₙ₊₁ - xₙ| > tolerancia:
    xₙ₊₁ = g(xₙ)
4. Retornar xₙ₊₁
```

### 🐍 Código en Python

```python
def punto_fijo(g, x0, tol=1e-6, max_iter=100):
    for _ in range(max_iter):
        x1 = g(x0)
        if abs(x1 - x0) < tol:
            return x1
        x0 = x1
    return x1

print("Raíz:", punto_fijo(lambda x: (x**3 - 2)/x, 1.5))
```

---

## 🧠 5. Método de Newton-Raphson

### 📌 Descripción
Usa la derivada de f(x) para calcular la raíz.

### 🧮 Fórmula
```
xₙ₊₁ = xₙ - f(xₙ)/f'(xₙ)
```

### 🧾 Pseudocódigo
```
1. Calcular f(xₙ) y f'(xₙ)
2. xₙ₊₁ = xₙ - f(xₙ)/f'(xₙ)
3. Repetir hasta converger
```

### 🐍 Código en Python

```python
def newton_raphson(f, df, x0, tol=1e-6, max_iter=100):
    for _ in range(max_iter):
        x1 = x0 - f(x0)/df(x0)
        if abs(x1 - x0) < tol:
            return x1
        x0 = x1
    return x1

print("Raíz:", newton_raphson(lambda x: x**3 - x - 2, lambda x: 3*x**2 - 1, 1.5))
```

---

## 🧮 6. Método de la Secante

### 📌 Descripción
Es una variación del método de Newton pero sin usar la derivada.

### 🧮 Fórmula
```
xₙ₊₁ = xₙ - f(xₙ)*(xₙ - xₙ₋₁)/(f(xₙ) - f(xₙ₋₁))
```

### 🧾 Pseudocódigo
```
1. Iniciar con x₀ y x₁
2. Calcular x₂ usando fórmula
3. Repetir hasta converger
```

### 🐍 Código en Python

```python
def secante(f, x0, x1, tol=1e-6, max_iter=100):
    for _ in range(max_iter):
        fx0, fx1 = f(x0), f(x1)
        if fx1 - fx0 == 0:
            break
        x2 = x1 - fx1*(x1 - x0)/(fx1 - fx0)
        if abs(x2 - x1) < tol:
            return x2
        x0, x1 = x1, x2
    return x2

print("Raíz:", secante(lambda x: x**3 - x - 2, 1, 2))
```

---

> Estos métodos permiten resolver ecuaciones no lineales con diversas precisiones y eficiencias, dependiendo del comportamiento de la función.
