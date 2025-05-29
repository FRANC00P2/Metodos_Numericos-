# Métodos Numéricos

## Método de Euler (Un paso)

### Descripción
El método de Euler es un método numérico simple para resolver ecuaciones diferenciales ordinarias. Utiliza una aproximación lineal para avanzar en el tiempo.

### Fórmula
\[
y_{n+1} = y_n + h f(t_n, y_n)
\]

### Pseudocódigo
```
1. Inicializar y_0, t_0, h
2. Para n desde 0 hasta N-1:
   3. y_{n+1} = y_n + h * f(t_n, y_n)
   4. t_{n+1} = t_n + h
```

### Código en Python
```python
def euler_method(f, y0, t0, h, N):
    y = y0
    t = t0
    for n in range(N):
        y += h * f(t, y)
        t += h
    return y
```

### Ejemplo de Aplicación
Resolver la ecuación \(\frac{dy}{dt} = y\) con \(y(0) = 1\).

---

## Método Adams-Bashforth-Moulton

### Descripción
Este método es un método de pasos múltiples que utiliza información de pasos anteriores para calcular el siguiente valor.

### Fórmula
\[
y_{n+1} = y_n + \frac{h}{2} \left( f(t_{n+1}, y_{n+1}) + f(t_n, y_n) \right)
\]

### Pseudocódigo
```
1. Inicializar y_0, t_0, h
2. Para n desde 0 hasta N-1:
   3. Predecir y_{n+1} usando Adams-Bashforth
   4. Corregir y_{n+1} usando Adams-Moulton
```

### Código en Python
```python
def adams_bashforth_moulton(f, y0, t0, h, N):
    # Implementación del método
    pass  # Completar implementación
```

### Ejemplo de Aplicación
Resolver la ecuación \(\frac{dy}{dt} = y\) con \(y(0) = 1\).

---

## Método de Taylor (Orden n)

### Descripción
El método de Taylor utiliza la serie de Taylor para aproximar la solución de una ODE.

### Fórmula
\[
y(t) = y(t_0) + (t - t_0) \frac{dy}{dt}(t_0) + \frac{(t - t_0)^2}{2!} \frac{d^2y}{dt^2}(t_0) + \ldots
\]

### Pseudocódigo
```
1. Inicializar y_0, t_0, h
2. Para n desde 0 hasta N-1:
   3. Calcular términos de Taylor
   4. y_{n+1} = y_n + \text{sumatoria de términos}
```

### Código en Python
```python
def taylor_method(f, y0, t0, h, N, order):
    # Implementación del método
    pass  # Completar implementación
```

### Ejemplo de Aplicación
Resolver la ecuación \(\frac{dy}{dt} = y\) con \(y(0) = 1\).

---

## Métodos de Euler para Sistemas

### Descripción
Extensión del método de Euler para resolver sistemas de ecuaciones diferenciales.

### Fórmula
Para un sistema de ecuaciones:
\[
\mathbf{y}_{n+1} = \mathbf{y}_n + h \mathbf{f}(t_n, \mathbf{y}_n)
\]

### Pseudocódigo
```
1. Inicializar \mathbf{y}_0, t_0, h
2. Para n desde 0 hasta N-1:
   3. \mathbf{y}_{n+1} = \mathbf{y}_n + h * \mathbf{f}(t_n, \mathbf{y}_n)
   4. t_{n+1} = t_n + h
```

### Código en Python
```python
def euler_method_system(f, y0, t0, h, N):
    # Implementación del método
    pass  # Completar implementación
```

### Ejemplo de Aplicación
Resolver el sistema de ecuaciones:
\[
\begin{align*}
\frac{dx}{dt} &= y \\
\frac{dy}{dt} &= -x
\end{align*}
\]

---

## Métodos de Runge-Kutta (RK4) para una Ecuación Diferencial Ordinaria

### Descripción
El método RK4 es un método de cuarto orden que proporciona una buena precisión.

### Fórmula
\[
y_{n+1} = y_n + \frac{h}{6} (k_1 + 2k_2 + 2k_3 + k_4)
\]
donde:
\[
\begin{align*}
k_1 &= f(t_n, y_n) \\
k_2 &= f(t_n + \frac{h}{2}, y_n + \frac{h}{2} k_1) \\
k_3 &= f(t_n + \frac{h}{2}, y_n + \frac{h}{2} k_2) \\
k_4 &= f(t_n + h, y_n + h k_3)
\end{align*}
\]

