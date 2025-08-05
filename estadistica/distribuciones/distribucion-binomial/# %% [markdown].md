# %% [markdown]
# # 🎲 Distribucion Binomial

# %% [markdown]
# ## 📌 Introducción

# %% [markdown]
# La **distribución binomial** modela la probabilidad de obtener exactamente \( k \) éxitos en \( n \) **ensayos independientes**, donde cada ensayo tiene solo **dos posibles resultados**: éxito o fracaso.
# 
# Es una distribución **discreta** (valores enteros), y cada ensayo debe cumplir con las condiciones de un experimento de **Bernoulli**.
# 
# Se aplica cuando:
# 
# - Tienes **n** repeticiones del mismo experimento.
# - Cada experimento tiene solo dos posibles resultados: ✅ Éxito / ❌ Fracaso.
# - La probabilidad de éxito \( p \) es **constante** en cada repetición.
# - Los ensayos son **independientes** entre sí.
# 

# %% [markdown]
# ## ✏️ Ejemplos típicos

# %% [markdown]
# - Lanzar una moneda 10 veces y contar cuántas veces sale cara.
# - Enviar 20 correos y medir cuántos reciben respuesta.
# - Un test de COVID aplicado a 100 personas, con $p = 0.05$ de positivo.

# %% [markdown]
# ## 📐 Función de Probabilidad (FDP)

# %% [markdown]
# La **fórmula** de la distribución binomial es:
# 
# $
# P(X = k) = \binom{n}{k} p^k (1 - p)^{n-k}
# $
# 
# Donde:
# 
# - $n$: número total de ensayos
# - $k$: número de éxitos
# - $p$: probabilidad de éxito
# - $ \binom{n}{k}$: coeficiente binomial = $ \frac{n!}{k!(n-k)!} $

# %% [markdown]
# ---

# %% [markdown]
# ## 🐍 Implementación en Python

# %%
import numpy as np
import matplotlib.pyplot as plt
import scipy.stats as ss

# %% [markdown]
# ### Paso 2: Parámetros del experimento

# %%
n = 100  # número de ensayos
p = 0.5   # probabilidad de éxito
#Considerar un conjunto de puntos en el eje X
x_binomial = np.arange(0, n+1)
#Funcion de masa de probabilidad
pmf = ss.binom.pmf(x_binomial, n, p)

# %%
# P(X=40)
prob_binomial=ss.binom.pmf(40,n,p)
prob_binomial

# %% [markdown]
# ### Paso 3: Visualización
# 

# %%
fig=plt.figure(figsize=(6,5))
plt.vlines(x_binomial,0,pmf,lw=5,label=f' $n:{n}$ y $p: {0.5}$')
plt.axhline(prob_binomial,color='magenta',label=f' $P(X=40)$') # plt.axhline= linea horizontal, plt.axvline= linea vertical
plt.legend()
plt.title('Distribución binomial: Función de masa de probabilidad')
plt.show()

# %% [markdown]
# ## Gráfica de la función de distribcuión de probabilidad

# %% [markdown]
# Para graficar la función de distribución probabilidad  $P(X\leq x)$ debemos, utilizar la función $ss.binom.cdf(x,n,p)$ de la librería scypi.stats

# %%
# Para está gráfica, consideraremos n=100 y p=0.5, además consideraremos x_binomial
fdp=ss.binom.cdf(x_binomial, n,p) # Función de distribuci+on de probabilidad

# %% [markdown]
# distribución probabilidad  $P(X\leq 50)$

# %%
prob=ss.binom.cdf(50,n,p)

# %% [markdown]
# ### Paso 3: Visualización

# %%
fig=plt.figure(figsize=(6,5))
plt.vlines(x_binomial,0,fdp,lw=5,color='pink',label=f' $n={n},p={p}$')
plt.title('Distribución Binomial: Función de distribución de probabilidad')
plt.axhline(prob,label=f'$P(X\leq 50):{round(prob,3)}$')
plt.ylabel('Probabilidad')
plt.legend()
plt.show()

# %% [markdown]
# ## 🧮 Media y Varianza

# %% [markdown]
# - **Media (esperanza):** $\mu = n \cdot p$
# - **Varianza:** $\sigma^2 = n \cdot p \cdot (1 - p)$

# %% [markdown]
# Para una variable aleatoria que se distribuye binomial, se definen la esperanza y la varianza como
# $$
# E(X) = n\cdot p ;\qquad V(X) = n \cdot p \cdot (1-p)
# $$
# donde $n$ corresponde al tamaño de la muestra, y $p$ a la probabilidad de éxito de la variable aleatoria

