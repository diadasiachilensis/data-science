# 🎲 Distribución Binomial con Python

Este proyecto presenta un análisis completo y visual de la **distribución binomial**, una herramienta fundamental en estadística, probabilidad y ciencia de datos. Utilizando Python y bibliotecas como `NumPy`, `SciPy` y `Matplotlib`, exploramos tanto la teoría como su aplicación práctica mediante gráficos y simulaciones.

---

## 📚 Contenido

### 1. Introducción a la Distribución Binomial
- Definición y condiciones de aplicación.
- Variables aleatorias discretas.
- Experimentos de Bernoulli.

### 2. Fundamento Matemático
$
P(X = k) = \binom{n}{k} \cdot p^k \cdot (1 - p)^{n - k}
$
- $n$: número de ensayos.
- $k$: número de éxitos deseados.
- $p$: probabilidad de éxito en un solo ensayo.

### 3. Visualización de la Función de Masa de Probabilidad (PMF)
- Representación gráfica de $P(X = k)$.
- Ejemplos con diferentes valores de $n$ y $p$.
- Barras verticales con valores numéricos.

### 4. Aplicaciones Reales (Ejercicio de Tiros Penales)
- Simulación de 100 partidos con 5 penales cada uno.
- Visualización de goles marcados.
- Cálculo de $P(X \geq 3)$: probabilidad de marcar al menos 3 goles por tanda.

### 5. Simulación vs Distribución Teórica
- Comparación entre la frecuencia observada y la distribución binomial esperada.

---

## 🧰 Tecnologías utilizadas

- `Python 3`
- `NumPy`
- `Matplotlib`
- `SciPy`
- `Jupyter Notebook`

## 📌 Cómo usar este notebook

1. Clona el repositorio.
2. Asegúrate de tener las dependencias instaladas:
   ```bash
   pip install numpy matplotlib scipy