### Pseudocódigo
```
1. Inicializar y_0, t_0, h
2. Para n desde 0 hasta N-1:
   3. Calcular k_1, k_2, k_3, k_4
   4. y_{n+1} = y_n + (h/6) * (k_1 + 2*k_2 + 2*k_3 + k_4)
   5. t_{n+1} = t_n + h
```

### Código en Python
```python
def runge_kutta_4(f, y0, t0, h, N):
    # Implementación del método
    pass  # Completar implementación
```

### Ejemplo de Aplicación
Resolver la ecuación \(\frac{dy}{dt} = y\) con \(y(0) = 1\).

---

## Métodos de Runge-Kutta (RK4) para Sistemas de Ecuaciones Diferenciales Ordinarias

### Descripción
Extensión del método RK4 para sistemas de ecuaciones.

### Fórmula
Similar al caso anterior, pero aplicado a vectores.

### Pseudocódigo
```
1. Inicializar \mathbf{y}_0, t_0, h
2. Para n desde 0 hasta N-1:
   3. Calcular k_1, k_2, k_3, k_4 para el sistema
   4. \mathbf{y}_{n+1} = \mathbf{y}_n + (h/6) * (k_1 + 2*k_2 + 2*k_3 + k_4)
   5. t_{n+1} = t_n + h
```

### Código en Python
```python
def runge_kutta_4_system(f, y0, t0, h, N):
    # Implementación del método
    pass  # Completar implementación
```

### Ejemplo de Aplicación
Resolver el sistema de ecuaciones:
\[
\begin{align*}
\frac{dx}{dt} &= y \\
\frac{dy}{dt} &= -x
\end{align*}
\]

---

## Métodos de Adams-Bashforth (Método de pasos múltiples)

### Descripción
Este método utiliza varios pasos anteriores para estimar el próximo valor.

### Fórmula
\[
y_{n+1} = y_n + \frac{h}{k} \sum_{j=0}^{k-1} b_j f(t_{n-j}, y_{n-j})
\]
donde \(b_j\) son los coeficientes del método.

### Pseudocódigo
```
1. Inicializar y_0, t_0, h
2. Para n desde 0 hasta N-1:
   3. Calcular y_{n+1} usando los pasos anteriores
```

### Código en Python
```python
def adams_bashforth(f, y0, t0, h, N, k):
    # Implementación del método
    pass  # Completar implementación
```

### Ejemplo de Aplicación
Resolver la ecuación \(\frac{dy}{dt} = y\) con \(y(0) = 1\).

---

## Método de Linealización

### Descripción
Este método transforma una ecuación no lineal en una lineal para facilitar su resolución.

### Fórmula
\[
y_{n+1} = y_n + h f(t_n, y_n)
\]

### Pseudocódigo
```
1. Inicializar y_0, t_0, h
2. Para n desde 0 hasta N-1:
   3. Linealizar la ecuación
   4. Resolver la ecuación linealizada
```

### Código en Python
```python
def linearization_method(f, y0, t0, h, N):
    # Implementación del método
    pass  # Completar implementación
```

### Ejemplo de Aplicación
Resolver la ecuación \(\frac{dy}{dt} = y^2\) con \(y(0) = 1\).

---

## Método de Adams-Moulton (Método de pasos múltiples)

### Descripción
Es un método implícito que utiliza pasos anteriores y el valor actual para calcular el próximo.

### Fórmula
\[
y_{n+1} = y_n + \frac{h}{2} \left( f(t_{n+1}, y_{n+1}) + f(t_n, y_n) \right)
\]

### Pseudocódigo
```
1. Inicializar y_0, t_0, h
2. Para n desde 0 hasta N-1:
   3. Predecir y_{n+1} usando Adams-Bashforth
   4. Corregir y_{n+1} usando Adams-Moulton
```

### Código en Python
```python
def adams_moulton(f, y0, t0, h, N):
    # Implementación del método
    pass  # Completar implementación
```

### Ejemplo de Aplicación
Resolver la ecuación \(\frac{dy}{dt} = y\) con \(y(0) = 1\).

---
