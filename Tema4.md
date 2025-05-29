
# Tema 4: Métodos de Integración

Este tema aborda los métodos más comunes para la integración numérica de funciones.

---

## 🟪 1. Método del Trapecio

### 📌 Descripción
Aproxima el área bajo la curva dividiendo el intervalo en segmentos que forman trapecios.

### 🧮 Fórmula
Para un solo trapecio:
```
∫(a to b) f(x) dx ≈ (b - a)/2 * [f(a) + f(b)]
```

Para n segmentos:
```
h = (b - a)/n
∫(a to b) f(x) dx ≈ h/2 * [f(x₀) + 2Σf(xᵢ) + f(xₙ)]
```

### 🧾 Pseudocódigo
```
1. Calcular h = (b - a) / n
2. Inicializar suma con f(a) + f(b)
3. Para i en 1 hasta n-1:
    suma += 2 * f(a + i*h)
4. Resultado = (h/2) * suma
```

### 🐍 Código en Python

```python
def trapecio(f, a, b, n):
    h = (b - a) / n
    suma = f(a) + f(b)
    for i in range(1, n):
        suma += 2 * f(a + i * h)
    return h * suma / 2

f = lambda x: x**2
print("Integral (Trapecio):", trapecio(f, 0, 1, 10))
```

---

## 🟩 2. Regla de Simpson

### 📌 Descripción
Usa parábolas para aproximar el área bajo la curva.

### 🧮 Fórmula
Para n par:
```
h = (b - a)/n
∫(a to b) f(x) dx ≈ (h/3) * [f(x₀) + 4Σf(xᵢ impares) + 2Σf(xᵢ pares) + f(xₙ)]
```

### 🧾 Pseudocódigo
```
1. Calcular h = (b - a) / n
2. Inicializar suma con f(a) + f(b)
3. Para i en 1 hasta n-1:
    si i es par: suma += 2 * f(a + i*h)
    si i es impar: suma += 4 * f(a + i*h)
4. Resultado = (h/3) * suma
```

### 🐍 Código en Python

```python
def simpson(f, a, b, n):
    if n % 2:
        raise ValueError("n debe ser par")
    h = (b - a) / n
    suma = f(a) + f(b)
    for i in range(1, n):
        factor = 4 if i % 2 else 2
        suma += factor * f(a + i * h)
    return h * suma / 3

print("Integral (Simpson):", simpson(f, 0, 1, 10))
```

---

## 🟥 3. Método de Cuadratura Gaussiana

### 📌 Descripción
Utiliza puntos y pesos óptimos para evaluar la integral con mayor precisión.

### 🧮 Fórmula
```
∫(a to b) f(x) dx ≈ Σ wᵢ * f(xᵢ)
```

Donde `xᵢ` son raíces de polinomios ortogonales y `wᵢ` los pesos.

### 🧾 Pseudocódigo
```
1. Transformar intervalo [a, b] a [-1, 1]
2. Obtener puntos y pesos
3. Evaluar f en cada punto y multiplicar por su peso
4. Ajustar resultado por el cambio de variable
```

### 🐍 Código en Python

```python
import numpy as np

def gauss_cuadratura(f, a, b, n):
    [x, w] = np.polynomial.legendre.leggauss(n)
    t = 0.5 * (x + 1) * (b - a) + a
    return 0.5 * (b - a) * sum(w * f(t))

print("Integral (Cuadratura Gaussiana):", gauss_cuadratura(f, 0, 1, 3))
```

---

> Estos métodos permiten calcular integrales definidas con alta precisión, siendo útiles cuando no es posible integrar simbólicamente.
