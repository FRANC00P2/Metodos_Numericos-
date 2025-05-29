# Métodos de Interpolación

## 1. Interpolación Lineal

**Descripción:**
La interpolación lineal es un método que utiliza segmentos de línea recta para aproximar los valores de una función entre dos puntos conocidos. Es simple y efectivo para datos que no presentan grandes variaciones.

**Fórmula:**
La fórmula de interpolación lineal entre dos puntos \((x_0, y_0)\) y \((x_1, y_1)\) es:
\[
y = y_0 + \frac{(x - x_0)(y_1 - y_0)}{x_1 - x_0}
\]

**Pseudocódigo:**
```
función interpolacion_lineal(x0, y0, x1, y1, x):
  y = y0 + (x - x0) * (y1 - y0) / (x1 - x0)
  retorno y
```

**Código en Python:**
```python
def interpolacion_lineal(x0, y0, x1, y1, x):
  y = y0 + (x - x0) * (y1 - y0) / (x1 - x0)
  return y

# Ejemplo de aplicación
resultado = interpolacion_lineal(1, 2, 3, 4, 2)
print("Resultado de la interpolación lineal:", resultado)
```

---

## 2. Interpolación Polinómica

**Descripción:**
La interpolación polinómica utiliza un polinomio de grado \(n-1\) para interpolar \(n\) puntos. Es más flexible que la interpolación lineal, pero puede oscilar mucho entre los puntos.

**Fórmula:**
La forma general del polinomio interpolador de Lagrange es:
\[
P(x) = \sum_{i=0}^{n} y_i \prod_{j=0, j \neq i}^{n} \frac{x - x_j}{x_i - x_j}
\]

**Pseudocódigo:**
```
función interpolacion_polinomica(x, x_vals, y_vals):
  n = longitud(x_vals)
  P = 0
  para i desde 0 hasta n-1:
      L = 1
      para j desde 0 hasta n-1:
          si i != j:
              L *= (x - x_vals[j]) / (x_vals[i] - x_vals[j])
      P += y_vals[i] * L
  retorno P
```

**Código en Python:**
```python
def interpolacion_polinomica(x, x_vals, y_vals):
  n = len(x_vals)
  P = 0
  for i in range(n):
      L = 1
      for j in range(n):
          if i != j:
              L *= (x - x_vals[j]) / (x_vals[i] - x_vals[j])
      P += y_vals[i] * L
  return P

# Ejemplo de aplicación
x_vals = [1, 2, 3]
y_vals = [2, 3, 5]
resultado = interpolacion_polinomica(2.5, x_vals, y_vals)
print("Resultado de la interpolación polinómica:", resultado)
```

---

## 3. Regresión Lineal

**Descripción:**
La regresión lineal es un método estadístico que modela la relación entre dos variables mediante una línea recta. Se utiliza para predecir valores y entender la relación entre variables.

**Fórmula:**
La ecuación de la recta de regresión es:
\[
y = mx + b
\]
donde \(m\) es la pendiente y \(b\) es la intersección con el eje \(y\).

**Pseudocódigo:**
```
función regresion_lineal(x_vals, y_vals):
  n = longitud(x_vals)
  m = (n * suma(x_vals * y_vals) - suma(x_vals) * suma(y_vals)) / (n * suma(x_vals^2) - suma(x_vals)^2)
  b = (suma(y_vals) - m * suma(x_vals)) / n
  retorno m, b
```

**Código en Python:**
```python
import numpy as np

def regresion_lineal(x_vals, y_vals):
  n = len(x_vals)
  m = (n * np.dot(x_vals, y_vals) - np.sum(x_vals) * np.sum(y_vals)) / (n * np.dot(x_vals, x_vals) - np.sum(x_vals)**2)
  b = (np.sum(y_vals) - m * np.sum(x_vals)) / n
  return m, b

# Ejemplo de aplicación
x_vals = np.array([1, 2, 3])
y_vals = np.array([2, 3, 5])
m, b = regresion_lineal(x_vals, y_vals)
print("Pendiente:", m, "Intersección:", b)
```

---

## 4. Correlación

**Descripción:**
La correlación mide la relación entre dos variables y cómo cambian juntas. Se expresa comúnmente mediante el coeficiente de correlación de Pearson.

**Fórmula:**
El coeficiente de correlación \(r\) se calcula como:
\[
r = \frac{n(\sum xy) - (\sum x)(\sum y)}{\sqrt{[n \sum x^2 - (\sum x)^2][n \sum y^2 - (\sum y)^2]}}
\]

**Pseudocódigo:**
```
función correlacion(x_vals, y_vals):
  n = longitud(x_vals)
  numerador = n * suma(x_vals * y_vals) - suma(x_vals) * suma(y_vals)
  den1 = sqrt(n * suma(x_vals^2) - suma(x_vals)^2)
  den2 = sqrt(n * suma(y_vals^2) - suma(y_vals)^2)
  retorno numerador / (den1 * den2)
```

**Código en Python:**
```python
def correlacion(x_vals, y_vals):
  n = len(x_vals)
  numerador = n * np.dot(x_vals, y_vals) - np.sum(x_vals) * np.sum(y_vals)
  den1 = np.sqrt(n * np.dot(x_vals, x_vals) - np.sum(x_vals)**2)
  den2 = np.sqrt(n * np.dot(y_vals, y_vals) - np.sum(y_vals)**2)
  return numerador / (den1 * den2)

# Ejemplo de aplicación
x_vals = np.array([1, 2, 3])
y_vals = np.array([2, 3, 5])
resultado = correlacion(x_vals, y_vals)
print("Coeficiente de correlación:", resultado)
```

---

## 5. Mínimos Cuadrados

**Descripción:**
El método de mínimos cuadrados es una técnica utilizada para ajustar un modelo a un conjunto de datos minimizando la suma de los cuadrados de las diferencias entre los valores observados y los valores predichos.

**Fórmula:**
La solución para los parámetros de un modelo lineal se obtiene resolviendo:
\[
\beta = (X^TX)^{-1}X^Ty
\]
donde \(X\) son las variables independientes y \(y\) es la variable dependiente.

**Pseudocódigo:**
```
función minimos_cuadrados(X, y):
  beta = inverso(transpuesta(X) * X) * transpuesta(X) * y
  retorno beta
```

**Código en Python:**
```python
def minimos_cuadrados(X, y):
  X = np.vstack([np.ones(len(X)), X]).T  # Añadir término independiente
  beta = np.linalg.inv(X.T @ X) @ X.T @ y
  return beta

# Ejemplo de aplicación
X_vals = np.array([1, 2, 3])
y_vals = np.array([2, 3, 5])
beta = minimos_cuadrados(X_vals, y_vals)
print("Parámetros de mínimos cuadrados:", beta)
```