# %% [markdown]
# Un restaurante quiere analizar la probabilidad de que un cliente deje una propina superior a $\$3$. Se sabe que, con base en datos históricos (según la base de datos tips), aproximadamente el $30%$ de los clientes dejan una propina mayor a $\$3$
# 
# 1. Si un día el restaurante atiende a 10 clientes, ¿cuál es la probabilidad de que exactamente 4 de ellos dejen una propina mayor a $3.00?

# %% [markdown]
# **Sol:**
# Sea
# $X=$ Clientes que dejan una propina superior a $\$3$.
# 
# Se sabe que:
# - Cada cliente es un intento independiente.
# - La probabilidad de éxito (dejar una propina mayor a $\$3$) es
# $p=0.3$
# - Se atienden $n=10$ clientes
# 
# De lo anterior, se tiene que
# $$
# X\sim Binom(n=10,p=0.3)
# $$
# 
# 

# %%
n=10    #Numero total de clientes
p=0.3   #probabilidad de que dejen propina > $3

# %%
p_binomial1=ss.binom.pmf(4,n,p).round(4)

# %%
print(f'P(X=4):{p_binomial1}')

# %% [markdown]
# ### ❓2. ¿ Cuál es la probabilidad de que más de 4 clientes dejen una propina superior a $\$3$?

# %% [markdown]
# distribución probabilidad  $P(X > 4)$
# 
# $
# P(X > 4) = 1 - P(X \leq 4)
# $
# 
# Donde:
# - $X$ es una variable aleatoria binomial: $X \sim \text{Binomial}(n, p)$
# - `n`: número de clientes.
# - `p`: probabilidad de que un cliente deje una propina superior a $3.

# %%
(1-ss.binom.cdf(4,n,p)).round(3)*100

# %% [markdown]
# #### ✅ Interpretación final

# %% [markdown]
# Significa que:
# 
# > Hay un 15% de probabilidad de que más de 4 clientes dejen una propina superior a $3.
# 
# > El resultado te está diciendo que en un grupo de 𝑛 clientes, solo en el 15% de los casos se espera que más de 4 personas dejen una propina alta.
# 
# 

# %% [markdown]
# #### Parámetros del experimento

# %%
x = np.arange(0, n + 1)
pmf = ss.binom.pmf(x, n, p)


# %% [markdown]
# #### Graficar distribución

# %%
plt.figure(figsize=(8,5))
for i in range(len(x)):
    if x[i] <= 4:
        plt.vlines(x[i], 0, pmf[i], colors='gray', lw=5, label='P(X ≤ 4)' if i == 0 else "")
    else:
        plt.vlines(x[i], 0, pmf[i], colors='crimson', lw=5, label='P(X > 4)' if i == 5 else "")

# Títulos y etiquetas
plt.title('Distribución Binomial: P(X > 4)')
plt.xlabel('Clientes que dejan propina > $3')
plt.ylabel('P(X = k)')
plt.legend()
plt.grid(True)
plt.show()

# %% [markdown]
# #### 🎯 Qué representa este gráfico

# %% [markdown]
# - Las barras **grises** son $ P(X \leq 4) $ → no nos interesan en esta pregunta.
# - Las barras **rojas (crimson)** representan $ P(X > 4) $ → **la zona de interés**.
# - La suma de las barras rojas es exactamente $ 1 - \text{binom.cdf}(4, n, p) $

# %% [markdown]
# ### ❓3. ¿Cuál es la probabibilidad de que menos de 4 clientes dejen una propina superior a $\$3$?

# %%
ss.binom.cdf(3,n,p).round(3)*100

# %% [markdown]
# #### ✅ Interpretación final

# %% [markdown]
# > Hay un 65% de probabilidad de que a los menos 4 clientes dejen una propina superior a $3.

# %% [markdown]
# #### Graficar distribucion

# %%
plt.figure(figsize=(8,5))

for i in range(len(x)):
    altura = pmf[i]
    color = 'crimson' if x[i] < 4 else 'gray'
    
    # Dibujar barra
    plt.vlines(x[i], 0, altura, colors=color, lw=5, label='P(X > 4)' if i == 0 else "")

    # Agregar valor en la parte superior de cada barra
    plt.text(x[i], altura + 0.002, f'{altura:.3f}', ha='center', fontsize=8)

# Títulos y etiquetas
plt.title('Distribución Binomial: P(X > 4)')
plt.xlabel('Clientes que dejan propina > $3')
plt.ylabel('P(X = k)')
plt.legend()
plt.grid(True)
plt.show()

# %% [markdown]
# ## Variaciones de 𝑝 y 𝑛

# %% [markdown]
# ### Paso 1: Librerias

# %%
import pandas as pd
import seaborn as sns
from IPython.display import display

# %% [markdown]
# ### Paso 2: Parametros bases

# %%
n = 50
p_values = [0.2, 0.5, 0.8]
x = np.arange(0, n + 1)

