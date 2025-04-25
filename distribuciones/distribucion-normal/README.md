# Indice

1. [Introducción](#introducción)
2. [Distribuciones](#distribuciones-analizadas)
    - [Distribución Normal](#Distribución-Normal)

# Distribuciones

# Distribución Normal

Este proyecto tiene como objetivo explorar y comparar **tres pruebas estadísticas de normalidad** utilizando Python, a través de un ejemplo práctico con datos simulados. Incluye visualizaciones, interpretación crítica y consideraciones técnicas que demuestran cómo evaluar la normalidad en un conjunto de datos.

---

## 📚 Contenido del Notebook

El archivo [`distribucion_normal.ipynb`](./distribucion_normal.ipynb) incluye:

### 1. **Generación de Datos**
- Simulación de una variable sesgada (log-normal) para probar los límites de cada test.

### 2. **Visualización**
- Histograma con curva de densidad.
- Análisis visual previo a los test estadísticos.

### 3. **Aplicación de Tests de Normalidad**
Se aplican las siguientes pruebas:
- 📏 **Shapiro-Wilk**
- 📈 **Kolmogorov-Smirnov** (ajustada a $ \mu$, $\sigma$)
- 📉 **D’Agostino y Pearson** (`normaltest`)

### 4. **Comparación de Resultados**
- Análisis de casos donde **una prueba detecta desviaciones** de la normalidad y otras no.
- Discusión sobre causas y recomendaciones.

---

## 🧠 Fundamento Matemático

### 📌 Fórmula de la distribución normal:

$$
f(x) = \frac{1}{\sqrt{2\pi\sigma^2}} \cdot e^{ -\frac{(x - \mu)^2}{2\sigma^2} }
$$

Donde:
- $\mu$ : media.
- $\sigma$ : desviación estándar.
- $x$ : valor de la variable aleatoria.

---

## 🧪 Interpretación Estadística

Cada prueba evalúa la hipótesis:

**H₀:** los datos siguen una distribución normal.

| Prueba                    | ¿Cuándo usarla?                                   | Ventajas                             |
|--------------------------|----------------------------------------------------|--------------------------------------|
| **Shapiro-Wilk**         | Muestras pequeñas o medianas (n < 5000)            | Alta potencia                        |
| **Kolmogorov-Smirnov**   | Comparación con una dist. teórica ajustada         | Simple de aplicar, menos sensible    |
| **D’Agostino y Pearson** | Muestras medianas/grandes con sesgos o curtosis    | Evalúa forma de la curva             |

---

## ✅ Resultados Esperados (Ejemplo)

```text
Shapiro-Wilk:            p = 0.1675  ✅
Kolmogorov-Smirnov:      p = 0.0501  ⚠️
D’Agostino-Pearson:      p = 0.0241  ❌
