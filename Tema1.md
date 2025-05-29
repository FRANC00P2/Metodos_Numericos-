
# Tema 1: Introducción a Métodos Numéricos

Los métodos numéricos permiten resolver problemas matemáticos mediante técnicas computacionales. En este tema se presentan los tipos de errores más comunes en los cálculos numéricos.

---

## 🔍 1. Tipos de errores

### 📌 Descripción
En los métodos numéricos, los errores son inevitables y pueden clasificarse como:
- **Errores de entrada**: valores medidos o redondeados.
- **Errores de truncamiento**: al usar una aproximación en lugar de una fórmula exacta.
- **Errores de redondeo**: debido a la representación finita de los números en computadora.
- **Errores propagados**: acumulación de errores a lo largo de múltiples pasos.

---

## 🧮 2. Errores de precisión

### 📌 Descripción
Ocurren por la cantidad limitada de cifras significativas que puede representar una computadora.

### 📊 Ejemplo en Python

```python
a = 0.1 + 0.2
print(a == 0.3)  # Falso debido a la pérdida de precisión
print("Resultado exacto:", a)
```

---

## 🧮 3. Errores de truncamiento

### 📌 Descripción
Se producen al usar una versión simplificada de una fórmula infinita, como al truncar una serie de Taylor.

### 🐍 Ejemplo en Python

```python
import math

def cos_aprox(x, n=4):
    # Serie de Taylor para cos(x) truncada
    return sum(((-1)**k * x**(2*k)) / math.factorial(2*k) for k in range(n))

print("cos(0.5) exacto:", math.cos(0.5))
print("cos(0.5) aproximado:", cos_aprox(0.5))
```

---

## 🧮 4. Error Absoluto

### 📌 Descripción
Diferencia entre el valor verdadero y el valor aproximado.

### 🧮 Fórmula:
```
Error Absoluto = |valor_verdadero - valor_aproximado|
```

### 🐍 Código

```python
valor_real = 3.1416
valor_aprox = 3.14
error_abs = abs(valor_real - valor_aprox)
print("Error absoluto:", error_abs)
```

---

## 🧮 5. Error Relativo

### 📌 Descripción
Error absoluto en relación con el valor verdadero.

### 🧮 Fórmula:
```
Error Relativo = Error Absoluto / |valor_verdadero|
```

### 🐍 Código

```python
error_rel = error_abs / abs(valor_real)
print("Error relativo:", error_rel)
```

---

## 🧮 6. Aproximación y Error

### 📌 Descripción
Una aproximación se refiere a un valor calculado que se acerca al valor exacto. El error cuantifica la diferencia.

### 🐍 Código

```python
aprox = 3.14
real = 3.1416
error = abs(real - aprox)
print("Aproximación:", aprox)
print("Error:", error)
```

---

## 🧮 7. Error de Redondeo

### 📌 Descripción
Se produce cuando se redondean números para adaptarlos al formato de la máquina.

### 🐍 Código

```python
x = round(2.675, 2)
print("Resultado de redondeo:", x)  # Imprime 2.67, no 2.68
```

---

## 🧮 8. Errores en Cálculos Numéricos

### 📌 Descripción
Resultado de operaciones matemáticas sucesivas que acumulan errores.

### 🐍 Ejemplo

```python
suma = 0
for _ in range(10**6):
    suma += 0.000001

print("Resultado acumulado:", suma)  # Debería ser 1.0, pero puede variar por errores acumulados
```

---

## 🧮 9. Errores Propagados

### 📌 Descripción
Cuando un error en una entrada afecta el resultado final por medio de una fórmula o proceso.

### 🐍 Ejemplo

```python
def volumen_esfera(r):
    return (4/3) * math.pi * r**3

r_aprox = 1.01  # Suponiendo un error en el radio
vol = volumen_esfera(r_aprox)
print("Volumen con radio aproximado:", vol)
```

---

> Todos estos errores son fundamentales para comprender cómo los métodos numéricos se comportan en la práctica y cómo se puede mejorar la precisión de los cálculos.