# %% [markdown]
# ### Paso 3: Visualización

# %%
for p in p_values:
    fmp = ss.binom.pmf(x, n, p)
    
    plt.figure(figsize=(8, 5))
    plt.vlines(x, 0, fmp, lw=3, label=f'$n={n}$, $p={p}$')
    
    # Marcamos un valor central
    valor_central = int(n * p)
    prob_puntual = ss.binom.pmf(valor_central, n, p)
    plt.axhline(prob_puntual, color='magenta', linestyle='--', label=f'$P(X={valor_central})={prob_puntual:.3f}$')

    plt.title('Distribución Binomial - Función de Masa de Probabilidad')
    plt.xlabel('Número de Éxitos (k)')
    plt.ylabel('P(X = k)')
    plt.legend()
    plt.grid(True)
    plt.tight_layout()
    plt.show()


# %% [markdown]
# ### 📊 ¿Qué puedes observar?

# %% [markdown]
# 1. **Para \( p = 0.2 \)**:
#    - La distribución está sesgada a la izquierda (asimetría positiva).
#    - La mayoría de los valores se agrupan en bajas cantidades de éxitos.
# 
# 2. **Para \( p = 0.5 \)**:
#    - Distribución simétrica, con la mayor probabilidad centrada en \( k = 25 \).
#    - Se parece mucho a una distribución normal cuando \( n \) es grande.
# 
# 3. **Para \( p = 0.8 \)**:
#    - Sesgo a la derecha (asimetría negativa).
#    - Se concentran los valores en altos números de éxito.

# %% [markdown]
# ## 🧪 ¿Y cómo se diferencia de la normal?

# %% [markdown]
# 
# La binomial **se aproxima** a la normal cuando $n$ es grande y $p$ no es extremo. Esta es la famosa **"aproximación normal a la binomial"**, válida cuando:
# 
# $
# n \cdot p \geq 5 \quad \text{y} \quad n \cdot (1-p) \geq 5
# $

# %% [markdown]
# # ⚽ Caso: Tiros penales en partidos simulados

# %% [markdown]
# - Cada penal tiene probabilidad $p = 0.75$ de éxito.
# - Simula 100 partidos con 5 tiros cada uno.
# - Grafica distribución de éxitos.
# - Calcula la probabilidad de meter al menos 3 goles por tanda.

# %% [markdown]
# ## 🎯 Enunciado del problema
# 
# - Cada penal tiene probabilidad \( p = 0.75 \) de ser **convertido en gol**.
# - En cada partido, un equipo ejecuta **5 tiros penales**.
# - Se simulan **100 partidos**.
# - Objetivos:
#   1. Simular los partidos en Python.
#   2. Graficar la distribución de goles por tanda.
#   3. Calcular la probabilidad de **marcar al menos 3 goles** por tanda.

# %%
# Parámetros
n_penales = 5      # número de penales por partido
p_gol = 0.75       # probabilidad de éxito en cada penal
n_partidos = 100   # partidos simulados

# 🎲 Simulación
np.random.seed(42)
goles_por_partido = np.random.binomial(n=n_penales, p=p_gol, size=n_partidos)

# 📊 Visualización
valores, cuentas = np.unique(goles_por_partido, return_counts=True)
plt.figure(figsize=(8, 5))
plt.bar(valores, cuentas, color='navy', alpha=0.8)
plt.title('Distribución de Goles en 100 Tandas de Penales')
plt.xlabel('Goles marcados en la tanda (de 5 penales)')
plt.ylabel('Frecuencia')
plt.xticks(np.arange(0, n_penales+1))
plt.grid(True)
plt.show()

# 📈 Comparación con distribución teórica
x = np.arange(0, n_penales + 1)
pmf_teorica = ss.binom.pmf(x, n=n_penales, p=p_gol)

plt.figure(figsize=(8, 5))
plt.vlines(x, 0, pmf_teorica, colors='darkorange', lw=5)
plt.title('Distribución Binomial Teórica: P(X = k)')
plt.xlabel('Goles en tanda')
plt.ylabel('P(X = k)')
plt.grid(True)
plt.show()

# ✅ Probabilidad de marcar al menos 3 goles en una tanda
# P(X >= 3) = 1 - P(X <= 2)
prob_3_o_mas = 1 - ss.binom.cdf(2, n=n_penales, p=p_gol)
print(f"📌 Probabilidad de marcar al menos 3 goles: {prob_3_o_mas:.4f} ({prob_3_o_mas*100:.2f}%)")


# %% [markdown]
# ## ✅ Conclusión
# 
# La distribución binomial es fundamental para modelar fenómenos dicotómicos repetitivos. Es ideal como **puente hacia modelos más complejos**, como la distribución normal, y ampliamente usada en pruebas de hipótesis y procesos industriales.


