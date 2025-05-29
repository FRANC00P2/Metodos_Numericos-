# Métodos de Resolución de Ecuaciones Diferenciales

## 1. Método de Euler (Un paso)

**Descripción:**
El método de Euler es un método numérico sencillo para resolver ecuaciones diferenciales ordinarias. Utiliza la pendiente en el punto inicial para estimar el valor en el siguiente punto.

**Fórmula:**
La fórmula del método de Euler es:
\[
y_{n+1} = y_n + h f(t_n, y_n)
\]

**Pseudocódigo:**
```
función euler(f, t0, y0, h, n):
  y = y0
  t = t0
  para i desde 0 hasta n-1:
      y += h * f(t, y)
      t += h
  retorno y
```

**Código en Python:**
```python
def euler(f, t0, y0, h, n):
  y = y0
  t = t0
  for i in range(n):
      y += h * f(t, y)
      t += h
  return y

# Ejemplo de aplicación
def f(t, y):
  return y  # dy/dt = y

resultado = euler(f, 0, 1, 0.1, 10)
print("Resultado del método de Euler:", resultado)
```

---

## 2. Método Adams-Bashforth-Moulton

**Descripción:**
Este método es un método de pasos múltiples que combina el método de Adams-Bashforth (predicción) y el método de Adams-Moulton (corrección) para mejorar la precisión.

**Fórmula:**
La fórmula del método de Adams-Bashforth-Moulton es:
\[
y_{n+1} = y_n + \frac{h}{2} \left( f(t_{n+1}, y_{n+1}) + f(t_n, y_n) \right)
\]

**Pseudocódigo:**
``
