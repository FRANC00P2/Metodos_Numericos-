
# Tema 3: Sistemas de Ecuaciones Lineales

Los métodos numéricos para sistemas lineales permiten resolver múltiples ecuaciones simultáneamente. A continuación, se describen los métodos más utilizados.

---

## 🔢 1. Eliminación Gaussiana

### 📌 Descripción
Convierte el sistema en una matriz triangular superior y luego resuelve por sustitución regresiva.

### 🧮 Fórmula
Transformar el sistema Ax = b en una forma triangular:

```
U*x = c
```

### 🧾 Pseudocódigo
```
1. Para cada fila i:
    a. Hacer cero los elementos debajo de A[i][i]
2. Aplicar sustitución regresiva
```

### 🐍 Código en Python

```python
import numpy as np

def gauss_eliminacion(A, b):
    n = len(b)
    Ab = np.hstack([A, b.reshape(-1,1)])
    for i in range(n):
        for j in range(i+1, n):
            factor = Ab[j][i] / Ab[i][i]
            Ab[j] = Ab[j] - factor * Ab[i]
    x = np.zeros(n)
    for i in range(n-1, -1, -1):
        x[i] = (Ab[i][-1] - np.dot(Ab[i][i+1:n], x[i+1:n])) / Ab[i][i]
    return x

A = np.array([[2,1,-1],[ -3,-1,2],[ -2,1,2]], float)
b = np.array([8,-11,-3], float)
print("Solución:", gauss_eliminacion(A, b))
```

---

## 🔁 2. Método de Gauss-Jordan

### 📌 Descripción
Reduce la matriz a su forma de identidad, dando la solución directamente.

### 🧮 Fórmula
Transformar la matriz aumentada [A|b] a [I|x]

### 🧾 Pseudocódigo
```
1. Para cada fila i:
    a. Hacer A[i][i] = 1
    b. Hacer ceros en todas las demás posiciones de la columna i
2. Extraer x de la matriz aumentada
```

### 🐍 Código en Python

```python
def gauss_jordan(A, b):
    n = len(b)
    Ab = np.hstack([A.astype(float), b.reshape(-1,1)])
    for i in range(n):
        Ab[i] = Ab[i] / Ab[i][i]
        for j in range(n):
            if i != j:
                Ab[j] = Ab[j] - Ab[j][i] * Ab[i]
    return Ab[:, -1]

print("Solución:", gauss_jordan(A, b))
```

---

## 🔃 3. Método de Gauss-Seidel

### 📌 Descripción
Método iterativo que usa la última actualización de valores en cada iteración.

### 🧮 Fórmula
```
x_i^(k+1) = (1/a_ii) * (b_i - Σ a_ij * x_j^(k+1 o k))
```

### 🧾 Pseudocódigo
```
1. Iniciar con x₀
2. Para cada iteración:
    a. Actualizar cada xᵢ con el valor más reciente
3. Repetir hasta converger
```

### 🐍 Código en Python

```python
def gauss_seidel(A, b, x0=None, tol=1e-6, max_iter=100):
    n = len(b)
    x = np.zeros(n) if x0 is None else x0
    for _ in range(max_iter):
        x_new = np.copy(x)
        for i in range(n):
            s1 = sum(A[i][j] * x_new[j] for j in range(i))
            s2 = sum(A[i][j] * x[j] for j in range(i+1, n))
            x_new[i] = (b[i] - s1 - s2) / A[i][i]
        if np.linalg.norm(x - x_new) < tol:
            return x_new
        x = x_new
    return x

print("Solución:", gauss_seidel(A, b))
```

---

## 🔄 4. Método de Jacobi

### 📌 Descripción
Otro método iterativo, pero usa únicamente valores de la iteración anterior.

### 🧮 Fórmula
```
x_i^(k+1) = (1/a_ii) * (b_i - Σ a_ij * x_j^(k))
```

### 🧾 Pseudocódigo
```
1. Iniciar con x₀
2. Para cada iteración:
    a. Calcular xᵢ⁽ᵏ⁺¹⁾ usando solo x⁽ᵏ⁾
3. Repetir hasta converger
```

### 🐍 Código en Python

```python
def jacobi(A, b, x0=None, tol=1e-6, max_iter=100):
    n = len(b)
    x = np.zeros(n) if x0 is None else x0
    for _ in range(max_iter):
        x_new = np.copy(x)
        for i in range(n):
            s = sum(A[i][j] * x[j] for j in range(n) if j != i)
            x_new[i] = (b[i] - s) / A[i][i]
        if np.linalg.norm(x - x_new) < tol:
            return x_new
        x = x_new
    return x

print("Solución:", jacobi(A, b))
```

---

> Estos métodos permiten resolver sistemas de ecuaciones de manera eficiente dependiendo del tipo de matriz (diagonal dominante, esparsa, etc.).
