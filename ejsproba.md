# Cálculo de Función de Regresión $E[X|Y=y]$ con LaTeX

Para calcular la función de regresión $E[X|Y=y]$ con la densidad conjunta dada, seguiré un procedimiento sistemático.

## Datos del problema

- Densidad conjunta: $f(x,y) = 4e^{-2y}$ para $0 < x < y^2$
- Necesito encontrar: $E[X|Y=y]$

## Paso 1: Calcular la densidad marginal de $Y$

$$f_Y(y) = \int f(x,y)dx = \int_{0}^{y^2} 4e^{-2y} \, dx$$  
$$f_Y(y) = 4e^{-2y}[x]_{0}^{y^2}$$  
$$f_Y(y) = 4e^{-2y}(y^2 - 0)$$  
$$f_Y(y) = 4y^2e^{-2y}$$

## Paso 2: Calcular la densidad condicional

$$f(x|y) = \frac{f(x,y)}{f_Y(y)} = \frac{4e^{-2y}}{4y^2e^{-2y}} = \frac{1}{y^2}$$

## Paso 3: Calcular la esperanza condicional

$$E[X|Y=y] = \int x \cdot f(x|y) \, dx = \int_{0}^{y^2} x \cdot \frac{1}{y^2} \, dx$$
$$E[X|Y=y] = \frac{1}{y^2} \cdot \int_{0}^{y^2} x \, dx$$
$$E[X|Y=y] = \frac{1}{y^2} \cdot \left[\frac{x^2}{2}\right]_{0}^{y^2}$$
$$E[X|Y=y] = \frac{1}{y^2} \cdot \left(\frac{(y^2)^2}{2} - 0\right)$$
$$E[X|Y=y] = \frac{1}{y^2} \cdot \frac{y^4}{2}$$
$$E[X|Y=y] = \frac{y^2}{2}$$

Por lo tanto, la función de regresión es $E[X|Y=y] = \frac{y^2}{2}$

# Cálculo de la función de distribución de $W = X - Y + 1$

## Datos del problema

- Vector aleatorio uniforme $(X,Y)$ con:
  - $0 < x < 4$
  - $x-1 < y < x+1$
- Necesitamos hallar la función de distribución de $W = X - Y + 1$

## Paso 1: Determinación del dominio

El dominio original del vector aleatorio es:
$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Este dominio corresponde a una banda de ancho 2, centrada en la recta $y = x$.

## Paso 2: Cálculo del área total del dominio

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

## Paso 3: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesitamos encontrar el área donde $X - Y + 1 \leq w$, o equivalentemente, $Y \geq X + 1 - w$.

### Caso 1: $w \leq 0$

Como $Y \leq X + 1$ siempre, tenemos que $X - Y + 1 \geq 0$, por lo que $W \geq 0$.
$$F_W(w) = 0 \quad \text{para } w \leq 0$$

### Caso 2: $0 < w < 2$

La región donde $W \leq w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+1-w) < y < x+1$$

Como $w < 2$, tenemos que $x+1-w > x-1$, por lo que:
$$0 < x < 4, \quad x+1-w < y < x+1$$

El área de esta región es:
$$A = \int_0^4 \int_{x+1-w}^{x+1} dy \, dx = \int_0^4 w \, dx = 4w$$

Por lo tanto:
$$F_W(w) = \frac{4w}{8} = \frac{w}{2} \quad \text{para } 0 < w < 2$$

### Caso 3: $w \geq 2$

En este caso, la condición $y \geq x+1-w$ es satisfecha por toda la región original, ya que $x+1-w \leq x-1$ para $w \geq 2$.

Por lo tanto:
$$F_W(w) = 1 \quad \text{para } w \geq 2$$

## Función de distribución completa

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq 0 \\
\frac{w}{2} & \text{si } 0 < w < 2 \\
1 & \text{si } w \geq 2
\end{cases}
$$

## Gráfica de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq 0$: Constante igual a 0
- Para $0 < w < 2$: Recta con pendiente $1/2$, partiendo de $(0,0)$ hasta $(2,1)$
- Para $w \geq 2$: Constante igual a 1

Es una función continua, no diferenciable en $w = 0$ y $w = 2$.

# Problema de procesos de Poisson: Roturas de copas

## Enunciado

Alva, Bauti y Charly comienzan sus turnos trabajando de lavacopas en el Bar Gibraltar a las 20:00. Alva rompe copas de acuerdo con un proceso de Poisson de intensidad 1 por hora, Bauti lo hace según un proceso de Poisson de intensidad 5/4 por hora, y Charly (el más cuidadoso) de acuerdo a un proceso de Poisson de intensidad 1/2 por hora; independientes entre sí. Si el sábado entre las 20:00 y las 22:00 rompieron exactamente 5 copas en total, calcular la probabilidad de que Charly no haya roto ninguna en ese intervalo de tiempo.

## Solución

### Datos del problema

- Alva: proceso de Poisson con $\lambda_A = 1$ copa/hora
- Bauti: proceso de Poisson con $\lambda_B = \frac{5}{4}$ copas/hora
- Charly: proceso de Poisson con $\lambda_C = \frac{1}{2}$ copa/hora
- Intervalo de tiempo: 2 horas (de 20:00 a 22:00)
- Número total de copas rotas: 5

### Cálculo de probabilidades

En un proceso de Poisson, cuando se condiciona el número total de eventos, la distribución del número de eventos por cada proceso sigue una multinomial.

La tasa total de roturas es:
$$\lambda_{total} = \lambda_A + \lambda_B + \lambda_C = 1 + \frac{5}{4} + \frac{1}{2} = \frac{11}{4} = 2.75 \text{ copas/hora}$$

Las probabilidades de que una copa rota corresponda a cada persona son:
$$p_A = \frac{\lambda_A}{\lambda_{total}} = \frac{1}{2.75} = \frac{4}{11}$$
$$p_B = \frac{\lambda_B}{\lambda_{total}} = \frac{5/4}{2.75} = \frac{5}{11}$$
$$p_C = \frac{\lambda_C}{\lambda_{total}} = \frac{1/2}{2.75} = \frac{2}{11}$$

La probabilidad de que Charly no haya roto ninguna copa, dado que se rompieron 5 en total:
$$P(N_C = 0 | N_A + N_B + N_C = 5) = P(N_A + N_B = 5 | N_A + N_B + N_C = 5)$$
$$= (p_A + p_B)^5 = \left(1 - p_C\right)^5 = \left(1 - \frac{2}{11}\right)^5 = \left(\frac{9}{11}\right)^5$$

Calculando:
$$\left(\frac{9}{11}\right)^5 = \frac{59049}{161051} \approx 0.3665$$

Por lo tanto, la probabilidad de que Charly no haya roto ninguna copa en ese intervalo de tiempo es aproximadamente 36.65%.

# Análisis del enfoque propuesto para el problema de Poisson

## Enfoque propuesto

Usar la expresión:
$$\frac{P(N_C = 0 \text{ AND } N_A + N_B = 5)}{P(N_A + N_B + N_C = 5)}$$

## Validación del enfoque

Sí, este enfoque es correcto. Estamos aplicando directamente la definición de probabilidad condicional:

$$P(N_C = 0 | N_A + N_B + N_C = 5) = \frac{P(N_C = 0 \text{ AND } N_A + N_B + N_C = 5)}{P(N_A + N_B + N_C = 5)}$$

Y dado que $N_C = 0$ y $N_A + N_B + N_C = 5$ implican que $N_A + N_B = 5$, podemos reescribir:

$$P(N_C = 0 | N_A + N_B + N_C = 5) = \frac{P(N_C = 0 \text{ AND } N_A + N_B = 5)}{P(N_A + N_B + N_C = 5)}$$

## Desarrollo del cálculo

1. $P(N_C = 0)$ en 2 horas: $e^{-\lambda_C \cdot 2} = e^{-0.5 \cdot 2} = e^{-1}$

2. $P(N_A + N_B = 5)$ en 2 horas, con tasa combinada $\lambda_A + \lambda_B = 1 + \frac{5}{4} = \frac{9}{4}$:
   $$P(N_A + N_B = 5) = \frac{(\frac{9}{4} \cdot 2)^5 \cdot e^{-\frac{9}{4} \cdot 2}}{5!} = \frac{(\frac{9}{2})^5 \cdot e^{-\frac{9}{2}}}{5!}$$

3. $P(N_A + N_B + N_C = 5)$ en 2 horas, con tasa total $\lambda_A + \lambda_B + \lambda_C = \frac{11}{4}$:
   $$P(N_A + N_B + N_C = 5) = \frac{(\frac{11}{4} \cdot 2)^5 \cdot e^{-\frac{11}{4} \cdot 2}}{5!} = \frac{(\frac{11}{2})^5 \cdot e^{-\frac{11}{2}}}{5!}$$

4. Como los procesos son independientes:
   $$P(N_C = 0 \text{ AND } N_A + N_B = 5) = P(N_C = 0) \cdot P(N_A + N_B = 5)$$

5. Sustituyendo todo:
   $$\frac{P(N_C = 0) \cdot P(N_A + N_B = 5)}{P(N_A + N_B + N_C = 5)} = \frac{e^{-1} \cdot \frac{(\frac{9}{2})^5 \cdot e^{-\frac{9}{2}}}{5!}}{\frac{(\frac{11}{2})^5 \cdot e^{-\frac{11}{2}}}{5!}}$$

6. Simplificando:
   $$= \frac{e^{-1} \cdot (\frac{9}{2})^5 \cdot e^{-\frac{9}{2}}}{(\frac{11}{2})^5 \cdot e^{-\frac{11}{2}}} = e^{-1-\frac{9}{2}+\frac{11}{2}} \cdot \frac{(\frac{9}{2})^5}{(\frac{11}{2})^5} = e^{0} \cdot \left(\frac{9}{11}\right)^5 = \left(\frac{9}{11}\right)^5$$

Por lo tanto, usando este enfoque llegamos al mismo resultado: $\left(\frac{9}{11}\right)^5 \approx 0.3665$, confirmando que es correcto.

# Aproximación de probabilidad usando el Teorema Central del Límite

## Enunciado del problema

El número de cerezas en una tarta es una variable aleatoria que puede valer 4, 5, 6 o 7; con probabilidades 0.2, 0.4, 0.3, 0.1 respectivamente. Calcular aproximadamente la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5.

## Solución

### Paso 1: Calcular la media y varianza de la variable aleatoria

Sea $X$ la variable aleatoria que representa el número de cerezas en una tarta.

$$P(X=4) = 0.2, \quad P(X=5) = 0.4, \quad P(X=6) = 0.3, \quad P(X=7) = 0.1$$

La **media** (valor esperado) de $X$ es:

$$\mu = E[X] = 4 \cdot 0.2 + 5 \cdot 0.4 + 6 \cdot 0.3 + 7 \cdot 0.1 = 5.3$$

Para calcular la **varianza**, primero hallamos $E[X^2]$:

$$E[X^2] = 4^2 \cdot 0.2 + 5^2 \cdot 0.4 + 6^2 \cdot 0.3 + 7^2 \cdot 0.1 = 28.9$$

Luego, la varianza es:

$$\sigma^2 = E[X^2] - (E[X])^2 = 28.9 - 5.3^2 = 28.9 - 28.09 = 0.81$$

La desviación estándar es $\sigma = \sqrt{0.81} = 0.9$

### Paso 2: Aplicar el Teorema Central del Límite

Sea $\bar{X}_{36}$ el promedio de cerezas en 36 tartas.

Por el Teorema Central del Límite, para $n$ grande (36 es suficientemente grande), la distribución de $\bar{X}_n$ se aproxima a una normal con:

$$\bar{X}_{36} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(5.3, \frac{0.81}{36}\right) = N(5.3, 0.0225)$$

### Paso 3: Calcular la probabilidad requerida

$$P(\bar{X}_{36} < 5.5) = P\left(\frac{\bar{X}_{36} - \mu}{\sigma/\sqrt{n}} < \frac{5.5 - 5.3}{0.9/\sqrt{36}}\right) = P(Z < 1.33)$$

Donde $Z$ es una variable aleatoria normal estándar.

Usando la tabla de la distribución normal o una calculadora:

$$P(Z < 1.33) \approx 0.9082$$

Por lo tanto, la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5 es aproximadamente **0.91** o **91%**.

# Problema de vendedores ambulantes en el subte

## Enunciado

Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos vendedores en el subte.

## Solución usando enfoque combinatorio

Planteamiento
Debemos calcular la probabilidad condicional de que todos los vendedores hayan subido en las estaciones 1-4, dado que exactamente uno subió en la estación 1.

Análisis del problema
Tenemos 8 vendedores que eligen independientemente entre 5 estaciones equiprobables
Ya sabemos que exactamente 1 vendedor subió en la estación 1
Para que todos estén en el subte al salir de la estación 4, los 7 vendedores restantes deben haber subido en las estaciones 2, 3 o 4
Cálculo de la probabilidad
Dado que cada vendedor elige su estación independientemente y con probabilidad uniforme ($p=\frac{1}{5}$ para cada estación), y que ya sabemos que uno subió en la estación 1, los 7 restantes deben elegir entre las estaciones 2, 3, 4 o 5.

Para los 7 vendedores restantes:

Probabilidad de subir en una estación específica (sin condiciones): $\frac{1}{5}$
Probabilidad de subir en las estaciones 2, 3 o 4: $\frac{3}{5}$
Probabilidad de subir en la estación 5: $\frac{1}{5}$
Probabilidad condicional de subir en las estaciones 2, 3 o 4 dado que no subió en la estación 1: $\frac{3/5}{4/5} = \frac{3}{4}$
Por lo tanto, la probabilidad de que todos los 7 vendedores restantes hayan subido en las estaciones 2, 3 o 4 es:

$$P(\text{todos los 7 en estaciones 2-4}) = \left(\frac{3}{4}\right)^7$$

Calculando:

$$\left(\frac{3}{4}\right)^7 = \frac{3^7}{4^7} = \frac{2187}{16384} \approx 0.1335$$

La probabilidad buscada es aproximadamente 13.35%.

Observación sobre Bose-Einstein
Si quisiéramos aplicar un enfoque tipo Bose-Einstein, estaríamos interesados en el número de formas de distribuir los 7 vendedores restantes en 3 estaciones (2, 3 y 4). Sin embargo, como los vendedores eligen independientemente, el enfoque de probabilidad condicional utilizado es más apropiado para este problema.

# Distribución de $W = \frac{Y-X}{2}$ para variables aleatorias uniformes

## Enunciado del problema

Sean las variables aleatorias $X,Y$ uniformes tal que:

$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Hallar y graficar la distribución de $W = \frac{Y-X}{2}$

## Solución

### Paso 1: Análisis del dominio

El dominio $D$ representa una banda diagonal de ancho 2 centrada en la recta $y = x$ y limitada horizontalmente por $x \in (0,4)$.

El área total del dominio es:

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

### Paso 2: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesito transformar la condición:

$$P\left(\frac{Y-X}{2} \leq w\right) = P(Y-X \leq 2w) = P(Y \leq X + 2w)$$

Consideraré diferentes casos según el valor de $w$:

#### Caso 1: $w \leq -\frac{1}{2}$

Si $w \leq -\frac{1}{2}$, entonces $2w \leq -1$.

Como $y > x-1$ (por definición del dominio) y $x+2w \leq x-1$ (ya que $2w \leq -1$), tenemos que $y > x-1 \geq x+2w$.

Por lo tanto, $Y$ siempre es mayor que $X+2w$, lo que significa:
$$F_W(w) = 0 \quad \text{para } w \leq -\frac{1}{2}$$

#### Caso 2: $-\frac{1}{2} < w < \frac{1}{2}$

En este caso, $-1 < 2w < 1$.
La región donde $Y \leq X+2w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+2w) < y < x+1$$

Como $-\frac{1}{2} < w < \frac{1}{2}$, tenemos que $x-1 < x+2w < x+1$, por lo que:
$$0 < x < 4, \quad x-1 < y \leq x+2w$$

El área de esta región es:
$$A = \int_0^4 \int_{x-1}^{x+2w} dy \, dx = \int_0^4 [(x+2w)-(x-1)] \, dx = \int_0^4 (2w+1) \, dx = 4(2w+1)$$

Por lo tanto:
$$F_W(w) = \frac{4(2w+1)}{8} = \frac{2w+1}{2} \quad \text{para } -\frac{1}{2} < w < \frac{1}{2}$$

#### Caso 3: $w \geq \frac{1}{2}$

Si $w \geq \frac{1}{2}$, entonces $2w \geq 1$.

Como $y < x+1$ (por definición del dominio) y $x+2w \geq x+1$ (ya que $2w \geq 1$), tenemos que $y < x+1 \leq x+2w$.

Por lo tanto, $Y$ siempre es menor o igual que $X+2w$, lo que significa:
$$F_W(w) = 1 \quad \text{para } w \geq \frac{1}{2}$$

### Paso 3: Función de distribución completa

La función de distribución acumulada de $W$ es:

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq -\frac{1}{2} \\
\frac{2w+1}{2} & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
1 & \text{si } w \geq \frac{1}{2}
\end{cases}
$$

### Paso 4: Función de densidad de probabilidad

Derivando la función de distribución acumulada, obtenemos la función de densidad:

$$
f_W(w) =
\begin{cases}
0 & \text{si } w < -\frac{1}{2} \\
1 & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
0 & \text{si } w > \frac{1}{2}
\end{cases}
$$

### Conclusión

La variable aleatoria $W = \frac{Y-X}{2}$ sigue una distribución uniforme en el intervalo $[-\frac{1}{2}, \frac{1}{2}]$.

### Gráfico de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq -\frac{1}{2}$: Constante igual a 0
- Para $-\frac{1}{2} < w < \frac{1}{2}$: Recta con pendiente 1, partiendo de $(−\frac{1}{2},0)$ hasta $(\frac{1}{2},1)$
- Para $w \geq \frac{1}{2}$: Constante igual a 1

# Problema de Procesos de Poisson: Clientes conectándose a un servidor

## Enunciado del problema

A y B se conectan a un servidor. Las conexiones que realiza el cliente A ocurren según un proceso de Poisson de 2 por minuto, mientras que para el cliente B ocurren según un proceso de Poisson de 3 por minuto. Los dos procesos de Poisson son independientes. Sabiendo que entre 3:00 y las 3:02 hubo exactamente una conexión al servidor por el cliente A, calcular la probabilidad de que entre 3:00 y 3:05 hayan realizado como máximo 2 conexiones en total.

## Solución

### Datos del problema

- Cliente A: proceso de Poisson con tasa $\lambda_A = 2$ conexiones/minuto
- Cliente B: proceso de Poisson con tasa $\lambda_B = 3$ conexiones/minuto
- Entre 3:00 y 3:02, el cliente A realizó exactamente 1 conexión

### Análisis

Denotemos:

- $N_A(t_1, t_2)$ = número de conexiones del cliente A en el intervalo $(t_1, t_2)$
- $N_B(t_1, t_2)$ = número de conexiones del cliente B en el intervalo $(t_1, t_2)$

Queremos calcular:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1)$$

Sabemos que $N_A(0,5) = N_A(0,2) + N_A(2,5) = 1 + N_A(2,5)$

Por lo tanto:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1) = P(1 + N_A(2,5) + N_B(0,5) \leq 2) = P(N_A(2,5) + N_B(0,5) \leq 1)$$

### Cálculo

Por la propiedad de independencia de incrementos del proceso de Poisson:

- $N_A(2,5)$ sigue una distribución Poisson con parámetro $\lambda_A \cdot 3 = 2 \cdot 3 = 6$
- $N_B(0,5)$ sigue una distribución Poisson con parámetro $\lambda_B \cdot 5 = 3 \cdot 5 = 15$

Por la propiedad de que la suma de variables Poisson independientes también es Poisson:

- $N_A(2,5) + N_B(0,5)$ sigue una distribución Poisson con parámetro $6 + 15 = 21$

Calculamos:
$$P(N_A(2,5) + N_B(0,5) \leq 1) = P(\text{Poisson}(21) \leq 1) = e^{-21} \cdot (1 + 21) = 22 \cdot e^{-21}$$

$$22 \cdot e^{-21} \approx 1.67 \times 10^{-8}$$

La probabilidad pedida es aproximadamente $1.67 \times 10^{-8}$, es decir, extremadamente pequeña (aproximadamente 1 en 60 millones).

# Problema de probabilidad condicional con cajas y bolas

Para resolver este problema, identificaré los eventos y aplicaré el teorema de Bayes.

## Eventos relevantes

- A₁: "Las dos bolas extraídas de C1 son blancas"
- A₂: "Las dos bolas extraídas de C1 son rojas"
- A₃: "Las dos bolas extraídas de C1 son de distinto color"
- B: "La tercera bola extraída es roja"

Necesitamos hallar P(A₂|B).

## Paso 1: Calcular probabilidades del primer evento

En C1 hay 6 bolas blancas y 4 rojas (total 10).

- P(A₁) = C(6,2)/C(10,2) = 15/45 = 1/3
- P(A₂) = C(4,2)/C(10,2) = 6/45 = 2/15
- P(A₃) = 1 - P(A₁) - P(A₂) = 1 - 1/3 - 2/15 = 8/15

## Paso 2: Calcular probabilidades condicionales de B dado cada caso

- Si ocurrió A₁ o A₂, sacamos de C2 (5 blancas, 3 rojas): P(B|A₁) = P(B|A₂) = 3/8
- Si ocurrió A₃, sacamos de C3 (3 blancas, 9 rojas): P(B|A₃) = 9/12 = 3/4

## Paso 3: Calcular P(B) usando la ley de probabilidad total

P(B) = P(B|A₁)P(A₁) + P(B|A₂)P(A₂) + P(B|A₃)P(A₃)
P(B) = (3/8)(1/3) + (3/8)(2/15) + (3/4)(8/15)
P(B) = 1/8 + 1/20 + 2/5 = 5/40 + 2/40 + 16/40 = 23/40

## Paso 4: Aplicar el teorema de Bayes

P(A₂|B) = P(B|A₂)P(A₂)/P(B)
P(A₂|B) = (3/8)(2/15)/(23/40) = (3×2×40)/(8×15×23) = 240/2760 = 2/23

Por lo tanto, la probabilidad de que las dos bolas extraídas de C1 hayan sido rojas, dado que la tercera bola extraída fue roja, es 2/23 ≈ 0.087 (aproximadamente 8.7%).

# Problema de probabilidad: tiempo de espera en el cine

## Enunciado

Nicolás quiere ir a ver su película favorita al cine, que tiene funciones a las 18:00 y a las 23:00. La hora a la que sale de su casa es una variable aleatoria con distribución uniforme entre las 16:00 y las 21:00. Independientemente de la hora de salida, el tiempo de viaje hasta el cine (en horas) es una variable aleatoria con distribución uniforme en el intervalo $(1,2)$. ¿Cuál es la probabilidad de que tenga que esperar más de media hora en el cine hasta que empiece su película?

## Solución

### Definición de variables

- $X$: hora de salida (uniforme en $[16,21]$)
- $Y$: tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: hora de llegada al cine

### Análisis del problema

Para que Nicolás tenga que esperar más de media hora, debe llegar al cine antes de las 17:30, ya que la primera función es a las 18:00.

Necesitamos calcular $P(X+Y < 17.5)$

### Densidades de probabilidad

- $f_X(x) = \frac{1}{21-16} = \frac{1}{5}$ para $16 \leq x \leq 21$
- $f_Y(y) = \frac{1}{2-1} = 1$ para $1 \leq y \leq 2$
- $f_{X,Y}(x,y) = \frac{1}{5} \cdot 1 = \frac{1}{5}$ (por independencia)

### Cálculo de la probabilidad

Identificamos la región donde $X+Y < 17.5$ dentro del dominio $[16,21] \times [1,2]$:

La recta $x+y=17.5$ interseca el dominio formando un triángulo con vértices en $(16,1)$, $(16,1.5)$ y $(16.5,1)$.

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (17.5-x-1) \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (16.5-x) \, dx$$

$$= \frac{1}{5} \cdot \left[16.5x - \frac{x^2}{2}\right]_{16}^{16.5}$$

$$= \frac{1}{5} \cdot \left[(16.5 \cdot 16.5 - \frac{16.5^2}{2}) - (16.5 \cdot 16 - \frac{16^2}{2})\right]$$

$$= \frac{1}{5} \cdot [272.25 - 136.125 - 264 + 128]$$

$$= \frac{1}{5} \cdot 0.125 = 0.025$$

### Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine hasta que empiece su película es $0.025$ o $2.5\%$.

# Análisis de probabilidad del tiempo de espera en el cine

Tienes razón, mi análisis anterior fue incorrecto. Debo considerar ambas funciones de cine (18:00 y 23:00) para determinar correctamente cuándo Nicolás esperará más de media hora.

## Planteamiento correcto

Analizaré los posibles escenarios de llegada de Nicolás al cine:

### Variables

- $X$: Hora de salida de casa ($X \sim U(16,21)$)
- $Y$: Tiempo de viaje ($Y \sim U(1,2)$)
- $X+Y$: Hora de llegada al cine

### Casos a considerar

1. Si $X+Y < 17.5$: Llega para la función de 18:00 y espera más de media hora
2. Si $17.5 \leq X+Y < 18$: Llega para la función de 18:00 pero espera menos de media hora
3. Si $18 \leq X+Y < 22.5$: Llega después de la función de 18:00 y debe esperar a la de 23:00 (más de media hora)
4. Si $22.5 \leq X+Y \leq 23$: Llega para la función de 23:00 y espera menos de media hora

Por lo tanto, Nicolás esperará más de media hora en los casos 1 y 3, y la probabilidad buscada es:
$P(X+Y < 17.5) + P(18 \leq X+Y < 22.5)$

## Cálculo de la probabilidad

### Para $P(X+Y < 17.5)$:

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx = \frac{0.125}{5} = 0.025$$

### Para $P(18 \leq X+Y < 22.5)$:

Divido esta región en tres partes:

$$
\begin{align*}
P(18 \leq X+Y < 22.5) &= \int_{16}^{17} \int_{18-x}^{2} \frac{1}{5} \, dy \, dx + \int_{17}^{20.5} \int_{1}^{2} \frac{1}{5} \, dy \, dx + \int_{20.5}^{21} \int_{1}^{22.5-x} \frac{1}{5} \, dy \, dx\\
&= 0.1 + 0.7 + 0.075\\
&= 0.875
\end{align*}
$$

### Probabilidad total

$$P(\text{espera} > 30 \text{ min}) = 0.025 + 0.875 = 0.9$$

## Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine es $0.9$ o $90\%$.

# Problema de la Distribución de Cerezas

## Enunciado

El número de cerezas en una tarta es una variable aleatoria que puede valer 4, 5, 6 o 7; con probabilidades 0.2, 0.4, 0.3, 0.1 respectivamente. Calcular aproximadamente la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5.

## Solución

### Paso 1: Calcular la media y varianza de la variable aleatoria

Sea $X$ la variable aleatoria que representa el número de cerezas en una tarta.

$$P(X=4) = 0.2, \quad P(X=5) = 0.4, \quad P(X=6) = 0.3, \quad P(X=7) = 0.1$$

La **media** (valor esperado) de $X$ es:

$$\mu = E[X] = 4 \cdot 0.2 + 5 \cdot 0.4 + 6 \cdot 0.3 + 7 \cdot 0.1 = 5.3$$

Para calcular la **varianza**, primero hallamos $E[X^2]$:

$$E[X^2] = 4^2 \cdot 0.2 + 5^2 \cdot 0.4 + 6^2 \cdot 0.3 + 7^2 \cdot 0.1 = 28.9$$

Luego, la varianza es:

$$\sigma^2 = E[X^2] - (E[X])^2 = 28.9 - 5.3^2 = 28.9 - 28.09 = 0.81$$

La desviación estándar es $\sigma = \sqrt{0.81} = 0.9$

### Paso 2: Aplicar el Teorema Central del Límite

Sea $\bar{X}_{36}$ el promedio de cerezas en 36 tartas.

Por el Teorema Central del Límite, para $n$ grande (36 es suficientemente grande), la distribución de $\bar{X}_n$ se aproxima a una normal con:

$$\bar{X}_{36} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(5.3, \frac{0.81}{36}\right) = N(5.3, 0.0225)$$

### Paso 3: Calcular la probabilidad requerida

$$P(\bar{X}_{36} < 5.5) = P\left(\frac{\bar{X}_{36} - \mu}{\sigma/\sqrt{n}} < \frac{5.5 - 5.3}{0.9/\sqrt{36}}\right) = P(Z < 1.33)$$

Donde $Z$ es una variable aleatoria normal estándar.

Usando la tabla de la distribución normal o una calculadora:

$$P(Z < 1.33) \approx 0.9082$$

Por lo tanto, la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5 es aproximadamente **0.91** o **91%**.

# Problema de vendedores ambulantes en el subte

## Enunciado

Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos vendedores en el subte.

## Solución usando enfoque combinatorio

Planteamiento
Debemos calcular la probabilidad condicional de que todos los vendedores hayan subido en las estaciones 1-4, dado que exactamente uno subió en la estación 1.

Análisis del problema
Tenemos 8 vendedores que eligen independientemente entre 5 estaciones equiprobables
Ya sabemos que exactamente 1 vendedor subió en la estación 1
Para que todos estén en el subte al salir de la estación 4, los 7 vendedores restantes deben haber subido en las estaciones 2, 3 o 4
Cálculo de la probabilidad
Dado que cada vendedor elige su estación independientemente y con probabilidad uniforme ($p=\frac{1}{5}$ para cada estación), y que ya sabemos que uno subió en la estación 1, los 7 restantes deben elegir entre las estaciones 2, 3, 4 o 5.

Para los 7 vendedores restantes:

Probabilidad de subir en una estación específica (sin condiciones): $\frac{1}{5}$
Probabilidad de subir en las estaciones 2, 3 o 4: $\frac{3}{5}$
Probabilidad de subir en la estación 5: $\frac{1}{5}$
Probabilidad condicional de subir en las estaciones 2, 3 o 4 dado que no subió en la estación 1: $\frac{3/5}{4/5} = \frac{3}{4}$
Por lo tanto, la probabilidad de que todos los 7 vendedores restantes hayan subido en las estaciones 2, 3 o 4 es:

$$P(\text{todos los 7 en estaciones 2-4}) = \left(\frac{3}{4}\right)^7$$

Calculando:

$$\left(\frac{3}{4}\right)^7 = \frac{3^7}{4^7} = \frac{2187}{16384} \approx 0.1335$$

La probabilidad buscada es aproximadamente 13.35%.

Observación sobre Bose-Einstein
Si quisiéramos aplicar un enfoque tipo Bose-Einstein, estaríamos interesados en el número de formas de distribuir los 7 vendedores restantes en 3 estaciones (2, 3 y 4). Sin embargo, como los vendedores eligen independientemente, el enfoque de probabilidad condicional utilizado es más apropiado para este problema.

# Distribución de $W = \frac{Y-X}{2}$ para variables aleatorias uniformes

## Enunciado del problema

Sean las variables aleatorias $X,Y$ uniformes tal que:

$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Hallar y graficar la distribución de $W = \frac{Y-X}{2}$

## Solución

### Paso 1: Análisis del dominio

El dominio $D$ representa una banda diagonal de ancho 2 centrada en la recta $y = x$ y limitada horizontalmente por $x \in (0,4)$.

El área total del dominio es:

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

### Paso 2: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesito transformar la condición:

$$P\left(\frac{Y-X}{2} \leq w\right) = P(Y-X \leq 2w) = P(Y \leq X + 2w)$$

Consideraré diferentes casos según el valor de $w$:

#### Caso 1: $w \leq -\frac{1}{2}$

Si $w \leq -\frac{1}{2}$, entonces $2w \leq -1$.

Como $y > x-1$ (por definición del dominio) y $x+2w \leq x-1$ (ya que $2w \leq -1$), tenemos que $y > x-1 \geq x+2w$.

Por lo tanto, $Y$ siempre es mayor que $X+2w$, lo que significa:
$$F_W(w) = 0 \quad \text{para } w \leq -\frac{1}{2}$$

#### Caso 2: $-\frac{1}{2} < w < \frac{1}{2}$

En este caso, $-1 < 2w < 1$.
La región donde $Y \leq X+2w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+2w) < y < x+1$$

Como $-\frac{1}{2} < w < \frac{1}{2}$, tenemos que $x-1 < x+2w < x+1$, por lo que:
$$0 < x < 4, \quad x-1 < y \leq x+2w$$

El área de esta región es:
$$A = \int_0^4 \int_{x-1}^{x+2w} dy \, dx = \int_0^4 [(x+2w)-(x-1)] \, dx = \int_0^4 (2w+1) \, dx = 4(2w+1)$$

Por lo tanto:
$$F_W(w) = \frac{4(2w+1)}{8} = \frac{2w+1}{2} \quad \text{para } -\frac{1}{2} < w < \frac{1}{2}$$

#### Caso 3: $w \geq \frac{1}{2}$

Si $w \geq \frac{1}{2}$, entonces $2w \geq 1$.

Como $y < x+1$ (por definición del dominio) y $x+2w \geq x+1$ (ya que $2w \geq 1$), tenemos que $y < x+1 \leq x+2w$.

Por lo tanto, $Y$ siempre es menor o igual que $X+2w$, lo que significa:
$$F_W(w) = 1 \quad \text{para } w \geq \frac{1}{2}$$

### Paso 3: Función de distribución completa

La función de distribución acumulada de $W$ es:

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq -\frac{1}{2} \\
\frac{2w+1}{2} & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
1 & \text{si } w \geq \frac{1}{2}
\end{cases}
$$

### Paso 4: Función de densidad de probabilidad

Derivando la función de distribución acumulada, obtenemos la función de densidad:

$$
f_W(w) =
\begin{cases}
0 & \text{si } w < -\frac{1}{2} \\
1 & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
0 & \text{si } w > \frac{1}{2}
\end{cases}
$$

### Conclusión

La variable aleatoria $W = \frac{Y-X}{2}$ sigue una distribución uniforme en el intervalo $[-\frac{1}{2}, \frac{1}{2}]$.

### Gráfico de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq -\frac{1}{2}$: Constante igual a 0
- Para $-\frac{1}{2} < w < \frac{1}{2}$: Recta con pendiente 1, partiendo de $(−\frac{1}{2},0)$ hasta $(\frac{1}{2},1)$
- Para $w \geq \frac{1}{2}$: Constante igual a 1

# Problema de Procesos de Poisson: Clientes conectándose a un servidor

## Enunciado del problema

A y B se conectan a un servidor. Las conexiones que realiza el cliente A ocurren según un proceso de Poisson de 2 por minuto, mientras que para el cliente B ocurren según un proceso de Poisson de 3 por minuto. Los dos procesos de Poisson son independientes. Sabiendo que entre 3:00 y las 3:02 hubo exactamente una conexión al servidor por el cliente A, calcular la probabilidad de que entre 3:00 y 3:05 hayan realizado como máximo 2 conexiones en total.

## Solución

### Datos del problema

- Cliente A: proceso de Poisson con tasa $\lambda_A = 2$ conexiones/minuto
- Cliente B: proceso de Poisson con tasa $\lambda_B = 3$ conexiones/minuto
- Entre 3:00 y 3:02, el cliente A realizó exactamente 1 conexión

### Análisis

Denotemos:

- $N_A(t_1, t_2)$ = número de conexiones del cliente A en el intervalo $(t_1, t_2)$
- $N_B(t_1, t_2)$ = número de conexiones del cliente B en el intervalo $(t_1, t_2)$

Queremos calcular:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1)$$

Sabemos que $N_A(0,5) = N_A(0,2) + N_A(2,5) = 1 + N_A(2,5)$

Por lo tanto:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1) = P(1 + N_A(2,5) + N_B(0,5) \leq 2) = P(N_A(2,5) + N_B(0,5) \leq 1)$$

### Cálculo

Por la propiedad de independencia de incrementos del proceso de Poisson:

- $N_A(2,5)$ sigue una distribución Poisson con parámetro $\lambda_A \cdot 3 = 2 \cdot 3 = 6$
- $N_B(0,5)$ sigue una distribución Poisson con parámetro $\lambda_B \cdot 5 = 3 \cdot 5 = 15$

Por la propiedad de que la suma de variables Poisson independientes también es Poisson:

- $N_A(2,5) + N_B(0,5)$ sigue una distribución Poisson con parámetro $6 + 15 = 21$

Calculamos:
$$P(N_A(2,5) + N_B(0,5) \leq 1) = P(\text{Poisson}(21) \leq 1) = e^{-21} \cdot (1 + 21) = 22 \cdot e^{-21}$$

$$22 \cdot e^{-21} \approx 1.67 \times 10^{-8}$$

La probabilidad pedida es aproximadamente $1.67 \times 10^{-8}$, es decir, extremadamente pequeña (aproximadamente 1 en 60 millones).

# Problema de probabilidad condicional con cajas y bolas

Para resolver este problema, identificaré los eventos y aplicaré el teorema de Bayes.

## Eventos relevantes

- A₁: "Las dos bolas extraídas de C1 son blancas"
- A₂: "Las dos bolas extraídas de C1 son rojas"
- A₃: "Las dos bolas extraídas de C1 son de distinto color"
- B: "La tercera bola extraída es roja"

Necesitamos hallar P(A₂|B).

## Paso 1: Calcular probabilidades del primer evento

En C1 hay 6 bolas blancas y 4 rojas (total 10).

- P(A₁) = C(6,2)/C(10,2) = 15/45 = 1/3
- P(A₂) = C(4,2)/C(10,2) = 6/45 = 2/15
- P(A₃) = 1 - P(A₁) - P(A₂) = 1 - 1/3 - 2/15 = 8/15

## Paso 2: Calcular probabilidades condicionales de B dado cada caso

- Si ocurrió A₁ o A₂, sacamos de C2 (5 blancas, 3 rojas): P(B|A₁) = P(B|A₂) = 3/8
- Si ocurrió A₃, sacamos de C3 (3 blancas, 9 rojas): P(B|A₃) = 9/12 = 3/4

## Paso 3: Calcular P(B) usando la ley de probabilidad total

P(B) = P(B|A₁)P(A₁) + P(B|A₂)P(A₂) + P(B|A₃)P(A₃)
P(B) = (3/8)(1/3) + (3/8)(2/15) + (3/4)(8/15)
P(B) = 1/8 + 1/20 + 2/5 = 5/40 + 2/40 + 16/40 = 23/40

## Paso 4: Aplicar el teorema de Bayes

P(A₂|B) = P(B|A₂)P(A₂)/P(B)
P(A₂|B) = (3/8)(2/15)/(23/40) = (3×2×40)/(8×15×23) = 240/2760 = 2/23

Por lo tanto, la probabilidad de que las dos bolas extraídas de C1 hayan sido rojas, dado que la tercera bola extraída fue roja, es 2/23 ≈ 0.087 (aproximadamente 8.7%).

# Problema de probabilidad: tiempo de espera en el cine

## Enunciado

Nicolás quiere ir a ver su película favorita al cine, que tiene funciones a las 18:00 y a las 23:00. La hora a la que sale de su casa es una variable aleatoria con distribución uniforme entre las 16:00 y las 21:00. Independientemente de la hora de salida, el tiempo de viaje hasta el cine (en horas) es una variable aleatoria con distribución uniforme en el intervalo $(1,2)$. ¿Cuál es la probabilidad de que tenga que esperar más de media hora en el cine hasta que empiece su película?

## Solución

### Definición de variables

- $X$: hora de salida (uniforme en $[16,21]$)
- $Y$: tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: hora de llegada al cine

### Análisis del problema

Para que Nicolás tenga que esperar más de media hora, debe llegar al cine antes de las 17:30, ya que la primera función es a las 18:00.

Necesitamos calcular $P(X+Y < 17.5)$

### Densidades de probabilidad

- $f_X(x) = \frac{1}{21-16} = \frac{1}{5}$ para $16 \leq x \leq 21$
- $f_Y(y) = \frac{1}{2-1} = 1$ para $1 \leq y \leq 2$
- $f_{X,Y}(x,y) = \frac{1}{5} \cdot 1 = \frac{1}{5}$ (por independencia)

### Cálculo de la probabilidad

Identificamos la región donde $X+Y < 17.5$ dentro del dominio $[16,21] \times [1,2]$:

La recta $x+y=17.5$ interseca el dominio formando un triángulo con vértices en $(16,1)$, $(16,1.5)$ y $(16.5,1)$.

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (17.5-x-1) \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (16.5-x) \, dx$$

$$= \frac{1}{5} \cdot \left[16.5x - \frac{x^2}{2}\right]_{16}^{16.5}$$

$$= \frac{1}{5} \cdot \left[(16.5 \cdot 16.5 - \frac{16.5^2}{2}) - (16.5 \cdot 16 - \frac{16^2}{2})\right]$$

$$= \frac{1}{5} \cdot [272.25 - 136.125 - 264 + 128]$$

$$= \frac{1}{5} \cdot 0.125 = 0.025$$

### Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine hasta que empiece su película es $0.025$ o $2.5\%$.

# Análisis de probabilidad del tiempo de espera en el cine

Tienes razón, mi análisis anterior fue incorrecto. Debo considerar ambas funciones de cine (18:00 y 23:00) para determinar correctamente cuándo Nicolás esperará más de media hora.

## Planteamiento correcto

Analizaré los posibles escenarios de llegada de Nicolás al cine:

### Variables

- $X$: Hora de salida de casa ($X \sim U(16,21)$)
- $Y$: Tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: Hora de llegada al cine

### Casos a considerar

1. Si $X+Y < 17.5$: Llega para la función de 18:00 y espera más de media hora
2. Si $17.5 \leq X+Y < 18$: Llega para la función de 18:00 pero espera menos de media hora
3. Si $18 \leq X+Y < 22.5$: Llega después de la función de 18:00 y debe esperar a la de 23:00 (más de media hora)
4. Si $22.5 \leq X+Y \leq 23$: Llega para la función de 23:00 y espera menos de media hora

Por lo tanto, Nicolás esperará más de media hora en los casos 1 y 3, y la probabilidad buscada es:
$P(X+Y < 17.5) + P(18 \leq X+Y < 22.5)$

## Cálculo de la probabilidad

### Para $P(X+Y < 17.5)$:

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx = \frac{0.125}{5} = 0.025$$

### Para $P(18 \leq X+Y < 22.5)$:

Divido esta región en tres partes:

$$
\begin{align*}
P(18 \leq X+Y < 22.5) &= \int_{16}^{17} \int_{18-x}^{2} \frac{1}{5} \, dy \, dx + \int_{17}^{20.5} \int_{1}^{2} \frac{1}{5} \, dy \, dx + \int_{20.5}^{21} \int_{1}^{22.5-x} \frac{1}{5} \, dy \, dx\\
&= 0.1 + 0.7 + 0.075\\
&= 0.875
\end{align*}
$$

### Probabilidad total

$$P(\text{espera} > 30 \text{ min}) = 0.025 + 0.875 = 0.9$$

## Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine es $0.9$ o $90\%$.

# Problema de la Distribución de Cerezas

## Enunciado

El número de cerezas en una tarta es una variable aleatoria que puede valer 4, 5, 6 o 7; con probabilidades 0.2, 0.4, 0.3, 0.1 respectivamente. Calcular aproximadamente la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5.

## Solución

### Paso 1: Calcular la media y varianza de la variable aleatoria

Sea $X$ la variable aleatoria que representa el número de cerezas en una tarta.

$$P(X=4) = 0.2, \quad P(X=5) = 0.4, \quad P(X=6) = 0.3, \quad P(X=7) = 0.1$$

La **media** (valor esperado) de $X$ es:

$$\mu = E[X] = 4 \cdot 0.2 + 5 \cdot 0.4 + 6 \cdot 0.3 + 7 \cdot 0.1 = 5.3$$

Para calcular la **varianza**, primero hallamos $E[X^2]$:

$$E[X^2] = 4^2 \cdot 0.2 + 5^2 \cdot 0.4 + 6^2 \cdot 0.3 + 7^2 \cdot 0.1 = 28.9$$

Luego, la varianza es:

$$\sigma^2 = E[X^2] - (E[X])^2 = 28.9 - 5.3^2 = 28.9 - 28.09 = 0.81$$

La desviación estándar es $\sigma = \sqrt{0.81} = 0.9$

### Paso 2: Aplicar el Teorema Central del Límite

Sea $\bar{X}_{36}$ el promedio de cerezas en 36 tartas.

Por el Teorema Central del Límite, para $n$ grande (36 es suficientemente grande), la distribución de $\bar{X}_n$ se aproxima a una normal con:

$$\bar{X}_{36} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(5.3, \frac{0.81}{36}\right) = N(5.3, 0.0225)$$

### Paso 3: Calcular la probabilidad requerida

$$P(\bar{X}_{36} < 5.5) = P\left(\frac{\bar{X}_{36} - \mu}{\sigma/\sqrt{n}} < \frac{5.5 - 5.3}{0.9/\sqrt{36}}\right) = P(Z < 1.33)$$

Donde $Z$ es una variable aleatoria normal estándar.

Usando la tabla de la distribución normal o una calculadora:

$$P(Z < 1.33) \approx 0.9082$$

Por lo tanto, la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5 es aproximadamente **0.91** o **91%**.

# Problema de vendedores ambulantes en el subte

## Enunciado

Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos vendedores en el subte.

## Solución usando enfoque combinatorio

Planteamiento
Debemos calcular la probabilidad condicional de que todos los vendedores hayan subido en las estaciones 1-4, dado que exactamente uno subió en la estación 1.

Análisis del problema
Tenemos 8 vendedores que eligen independientemente entre 5 estaciones equiprobables
Ya sabemos que exactamente 1 vendedor subió en la estación 1
Para que todos estén en el subte al salir de la estación 4, los 7 vendedores restantes deben haber subido en las estaciones 2, 3 o 4
Cálculo de la probabilidad
Dado que cada vendedor elige su estación independientemente y con probabilidad uniforme ($p=\frac{1}{5}$ para cada estación), y que ya sabemos que uno subió en la estación 1, los 7 restantes deben elegir entre las estaciones 2, 3, 4 o 5.

Para los 7 vendedores restantes:

Probabilidad de subir en una estación específica (sin condiciones): $\frac{1}{5}$
Probabilidad de subir en las estaciones 2, 3 o 4: $\frac{3}{5}$
Probabilidad de subir en la estación 5: $\frac{1}{5}$
Probabilidad condicional de subir en las estaciones 2, 3 o 4 dado que no subió en la estación 1: $\frac{3/5}{4/5} = \frac{3}{4}$
Por lo tanto, la probabilidad de que todos los 7 vendedores restantes hayan subido en las estaciones 2, 3 o 4 es:

$$P(\text{todos los 7 en estaciones 2-4}) = \left(\frac{3}{4}\right)^7$$

Calculando:

$$\left(\frac{3}{4}\right)^7 = \frac{3^7}{4^7} = \frac{2187}{16384} \approx 0.1335$$

La probabilidad buscada es aproximadamente 13.35%.

Observación sobre Bose-Einstein
Si quisiéramos aplicar un enfoque tipo Bose-Einstein, estaríamos interesados en el número de formas de distribuir los 7 vendedores restantes en 3 estaciones (2, 3 y 4). Sin embargo, como los vendedores eligen independientemente, el enfoque de probabilidad condicional utilizado es más apropiado para este problema.

# Distribución de $W = \frac{Y-X}{2}$ para variables aleatorias uniformes

## Enunciado del problema

Sean las variables aleatorias $X,Y$ uniformes tal que:

$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Hallar y graficar la distribución de $W = \frac{Y-X}{2}$

## Solución

### Paso 1: Análisis del dominio

El dominio $D$ representa una banda diagonal de ancho 2 centrada en la recta $y = x$ y limitada horizontalmente por $x \in (0,4)$.

El área total del dominio es:

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

### Paso 2: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesito transformar la condición:

$$P\left(\frac{Y-X}{2} \leq w\right) = P(Y-X \leq 2w) = P(Y \leq X + 2w)$$

Consideraré diferentes casos según el valor de $w$:

#### Caso 1: $w \leq -\frac{1}{2}$

Si $w \leq -\frac{1}{2}$, entonces $2w \leq -1$.

Como $y > x-1$ (por definición del dominio) y $x+2w \leq x-1$ (ya que $2w \leq -1$), tenemos que $y > x-1 \geq x+2w$.

Por lo tanto, $Y$ siempre es mayor que $X+2w$, lo que significa:
$$F_W(w) = 0 \quad \text{para } w \leq -\frac{1}{2}$$

#### Caso 2: $-\frac{1}{2} < w < \frac{1}{2}$

En este caso, $-1 < 2w < 1$.
La región donde $Y \leq X+2w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+2w) < y < x+1$$

Como $-\frac{1}{2} < w < \frac{1}{2}$, tenemos que $x-1 < x+2w < x+1$, por lo que:
$$0 < x < 4, \quad x-1 < y \leq x+2w$$

El área de esta región es:
$$A = \int_0^4 \int_{x-1}^{x+2w} dy \, dx = \int_0^4 [(x+2w)-(x-1)] \, dx = \int_0^4 (2w+1) \, dx = 4(2w+1)$$

Por lo tanto:
$$F_W(w) = \frac{4(2w+1)}{8} = \frac{2w+1}{2} \quad \text{para } -\frac{1}{2} < w < \frac{1}{2}$$

#### Caso 3: $w \geq \frac{1}{2}$

Si $w \geq \frac{1}{2}$, entonces $2w \geq 1$.

Como $y < x+1$ (por definición del dominio) y $x+2w \geq x+1$ (ya que $2w \geq 1$), tenemos que $y < x+1 \leq x+2w$.

Por lo tanto, $Y$ siempre es menor o igual que $X+2w$, lo que significa:
$$F_W(w) = 1 \quad \text{para } w \geq \frac{1}{2}$$

### Paso 3: Función de distribución completa

La función de distribución acumulada de $W$ es:

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq -\frac{1}{2} \\
\frac{2w+1}{2} & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
1 & \text{si } w \geq \frac{1}{2}
\end{cases}
$$

### Paso 4: Función de densidad de probabilidad

Derivando la función de distribución acumulada, obtenemos la función de densidad:

$$
f_W(w) =
\begin{cases}
0 & \text{si } w < -\frac{1}{2} \\
1 & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
0 & \text{si } w > \frac{1}{2}
\end{cases}
$$

### Conclusión

La variable aleatoria $W = \frac{Y-X}{2}$ sigue una distribución uniforme en el intervalo $[-\frac{1}{2}, \frac{1}{2}]$.

### Gráfico de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq -\frac{1}{2}$: Constante igual a 0
- Para $-\frac{1}{2} < w < \frac{1}{2}$: Recta con pendiente 1, partiendo de $(−\frac{1}{2},0)$ hasta $(\frac{1}{2},1)$
- Para $w \geq \frac{1}{2}$: Constante igual a 1

# Problema de Procesos de Poisson: Clientes conectándose a un servidor

## Enunciado del problema

A y B se conectan a un servidor. Las conexiones que realiza el cliente A ocurren según un proceso de Poisson de 2 por minuto, mientras que para el cliente B ocurren según un proceso de Poisson de 3 por minuto. Los dos procesos de Poisson son independientes. Sabiendo que entre 3:00 y las 3:02 hubo exactamente una conexión al servidor por el cliente A, calcular la probabilidad de que entre 3:00 y 3:05 hayan realizado como máximo 2 conexiones en total.

## Solución

### Datos del problema

- Cliente A: proceso de Poisson con tasa $\lambda_A = 2$ conexiones/minuto
- Cliente B: proceso de Poisson con tasa $\lambda_B = 3$ conexiones/minuto
- Entre 3:00 y 3:02, el cliente A realizó exactamente 1 conexión

### Análisis

Denotemos:

- $N_A(t_1, t_2)$ = número de conexiones del cliente A en el intervalo $(t_1, t_2)$
- $N_B(t_1, t_2)$ = número de conexiones del cliente B en el intervalo $(t_1, t_2)$

Queremos calcular:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1)$$

Sabemos que $N_A(0,5) = N_A(0,2) + N_A(2,5) = 1 + N_A(2,5)$

Por lo tanto:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1) = P(1 + N_A(2,5) + N_B(0,5) \leq 2) = P(N_A(2,5) + N_B(0,5) \leq 1)$$

### Cálculo

Por la propiedad de independencia de incrementos del proceso de Poisson:

- $N_A(2,5)$ sigue una distribución Poisson con parámetro $\lambda_A \cdot 3 = 2 \cdot 3 = 6$
- $N_B(0,5)$ sigue una distribución Poisson con parámetro $\lambda_B \cdot 5 = 3 \cdot 5 = 15$

Por la propiedad de que la suma de variables Poisson independientes también es Poisson:

- $N_A(2,5) + N_B(0,5)$ sigue una distribución Poisson con parámetro $6 + 15 = 21$

Calculamos:
$$P(N_A(2,5) + N_B(0,5) \leq 1) = P(\text{Poisson}(21) \leq 1) = e^{-21} \cdot (1 + 21) = 22 \cdot e^{-21}$$

$$22 \cdot e^{-21} \approx 1.67 \times 10^{-8}$$

La probabilidad pedida es aproximadamente $1.67 \times 10^{-8}$, es decir, extremadamente pequeña (aproximadamente 1 en 60 millones).

# Problema de probabilidad condicional con cajas y bolas

Para resolver este problema, identificaré los eventos y aplicaré el teorema de Bayes.

## Eventos relevantes

- A₁: "Las dos bolas extraídas de C1 son blancas"
- A₂: "Las dos bolas extraídas de C1 son rojas"
- A₃: "Las dos bolas extraídas de C1 son de distinto color"
- B: "La tercera bola extraída es roja"

Necesitamos hallar P(A₂|B).

## Paso 1: Calcular probabilidades del primer evento

En C1 hay 6 bolas blancas y 4 rojas (total 10).

- P(A₁) = C(6,2)/C(10,2) = 15/45 = 1/3
- P(A₂) = C(4,2)/C(10,2) = 6/45 = 2/15
- P(A₃) = 1 - P(A₁) - P(A₂) = 1 - 1/3 - 2/15 = 8/15

## Paso 2: Calcular probabilidades condicionales de B dado cada caso

- Si ocurrió A₁ o A₂, sacamos de C2 (5 blancas, 3 rojas): P(B|A₁) = P(B|A₂) = 3/8
- Si ocurrió A₃, sacamos de C3 (3 blancas, 9 rojas): P(B|A₃) = 9/12 = 3/4

## Paso 3: Calcular P(B) usando la ley de probabilidad total

P(B) = P(B|A₁)P(A₁) + P(B|A₂)P(A₂) + P(B|A₃)P(A₃)
P(B) = (3/8)(1/3) + (3/8)(2/15) + (3/4)(8/15)
P(B) = 1/8 + 1/20 + 2/5 = 5/40 + 2/40 + 16/40 = 23/40

## Paso 4: Aplicar el teorema de Bayes

P(A₂|B) = P(B|A₂)P(A₂)/P(B)
P(A₂|B) = (3/8)(2/15)/(23/40) = (3×2×40)/(8×15×23) = 240/2760 = 2/23

Por lo tanto, la probabilidad de que las dos bolas extraídas de C1 hayan sido rojas, dado que la tercera bola extraída fue roja, es 2/23 ≈ 0.087 (aproximadamente 8.7%).

# Problema de probabilidad: tiempo de espera en el cine

## Enunciado

Nicolás quiere ir a ver su película favorita al cine, que tiene funciones a las 18:00 y a las 23:00. La hora a la que sale de su casa es una variable aleatoria con distribución uniforme entre las 16:00 y las 21:00. Independientemente de la hora de salida, el tiempo de viaje hasta el cine (en horas) es una variable aleatoria con distribución uniforme en el intervalo $(1,2)$. ¿Cuál es la probabilidad de que tenga que esperar más de media hora en el cine hasta que empiece su película?

## Solución

### Definición de variables

- $X$: hora de salida (uniforme en $[16,21]$)
- $Y$: tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: hora de llegada al cine

### Análisis del problema

Para que Nicolás tenga que esperar más de media hora, debe llegar al cine antes de las 17:30, ya que la primera función es a las 18:00.

Necesitamos calcular $P(X+Y < 17.5)$

### Densidades de probabilidad

- $f_X(x) = \frac{1}{21-16} = \frac{1}{5}$ para $16 \leq x \leq 21$
- $f_Y(y) = \frac{1}{2-1} = 1$ para $1 \leq y \leq 2$
- $f_{X,Y}(x,y) = \frac{1}{5} \cdot 1 = \frac{1}{5}$ (por independencia)

### Cálculo de la probabilidad

Identificamos la región donde $X+Y < 17.5$ dentro del dominio $[16,21] \times [1,2]$:

La recta $x+y=17.5$ interseca el dominio formando un triángulo con vértices en $(16,1)$, $(16,1.5)$ y $(16.5,1)$.

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (17.5-x-1) \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (16.5-x) \, dx$$

$$= \frac{1}{5} \cdot \left[16.5x - \frac{x^2}{2}\right]_{16}^{16.5}$$

$$= \frac{1}{5} \cdot \left[(16.5 \cdot 16.5 - \frac{16.5^2}{2}) - (16.5 \cdot 16 - \frac{16^2}{2})\right]$$

$$= \frac{1}{5} \cdot [272.25 - 136.125 - 264 + 128]$$

$$= \frac{1}{5} \cdot 0.125 = 0.025$$

### Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine hasta que empiece su película es $0.025$ o $2.5\%$.

# Análisis de probabilidad del tiempo de espera en el cine

Tienes razón, mi análisis anterior fue incorrecto. Debo considerar ambas funciones de cine (18:00 y 23:00) para determinar correctamente cuándo Nicolás esperará más de media hora.

## Planteamiento correcto

Analizaré los posibles escenarios de llegada de Nicolás al cine:

### Variables

- $X$: Hora de salida de casa ($X \sim U(16,21)$)
- $Y$: Tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: Hora de llegada al cine

### Casos a considerar

1. Si $X+Y < 17.5$: Llega para la función de 18:00 y espera más de media hora
2. Si $17.5 \leq X+Y < 18$: Llega para la función de 18:00 pero espera menos de media hora
3. Si $18 \leq X+Y < 22.5$: Llega después de la función de 18:00 y debe esperar a la de 23:00 (más de media hora)
4. Si $22.5 \leq X+Y \leq 23$: Llega para la función de 23:00 y espera menos de media hora

Por lo tanto, Nicolás esperará más de media hora en los casos 1 y 3, y la probabilidad buscada es:
$P(X+Y < 17.5) + P(18 \leq X+Y < 22.5)$

## Cálculo de la probabilidad

### Para $P(X+Y < 17.5)$:

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx = \frac{0.125}{5} = 0.025$$

### Para $P(18 \leq X+Y < 22.5)$:

Divido esta región en tres partes:

$$
\begin{align*}
P(18 \leq X+Y < 22.5) &= \int_{16}^{17} \int_{18-x}^{2} \frac{1}{5} \, dy \, dx + \int_{17}^{20.5} \int_{1}^{2} \frac{1}{5} \, dy \, dx + \int_{20.5}^{21} \int_{1}^{22.5-x} \frac{1}{5} \, dy \, dx\\
&= 0.1 + 0.7 + 0.075\\
&= 0.875
\end{align*}
$$

### Probabilidad total

$$P(\text{espera} > 30 \text{ min}) = 0.025 + 0.875 = 0.9$$

## Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine es $0.9$ o $90\%$.

# Problema de la Distribución de Cerezas

## Enunciado

El número de cerezas en una tarta es una variable aleatoria que puede valer 4, 5, 6 o 7; con probabilidades 0.2, 0.4, 0.3, 0.1 respectivamente. Calcular aproximadamente la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5.

## Solución

### Paso 1: Calcular la media y varianza de la variable aleatoria

Sea $X$ la variable aleatoria que representa el número de cerezas en una tarta.

$$P(X=4) = 0.2, \quad P(X=5) = 0.4, \quad P(X=6) = 0.3, \quad P(X=7) = 0.1$$

La **media** (valor esperado) de $X$ es:

$$\mu = E[X] = 4 \cdot 0.2 + 5 \cdot 0.4 + 6 \cdot 0.3 + 7 \cdot 0.1 = 5.3$$

Para calcular la **varianza**, primero hallamos $E[X^2]$:

$$E[X^2] = 4^2 \cdot 0.2 + 5^2 \cdot 0.4 + 6^2 \cdot 0.3 + 7^2 \cdot 0.1 = 28.9$$

Luego, la varianza es:

$$\sigma^2 = E[X^2] - (E[X])^2 = 28.9 - 5.3^2 = 28.9 - 28.09 = 0.81$$

La desviación estándar es $\sigma = \sqrt{0.81} = 0.9$

### Paso 2: Aplicar el Teorema Central del Límite

Sea $\bar{X}_{36}$ el promedio de cerezas en 36 tartas.

Por el Teorema Central del Límite, para $n$ grande (36 es suficientemente grande), la distribución de $\bar{X}_n$ se aproxima a una normal con:

$$\bar{X}_{36} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(5.3, \frac{0.81}{36}\right) = N(5.3, 0.0225)$$

### Paso 3: Calcular la probabilidad requerida

$$P(\bar{X}_{36} < 5.5) = P\left(\frac{\bar{X}_{36} - \mu}{\sigma/\sqrt{n}} < \frac{5.5 - 5.3}{0.9/\sqrt{36}}\right) = P(Z < 1.33)$$

Donde $Z$ es una variable aleatoria normal estándar.

Usando la tabla de la distribución normal o una calculadora:

$$P(Z < 1.33) \approx 0.9082$$

Por lo tanto, la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5 es aproximadamente **0.91** o **91%**.

# Problema de vendedores ambulantes en el subte

## Enunciado

Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos vendedores en el subte.

## Solución usando enfoque combinatorio

Planteamiento
Debemos calcular la probabilidad condicional de que todos los vendedores hayan subido en las estaciones 1-4, dado que exactamente uno subió en la estación 1.

Análisis del problema
Tenemos 8 vendedores que eligen independientemente entre 5 estaciones equiprobables
Ya sabemos que exactamente 1 vendedor subió en la estación 1
Para que todos estén en el subte al salir de la estación 4, los 7 vendedores restantes deben haber subido en las estaciones 2, 3 o 4
Cálculo de la probabilidad
Dado que cada vendedor elige su estación independientemente y con probabilidad uniforme ($p=\frac{1}{5}$ para cada estación), y que ya sabemos que uno subió en la estación 1, los 7 restantes deben elegir entre las estaciones 2, 3, 4 o 5.

Para los 7 vendedores restantes:

Probabilidad de subir en una estación específica (sin condiciones): $\frac{1}{5}$
Probabilidad de subir en las estaciones 2, 3 o 4: $\frac{3}{5}$
Probabilidad de subir en la estación 5: $\frac{1}{5}$
Probabilidad condicional de subir en las estaciones 2, 3 o 4 dado que no subió en la estación 1: $\frac{3/5}{4/5} = \frac{3}{4}$
Por lo tanto, la probabilidad de que todos los 7 vendedores restantes hayan subido en las estaciones 2, 3 o 4 es:

$$P(\text{todos los 7 en estaciones 2-4}) = \left(\frac{3}{4}\right)^7$$

Calculando:

$$\left(\frac{3}{4}\right)^7 = \frac{3^7}{4^7} = \frac{2187}{16384} \approx 0.1335$$

La probabilidad buscada es aproximadamente 13.35%.

Observación sobre Bose-Einstein
Si quisiéramos aplicar un enfoque tipo Bose-Einstein, estaríamos interesados en el número de formas de distribuir los 7 vendedores restantes en 3 estaciones (2, 3 y 4). Sin embargo, como los vendedores eligen independientemente, el enfoque de probabilidad condicional utilizado es más apropiado para este problema.

# Distribución de $W = \frac{Y-X}{2}$ para variables aleatorias uniformes

## Enunciado del problema

Sean las variables aleatorias $X,Y$ uniformes tal que:

$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Hallar y graficar la distribución de $W = \frac{Y-X}{2}$

## Solución

### Paso 1: Análisis del dominio

El dominio $D$ representa una banda diagonal de ancho 2 centrada en la recta $y = x$ y limitada horizontalmente por $x \in (0,4)$.

El área total del dominio es:

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

### Paso 2: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesito transformar la condición:

$$P\left(\frac{Y-X}{2} \leq w\right) = P(Y-X \leq 2w) = P(Y \leq X + 2w)$$

Consideraré diferentes casos según el valor de $w$:

#### Caso 1: $w \leq -\frac{1}{2}$

Si $w \leq -\frac{1}{2}$, entonces $2w \leq -1$.

Como $y > x-1$ (por definición del dominio) y $x+2w \leq x-1$ (ya que $2w \leq -1$), tenemos que $y > x-1 \geq x+2w$.

Por lo tanto, $Y$ siempre es mayor que $X+2w$, lo que significa:
$$F_W(w) = 0 \quad \text{para } w \leq -\frac{1}{2}$$

#### Caso 2: $-\frac{1}{2} < w < \frac{1}{2}$

En este caso, $-1 < 2w < 1$.
La región donde $Y \leq X+2w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+2w) < y < x+1$$

Como $-\frac{1}{2} < w < \frac{1}{2}$, tenemos que $x-1 < x+2w < x+1$, por lo que:
$$0 < x < 4, \quad x-1 < y \leq x+2w$$

El área de esta región es:
$$A = \int_0^4 \int_{x-1}^{x+2w} dy \, dx = \int_0^4 [(x+2w)-(x-1)] \, dx = \int_0^4 (2w+1) \, dx = 4(2w+1)$$

Por lo tanto:
$$F_W(w) = \frac{4(2w+1)}{8} = \frac{2w+1}{2} \quad \text{para } -\frac{1}{2} < w < \frac{1}{2}$$

#### Caso 3: $w \geq \frac{1}{2}$

Si $w \geq \frac{1}{2}$, entonces $2w \geq 1$.

Como $y < x+1$ (por definición del dominio) y $x+2w \geq x+1$ (ya que $2w \geq 1$), tenemos que $y < x+1 \leq x+2w$.

Por lo tanto, $Y$ siempre es menor o igual que $X+2w$, lo que significa:
$$F_W(w) = 1 \quad \text{para } w \geq \frac{1}{2}$$

### Paso 3: Función de distribución completa

La función de distribución acumulada de $W$ es:

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq -\frac{1}{2} \\
\frac{2w+1}{2} & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
1 & \text{si } w \geq \frac{1}{2}
\end{cases}
$$

### Paso 4: Función de densidad de probabilidad

Derivando la función de distribución acumulada, obtenemos la función de densidad:

$$
f_W(w) =
\begin{cases}
0 & \text{si } w < -\frac{1}{2} \\
1 & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
0 & \text{si } w > \frac{1}{2}
\end{cases}
$$

### Conclusión

La variable aleatoria $W = \frac{Y-X}{2}$ sigue una distribución uniforme en el intervalo $[-\frac{1}{2}, \frac{1}{2}]$.

### Gráfico de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq -\frac{1}{2}$: Constante igual a 0
- Para $-\frac{1}{2} < w < \frac{1}{2}$: Recta con pendiente 1, partiendo de $(−\frac{1}{2},0)$ hasta $(\frac{1}{2},1)$
- Para $w \geq \frac{1}{2}$: Constante igual a 1

# Problema de Procesos de Poisson: Clientes conectándose a un servidor

## Enunciado del problema

A y B se conectan a un servidor. Las conexiones que realiza el cliente A ocurren según un proceso de Poisson de 2 por minuto, mientras que para el cliente B ocurren según un proceso de Poisson de 3 por minuto. Los dos procesos de Poisson son independientes. Sabiendo que entre 3:00 y las 3:02 hubo exactamente una conexión al servidor por el cliente A, calcular la probabilidad de que entre 3:00 y 3:05 hayan realizado como máximo 2 conexiones en total.

## Solución

### Datos del problema

- Cliente A: proceso de Poisson con tasa $\lambda_A = 2$ conexiones/minuto
- Cliente B: proceso de Poisson con tasa $\lambda_B = 3$ conexiones/minuto
- Entre 3:00 y 3:02, el cliente A realizó exactamente 1 conexión

### Análisis

Denotemos:

- $N_A(t_1, t_2)$ = número de conexiones del cliente A en el intervalo $(t_1, t_2)$
- $N_B(t_1, t_2)$ = número de conexiones del cliente B en el intervalo $(t_1, t_2)$

Queremos calcular:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1)$$

Sabemos que $N_A(0,5) = N_A(0,2) + N_A(2,5) = 1 + N_A(2,5)$

Por lo tanto:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1) = P(1 + N_A(2,5) + N_B(0,5) \leq 2) = P(N_A(2,5) + N_B(0,5) \leq 1)$$

### Cálculo

Por la propiedad de independencia de incrementos del proceso de Poisson:

- $N_A(2,5)$ sigue una distribución Poisson con parámetro $\lambda_A \cdot 3 = 2 \cdot 3 = 6$
- $N_B(0,5)$ sigue una distribución Poisson con parámetro $\lambda_B \cdot 5 = 3 \cdot 5 = 15$

Por la propiedad de que la suma de variables Poisson independientes también es Poisson:

- $N_A(2,5) + N_B(0,5)$ sigue una distribución Poisson con parámetro $6 + 15 = 21$

Calculamos:
$$P(N_A(2,5) + N_B(0,5) \leq 1) = P(\text{Poisson}(21) \leq 1) = e^{-21} \cdot (1 + 21) = 22 \cdot e^{-21}$$

$$22 \cdot e^{-21} \approx 1.67 \times 10^{-8}$$

La probabilidad pedida es aproximadamente $1.67 \times 10^{-8}$, es decir, extremadamente pequeña (aproximadamente 1 en 60 millones).

# Problema de probabilidad condicional con cajas y bolas

Para resolver este problema, identificaré los eventos y aplicaré el teorema de Bayes.

## Eventos relevantes

- A₁: "Las dos bolas extraídas de C1 son blancas"
- A₂: "Las dos bolas extraídas de C1 son rojas"
- A₃: "Las dos bolas extraídas de C1 son de distinto color"
- B: "La tercera bola extraída es roja"

Necesitamos hallar P(A₂|B).

## Paso 1: Calcular probabilidades del primer evento

En C1 hay 6 bolas blancas y 4 rojas (total 10).

- P(A₁) = C(6,2)/C(10,2) = 15/45 = 1/3
- P(A₂) = C(4,2)/C(10,2) = 6/45 = 2/15
- P(A₃) = 1 - P(A₁) - P(A₂) = 1 - 1/3 - 2/15 = 8/15

## Paso 2: Calcular probabilidades condicionales de B dado cada caso

- Si ocurrió A₁ o A₂, sacamos de C2 (5 blancas, 3 rojas): P(B|A₁) = P(B|A₂) = 3/8
- Si ocurrió A₃, sacamos de C3 (3 blancas, 9 rojas): P(B|A₃) = 9/12 = 3/4

## Paso 3: Calcular P(B) usando la ley de probabilidad total

P(B) = P(B|A₁)P(A₁) + P(B|A₂)P(A₂) + P(B|A₃)P(A₃)
P(B) = (3/8)(1/3) + (3/8)(2/15) + (3/4)(8/15)
P(B) = 1/8 + 1/20 + 2/5 = 5/40 + 2/40 + 16/40 = 23/40

## Paso 4: Aplicar el teorema de Bayes

P(A₂|B) = P(B|A₂)P(A₂)/P(B)
P(A₂|B) = (3/8)(2/15)/(23/40) = (3×2×40)/(8×15×23) = 240/2760 = 2/23

Por lo tanto, la probabilidad de que las dos bolas extraídas de C1 hayan sido rojas, dado que la tercera bola extraída fue roja, es 2/23 ≈ 0.087 (aproximadamente 8.7%).

# Problema de probabilidad: tiempo de espera en el cine

## Enunciado

Nicolás quiere ir a ver su película favorita al cine, que tiene funciones a las 18:00 y a las 23:00. La hora a la que sale de su casa es una variable aleatoria con distribución uniforme entre las 16:00 y las 21:00. Independientemente de la hora de salida, el tiempo de viaje hasta el cine (en horas) es una variable aleatoria con distribución uniforme en el intervalo $(1,2)$. ¿Cuál es la probabilidad de que tenga que esperar más de media hora en el cine hasta que empiece su película?

## Solución

### Definición de variables

- $X$: hora de salida (uniforme en $[16,21]$)
- $Y$: tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: hora de llegada al cine

### Análisis del problema

Para que Nicolás tenga que esperar más de media hora, debe llegar al cine antes de las 17:30, ya que la primera función es a las 18:00.

Necesitamos calcular $P(X+Y < 17.5)$

### Densidades de probabilidad

- $f_X(x) = \frac{1}{21-16} = \frac{1}{5}$ para $16 \leq x \leq 21$
- $f_Y(y) = \frac{1}{2-1} = 1$ para $1 \leq y \leq 2$
- $f_{X,Y}(x,y) = \frac{1}{5} \cdot 1 = \frac{1}{5}$ (por independencia)

### Cálculo de la probabilidad

Identificamos la región donde $X+Y < 17.5$ dentro del dominio $[16,21] \times [1,2]$:

La recta $x+y=17.5$ interseca el dominio formando un triángulo con vértices en $(16,1)$, $(16,1.5)$ y $(16.5,1)$.

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (17.5-x-1) \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (16.5-x) \, dx$$

$$= \frac{1}{5} \cdot \left[16.5x - \frac{x^2}{2}\right]_{16}^{16.5}$$

$$= \frac{1}{5} \cdot \left[(16.5 \cdot 16.5 - \frac{16.5^2}{2}) - (16.5 \cdot 16 - \frac{16^2}{2})\right]$$

$$= \frac{1}{5} \cdot [272.25 - 136.125 - 264 + 128]$$

$$= \frac{1}{5} \cdot 0.125 = 0.025$$

### Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine hasta que empiece su película es $0.025$ o $2.5\%$.

# Análisis de probabilidad del tiempo de espera en el cine

Tienes razón, mi análisis anterior fue incorrecto. Debo considerar ambas funciones de cine (18:00 y 23:00) para determinar correctamente cuándo Nicolás esperará más de media hora.

## Planteamiento correcto

Analizaré los posibles escenarios de llegada de Nicolás al cine:

### Variables

- $X$: Hora de salida de casa ($X \sim U(16,21)$)
- $Y$: Tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: Hora de llegada al cine

### Casos a considerar

1. Si $X+Y < 17.5$: Llega para la función de 18:00 y espera más de media hora
2. Si $17.5 \leq X+Y < 18$: Llega para la función de 18:00 pero espera menos de media hora
3. Si $18 \leq X+Y < 22.5$: Llega después de la función de 18:00 y debe esperar a la de 23:00 (más de media hora)
4. Si $22.5 \leq X+Y \leq 23$: Llega para la función de 23:00 y espera menos de media hora

Por lo tanto, Nicolás esperará más de media hora en los casos 1 y 3, y la probabilidad buscada es:
$P(X+Y < 17.5) + P(18 \leq X+Y < 22.5)$

## Cálculo de la probabilidad

### Para $P(X+Y < 17.5)$:

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx = \frac{0.125}{5} = 0.025$$

### Para $P(18 \leq X+Y < 22.5)$:

Divido esta región en tres partes:

$$
\begin{align*}
P(18 \leq X+Y < 22.5) &= \int_{16}^{17} \int_{18-x}^{2} \frac{1}{5} \, dy \, dx + \int_{17}^{20.5} \int_{1}^{2} \frac{1}{5} \, dy \, dx + \int_{20.5}^{21} \int_{1}^{22.5-x} \frac{1}{5} \, dy \, dx\\
&= 0.1 + 0.7 + 0.075\\
&= 0.875
\end{align*}
$$

### Probabilidad total

$$P(\text{espera} > 30 \text{ min}) = 0.025 + 0.875 = 0.9$$

## Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine es $0.9$ o $90\%$.

# Problema de la Distribución de Cerezas

## Enunciado

El número de cerezas en una tarta es una variable aleatoria que puede valer 4, 5, 6 o 7; con probabilidades 0.2, 0.4, 0.3, 0.1 respectivamente. Calcular aproximadamente la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5.

## Solución

### Paso 1: Calcular la media y varianza de la variable aleatoria

Sea $X$ la variable aleatoria que representa el número de cerezas en una tarta.

$$P(X=4) = 0.2, \quad P(X=5) = 0.4, \quad P(X=6) = 0.3, \quad P(X=7) = 0.1$$

La **media** (valor esperado) de $X$ es:

$$\mu = E[X] = 4 \cdot 0.2 + 5 \cdot 0.4 + 6 \cdot 0.3 + 7 \cdot 0.1 = 5.3$$

Para calcular la **varianza**, primero hallamos $E[X^2]$:

$$E[X^2] = 4^2 \cdot 0.2 + 5^2 \cdot 0.4 + 6^2 \cdot 0.3 + 7^2 \cdot 0.1 = 28.9$$

Luego, la varianza es:

$$\sigma^2 = E[X^2] - (E[X])^2 = 28.9 - 5.3^2 = 28.9 - 28.09 = 0.81$$

La desviación estándar es $\sigma = \sqrt{0.81} = 0.9$

### Paso 2: Aplicar el Teorema Central del Límite

Sea $\bar{X}_{36}$ el promedio de cerezas en 36 tartas.

Por el Teorema Central del Límite, para $n$ grande (36 es suficientemente grande), la distribución de $\bar{X}_n$ se aproxima a una normal con:

$$\bar{X}_{36} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(5.3, \frac{0.81}{36}\right) = N(5.3, 0.0225)$$

### Paso 3: Calcular la probabilidad requerida

$$P(\bar{X}_{36} < 5.5) = P\left(\frac{\bar{X}_{36} - \mu}{\sigma/\sqrt{n}} < \frac{5.5 - 5.3}{0.9/\sqrt{36}}\right) = P(Z < 1.33)$$

Donde $Z$ es una variable aleatoria normal estándar.

Usando la tabla de la distribución normal o una calculadora:

$$P(Z < 1.33) \approx 0.9082$$

Por lo tanto, la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5 es aproximadamente **0.91** o **91%**.

# Problema de vendedores ambulantes en el subte

## Enunciado

Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos vendedores en el subte.

## Solución usando enfoque combinatorio

Planteamiento
Debemos calcular la probabilidad condicional de que todos los vendedores hayan subido en las estaciones 1-4, dado que exactamente uno subió en la estación 1.

Análisis del problema
Tenemos 8 vendedores que eligen independientemente entre 5 estaciones equiprobables
Ya sabemos que exactamente 1 vendedor subió en la estación 1
Para que todos estén en el subte al salir de la estación 4, los 7 vendedores restantes deben haber subido en las estaciones 2, 3 o 4
Cálculo de la probabilidad
Dado que cada vendedor elige su estación independientemente y con probabilidad uniforme ($p=\frac{1}{5}$ para cada estación), y que ya sabemos que uno subió en la estación 1, los 7 restantes deben elegir entre las estaciones 2, 3, 4 o 5.

Para los 7 vendedores restantes:

Probabilidad de subir en una estación específica (sin condiciones): $\frac{1}{5}$
Probabilidad de subir en las estaciones 2, 3 o 4: $\frac{3}{5}$
Probabilidad de subir en la estación 5: $\frac{1}{5}$
Probabilidad condicional de subir en las estaciones 2, 3 o 4 dado que no subió en la estación 1: $\frac{3/5}{4/5} = \frac{3}{4}$
Por lo tanto, la probabilidad de que todos los 7 vendedores restantes hayan subido en las estaciones 2, 3 o 4 es:

$$P(\text{todos los 7 en estaciones 2-4}) = \left(\frac{3}{4}\right)^7$$

Calculando:

$$\left(\frac{3}{4}\right)^7 = \frac{3^7}{4^7} = \frac{2187}{16384} \approx 0.1335$$

La probabilidad buscada es aproximadamente 13.35%.

Observación sobre Bose-Einstein
Si quisiéramos aplicar un enfoque tipo Bose-Einstein, estaríamos interesados en el número de formas de distribuir los 7 vendedores restantes en 3 estaciones (2, 3 y 4). Sin embargo, como los vendedores eligen independientemente, el enfoque de probabilidad condicional utilizado es más apropiado para este problema.

# Distribución de $W = \frac{Y-X}{2}$ para variables aleatorias uniformes

## Enunciado del problema

Sean las variables aleatorias $X,Y$ uniformes tal que:

$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Hallar y graficar la distribución de $W = \frac{Y-X}{2}$

## Solución

### Paso 1: Análisis del dominio

El dominio $D$ representa una banda diagonal de ancho 2 centrada en la recta $y = x$ y limitada horizontalmente por $x \in (0,4)$.

El área total del dominio es:

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

### Paso 2: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesito transformar la condición:

$$P\left(\frac{Y-X}{2} \leq w\right) = P(Y-X \leq 2w) = P(Y \leq X + 2w)$$

Consideraré diferentes casos según el valor de $w$:

#### Caso 1: $w \leq -\frac{1}{2}$

Si $w \leq -\frac{1}{2}$, entonces $2w \leq -1$.

Como $y > x-1$ (por definición del dominio) y $x+2w \leq x-1$ (ya que $2w \leq -1$), tenemos que $y > x-1 \geq x+2w$.

Por lo tanto, $Y$ siempre es mayor que $X+2w$, lo que significa:
$$F_W(w) = 0 \quad \text{para } w \leq -\frac{1}{2}$$

#### Caso 2: $-\frac{1}{2} < w < \frac{1}{2}$

En este caso, $-1 < 2w < 1$.
La región donde $Y \leq X+2w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+2w) < y < x+1$$

Como $-\frac{1}{2} < w < \frac{1}{2}$, tenemos que $x-1 < x+2w < x+1$, por lo que:
$$0 < x < 4, \quad x-1 < y \leq x+2w$$

El área de esta región es:
$$A = \int_0^4 \int_{x-1}^{x+2w} dy \, dx = \int_0^4 [(x+2w)-(x-1)] \, dx = \int_0^4 (2w+1) \, dx = 4(2w+1)$$

Por lo tanto:
$$F_W(w) = \frac{4(2w+1)}{8} = \frac{2w+1}{2} \quad \text{para } -\frac{1}{2} < w < \frac{1}{2}$$

#### Caso 3: $w \geq \frac{1}{2}$

Si $w \geq \frac{1}{2}$, entonces $2w \geq 1$.

Como $y < x+1$ (por definición del dominio) y $x+2w \geq x+1$ (ya que $2w \geq 1$), tenemos que $y < x+1 \leq x+2w$.

Por lo tanto, $Y$ siempre es menor o igual que $X+2w$, lo que significa:
$$F_W(w) = 1 \quad \text{para } w \geq \frac{1}{2}$$

### Paso 3: Función de distribución completa

La función de distribución acumulada de $W$ es:

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq -\frac{1}{2} \\
\frac{2w+1}{2} & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
1 & \text{si } w \geq \frac{1}{2}
\end{cases}
$$

### Paso 4: Función de densidad de probabilidad

Derivando la función de distribución acumulada, obtenemos la función de densidad:

$$
f_W(w) =
\begin{cases}
0 & \text{si } w < -\frac{1}{2} \\
1 & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
0 & \text{si } w > \frac{1}{2}
\end{cases}
$$

### Conclusión

La variable aleatoria $W = \frac{Y-X}{2}$ sigue una distribución uniforme en el intervalo $[-\frac{1}{2}, \frac{1}{2}]$.

### Gráfico de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq -\frac{1}{2}$: Constante igual a 0
- Para $-\frac{1}{2} < w < \frac{1}{2}$: Recta con pendiente 1, partiendo de $(−\frac{1}{2},0)$ hasta $(\frac{1}{2},1)$
- Para $w \geq \frac{1}{2}$: Constante igual a 1

# Problema de Procesos de Poisson: Clientes conectándose a un servidor

## Enunciado del problema

A y B se conectan a un servidor. Las conexiones que realiza el cliente A ocurren según un proceso de Poisson de 2 por minuto, mientras que para el cliente B ocurren según un proceso de Poisson de 3 por minuto. Los dos procesos de Poisson son independientes. Sabiendo que entre 3:00 y las 3:02 hubo exactamente una conexión al servidor por el cliente A, calcular la probabilidad de que entre 3:00 y 3:05 hayan realizado como máximo 2 conexiones en total.

## Solución

### Datos del problema

- Cliente A: proceso de Poisson con tasa $\lambda_A = 2$ conexiones/minuto
- Cliente B: proceso de Poisson con tasa $\lambda_B = 3$ conexiones/minuto
- Entre 3:00 y 3:02, el cliente A realizó exactamente 1 conexión

### Análisis

Denotemos:

- $N_A(t_1, t_2)$ = número de conexiones del cliente A en el intervalo $(t_1, t_2)$
- $N_B(t_1, t_2)$ = número de conexiones del cliente B en el intervalo $(t_1, t_2)$

Queremos calcular:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1)$$

Sabemos que $N_A(0,5) = N_A(0,2) + N_A(2,5) = 1 + N_A(2,5)$

Por lo tanto:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1) = P(1 + N_A(2,5) + N_B(0,5) \leq 2) = P(N_A(2,5) + N_B(0,5) \leq 1)$$

### Cálculo

Por la propiedad de independencia de incrementos del proceso de Poisson:

- $N_A(2,5)$ sigue una distribución Poisson con parámetro $\lambda_A \cdot 3 = 2 \cdot 3 = 6$
- $N_B(0,5)$ sigue una distribución Poisson con parámetro $\lambda_B \cdot 5 = 3 \cdot 5 = 15$

Por la propiedad de que la suma de variables Poisson independientes también es Poisson:

- $N_A(2,5) + N_B(0,5)$ sigue una distribución Poisson con parámetro $6 + 15 = 21$

Calculamos:
$$P(N_A(2,5) + N_B(0,5) \leq 1) = P(\text{Poisson}(21) \leq 1) = e^{-21} \cdot (1 + 21) = 22 \cdot e^{-21}$$

$$22 \cdot e^{-21} \approx 1.67 \times 10^{-8}$$

La probabilidad pedida es aproximadamente $1.67 \times 10^{-8}$, es decir, extremadamente pequeña (aproximadamente 1 en 60 millones).

# Problema de probabilidad condicional con cajas y bolas

Para resolver este problema, identificaré los eventos y aplicaré el teorema de Bayes.

## Eventos relevantes

- A₁: "Las dos bolas extraídas de C1 son blancas"
- A₂: "Las dos bolas extraídas de C1 son rojas"
- A₃: "Las dos bolas extraídas de C1 son de distinto color"
- B: "La tercera bola extraída es roja"

Necesitamos hallar P(A₂|B).

## Paso 1: Calcular probabilidades del primer evento

En C1 hay 6 bolas blancas y 4 rojas (total 10).

- P(A₁) = C(6,2)/C(10,2) = 15/45 = 1/3
- P(A₂) = C(4,2)/C(10,2) = 6/45 = 2/15
- P(A₃) = 1 - P(A₁) - P(A₂) = 1 - 1/3 - 2/15 = 8/15

## Paso 2: Calcular probabilidades condicionales de B dado cada caso

- Si ocurrió A₁ o A₂, sacamos de C2 (5 blancas, 3 rojas): P(B|A₁) = P(B|A₂) = 3/8
- Si ocurrió A₃, sacamos de C3 (3 blancas, 9 rojas): P(B|A₃) = 9/12 = 3/4

## Paso 3: Calcular P(B) usando la ley de probabilidad total

P(B) = P(B|A₁)P(A₁) + P(B|A₂)P(A₂) + P(B|A₃)P(A₃)
P(B) = (3/8)(1/3) + (3/8)(2/15) + (3/4)(8/15)
P(B) = 1/8 + 1/20 + 2/5 = 5/40 + 2/40 + 16/40 = 23/40

## Paso 4: Aplicar el teorema de Bayes

P(A₂|B) = P(B|A₂)P(A₂)/P(B)
P(A₂|B) = (3/8)(2/15)/(23/40) = (3×2×40)/(8×15×23) = 240/2760 = 2/23

Por lo tanto, la probabilidad de que las dos bolas extraídas de C1 hayan sido rojas, dado que la tercera bola extraída fue roja, es 2/23 ≈ 0.087 (aproximadamente 8.7%).

# Problema de probabilidad: tiempo de espera en el cine

## Enunciado

Nicolás quiere ir a ver su película favorita al cine, que tiene funciones a las 18:00 y a las 23:00. La hora a la que sale de su casa es una variable aleatoria con distribución uniforme entre las 16:00 y las 21:00. Independientemente de la hora de salida, el tiempo de viaje hasta el cine (en horas) es una variable aleatoria con distribución uniforme en el intervalo $(1,2)$. ¿Cuál es la probabilidad de que tenga que esperar más de media hora en el cine hasta que empiece su película?

## Solución

### Definición de variables

- $X$: hora de salida (uniforme en $[16,21]$)
- $Y$: tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: hora de llegada al cine

### Análisis del problema

Para que Nicolás tenga que esperar más de media hora, debe llegar al cine antes de las 17:30, ya que la primera función es a las 18:00.

Necesitamos calcular $P(X+Y < 17.5)$

### Densidades de probabilidad

- $f_X(x) = \frac{1}{21-16} = \frac{1}{5}$ para $16 \leq x \leq 21$
- $f_Y(y) = \frac{1}{2-1} = 1$ para $1 \leq y \leq 2$
- $f_{X,Y}(x,y) = \frac{1}{5} \cdot 1 = \frac{1}{5}$ (por independencia)

### Cálculo de la probabilidad

Identificamos la región donde $X+Y < 17.5$ dentro del dominio $[16,21] \times [1,2]$:

La recta $x+y=17.5$ interseca el dominio formando un triángulo con vértices en $(16,1)$, $(16,1.5)$ y $(16.5,1)$.

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (17.5-x-1) \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (16.5-x) \, dx$$

$$= \frac{1}{5} \cdot \left[16.5x - \frac{x^2}{2}\right]_{16}^{16.5}$$

$$= \frac{1}{5} \cdot \left[(16.5 \cdot 16.5 - \frac{16.5^2}{2}) - (16.5 \cdot 16 - \frac{16^2}{2})\right]$$

$$= \frac{1}{5} \cdot [272.25 - 136.125 - 264 + 128]$$

$$= \frac{1}{5} \cdot 0.125 = 0.025$$

### Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine hasta que empiece su película es $0.025$ o $2.5\%$.

# Análisis de probabilidad del tiempo de espera en el cine

Tienes razón, mi análisis anterior fue incorrecto. Debo considerar ambas funciones de cine (18:00 y 23:00) para determinar correctamente cuándo Nicolás esperará más de media hora.

## Planteamiento correcto

Analizaré los posibles escenarios de llegada de Nicolás al cine:

### Variables

- $X$: Hora de salida de casa ($X \sim U(16,21)$)
- $Y$: Tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: Hora de llegada al cine

### Casos a considerar

1. Si $X+Y < 17.5$: Llega para la función de 18:00 y espera más de media hora
2. Si $17.5 \leq X+Y < 18$: Llega para la función de 18:00 pero espera menos de media hora
3. Si $18 \leq X+Y < 22.5$: Llega después de la función de 18:00 y debe esperar a la de 23:00 (más de media hora)
4. Si $22.5 \leq X+Y \leq 23$: Llega para la función de 23:00 y espera menos de media hora

Por lo tanto, Nicolás esperará más de media hora en los casos 1 y 3, y la probabilidad buscada es:
$P(X+Y < 17.5) + P(18 \leq X+Y < 22.5)$

## Cálculo de la probabilidad

### Para $P(X+Y < 17.5)$:

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx = \frac{0.125}{5} = 0.025$$

### Para $P(18 \leq X+Y < 22.5)$:

Divido esta región en tres partes:

$$
\begin{align*}
P(18 \leq X+Y < 22.5) &= \int_{16}^{17} \int_{18-x}^{2} \frac{1}{5} \, dy \, dx + \int_{17}^{20.5} \int_{1}^{2} \frac{1}{5} \, dy \, dx + \int_{20.5}^{21} \int_{1}^{22.5-x} \frac{1}{5} \, dy \, dx\\
&= 0.1 + 0.7 + 0.075\\
&= 0.875
\end{align*}
$$

### Probabilidad total

$$P(\text{espera} > 30 \text{ min}) = 0.025 + 0.875 = 0.9$$

## Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine es $0.9$ o $90\%$.

# Problema de la Distribución de Cerezas

## Enunciado

El número de cerezas en una tarta es una variable aleatoria que puede valer 4, 5, 6 o 7; con probabilidades 0.2, 0.4, 0.3, 0.1 respectivamente. Calcular aproximadamente la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5.

## Solución

### Paso 1: Calcular la media y varianza de la variable aleatoria

Sea $X$ la variable aleatoria que representa el número de cerezas en una tarta.

$$P(X=4) = 0.2, \quad P(X=5) = 0.4, \quad P(X=6) = 0.3, \quad P(X=7) = 0.1$$

La **media** (valor esperado) de $X$ es:

$$\mu = E[X] = 4 \cdot 0.2 + 5 \cdot 0.4 + 6 \cdot 0.3 + 7 \cdot 0.1 = 5.3$$

Para calcular la **varianza**, primero hallamos $E[X^2]$:

$$E[X^2] = 4^2 \cdot 0.2 + 5^2 \cdot 0.4 + 6^2 \cdot 0.3 + 7^2 \cdot 0.1 = 28.9$$

Luego, la varianza es:

$$\sigma^2 = E[X^2] - (E[X])^2 = 28.9 - 5.3^2 = 28.9 - 28.09 = 0.81$$

La desviación estándar es $\sigma = \sqrt{0.81} = 0.9$

### Paso 2: Aplicar el Teorema Central del Límite

Sea $\bar{X}_{36}$ el promedio de cerezas en 36 tartas.

Por el Teorema Central del Límite, para $n$ grande (36 es suficientemente grande), la distribución de $\bar{X}_n$ se aproxima a una normal con:

$$\bar{X}_{36} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(5.3, \frac{0.81}{36}\right) = N(5.3, 0.0225)$$

### Paso 3: Calcular la probabilidad requerida

$$P(\bar{X}_{36} < 5.5) = P\left(\frac{\bar{X}_{36} - \mu}{\sigma/\sqrt{n}} < \frac{5.5 - 5.3}{0.9/\sqrt{36}}\right) = P(Z < 1.33)$$

Donde $Z$ es una variable aleatoria normal estándar.

Usando la tabla de la distribución normal o una calculadora:

$$P(Z < 1.33) \approx 0.9082$$

Por lo tanto, la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5 es aproximadamente **0.91** o **91%**.

# Problema de vendedores ambulantes en el subte

## Enunciado

Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos vendedores en el subte.

## Solución usando enfoque combinatorio

Planteamiento
Debemos calcular la probabilidad condicional de que todos los vendedores hayan subido en las estaciones 1-4, dado que exactamente uno subió en la estación 1.

Análisis del problema
Tenemos 8 vendedores que eligen independientemente entre 5 estaciones equiprobables
Ya sabemos que exactamente 1 vendedor subió en la estación 1
Para que todos estén en el subte al salir de la estación 4, los 7 vendedores restantes deben haber subido en las estaciones 2, 3 o 4
Cálculo de la probabilidad
Dado que cada vendedor elige su estación independientemente y con probabilidad uniforme ($p=\frac{1}{5}$ para cada estación), y que ya sabemos que uno subió en la estación 1, los 7 restantes deben elegir entre las estaciones 2, 3, 4 o 5.

Para los 7 vendedores restantes:

Probabilidad de subir en una estación específica (sin condiciones): $\frac{1}{5}$
Probabilidad de subir en las estaciones 2, 3 o 4: $\frac{3}{5}$
Probabilidad de subir en la estación 5: $\frac{1}{5}$
Probabilidad condicional de subir en las estaciones 2, 3 o 4 dado que no subió en la estación 1: $\frac{3/5}{4/5} = \frac{3}{4}$
Por lo tanto, la probabilidad de que todos los 7 vendedores restantes hayan subido en las estaciones 2, 3 o 4 es:

$$P(\text{todos los 7 en estaciones 2-4}) = \left(\frac{3}{4}\right)^7$$

Calculando:

$$\left(\frac{3}{4}\right)^7 = \frac{3^7}{4^7} = \frac{2187}{16384} \approx 0.1335$$

La probabilidad buscada es aproximadamente 13.35%.

Observación sobre Bose-Einstein
Si quisiéramos aplicar un enfoque tipo Bose-Einstein, estaríamos interesados en el número de formas de distribuir los 7 vendedores restantes en 3 estaciones (2, 3 y 4). Sin embargo, como los vendedores eligen independientemente, el enfoque de probabilidad condicional utilizado es más apropiado para este problema.

# Distribución de $W = \frac{Y-X}{2}$ para variables aleatorias uniformes

## Enunciado del problema

Sean las variables aleatorias $X,Y$ uniformes tal que:

$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Hallar y graficar la distribución de $W = \frac{Y-X}{2}$

## Solución

### Paso 1: Análisis del dominio

El dominio $D$ representa una banda diagonal de ancho 2 centrada en la recta $y = x$ y limitada horizontalmente por $x \in (0,4)$.

El área total del dominio es:

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

### Paso 2: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesito transformar la condición:

$$P\left(\frac{Y-X}{2} \leq w\right) = P(Y-X \leq 2w) = P(Y \leq X + 2w)$$

Consideraré diferentes casos según el valor de $w$:

#### Caso 1: $w \leq -\frac{1}{2}$

Si $w \leq -\frac{1}{2}$, entonces $2w \leq -1$.

Como $y > x-1$ (por definición del dominio) y $x+2w \leq x-1$ (ya que $2w \leq -1$), tenemos que $y > x-1 \geq x+2w$.

Por lo tanto, $Y$ siempre es mayor que $X+2w$, lo que significa:
$$F_W(w) = 0 \quad \text{para } w \leq -\frac{1}{2}$$

#### Caso 2: $-\frac{1}{2} < w < \frac{1}{2}$

En este caso, $-1 < 2w < 1$.
La región donde $Y \leq X+2w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+2w) < y < x+1$$

Como $-\frac{1}{2} < w < \frac{1}{2}$, tenemos que $x-1 < x+2w < x+1$, por lo que:
$$0 < x < 4, \quad x-1 < y \leq x+2w$$

El área de esta región es:
$$A = \int_0^4 \int_{x-1}^{x+2w} dy \, dx = \int_0^4 [(x+2w)-(x-1)] \, dx = \int_0^4 (2w+1) \, dx = 4(2w+1)$$

Por lo tanto:
$$F_W(w) = \frac{4(2w+1)}{8} = \frac{2w+1}{2} \quad \text{para } -\frac{1}{2} < w < \frac{1}{2}$$

#### Caso 3: $w \geq \frac{1}{2}$

Si $w \geq \frac{1}{2}$, entonces $2w \geq 1$.

Como $y < x+1$ (por definición del dominio) y $x+2w \geq x+1$ (ya que $2w \geq 1$), tenemos que $y < x+1 \leq x+2w$.

Por lo tanto, $Y$ siempre es menor o igual que $X+2w$, lo que significa:
$$F_W(w) = 1 \quad \text{para } w \geq \frac{1}{2}$$

### Paso 3: Función de distribución completa

La función de distribución acumulada de $W$ es:

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq -\frac{1}{2} \\
\frac{2w+1}{2} & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
1 & \text{si } w \geq \frac{1}{2}
\end{cases}
$$

### Paso 4: Función de densidad de probabilidad

Derivando la función de distribución acumulada, obtenemos la función de densidad:

$$
f_W(w) =
\begin{cases}
0 & \text{si } w < -\frac{1}{2} \\
1 & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
0 & \text{si } w > \frac{1}{2}
\end{cases}
$$

### Conclusión

La variable aleatoria $W = \frac{Y-X}{2}$ sigue una distribución uniforme en el intervalo $[-\frac{1}{2}, \frac{1}{2}]$.

### Gráfico de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq -\frac{1}{2}$: Constante igual a 0
- Para $-\frac{1}{2} < w < \frac{1}{2}$: Recta con pendiente 1, partiendo de $(−\frac{1}{2},0)$ hasta $(\frac{1}{2},1)$
- Para $w \geq \frac{1}{2}$: Constante igual a 1

# Problema de Procesos de Poisson: Clientes conectándose a un servidor

## Enunciado del problema

A y B se conectan a un servidor. Las conexiones que realiza el cliente A ocurren según un proceso de Poisson de 2 por minuto, mientras que para el cliente B ocurren según un proceso de Poisson de 3 por minuto. Los dos procesos de Poisson son independientes. Sabiendo que entre 3:00 y las 3:02 hubo exactamente una conexión al servidor por el cliente A, calcular la probabilidad de que entre 3:00 y 3:05 hayan realizado como máximo 2 conexiones en total.

## Solución

### Datos del problema

- Cliente A: proceso de Poisson con tasa $\lambda_A = 2$ conexiones/minuto
- Cliente B: proceso de Poisson con tasa $\lambda_B = 3$ conexiones/minuto
- Entre 3:00 y 3:02, el cliente A realizó exactamente 1 conexión

### Análisis

Denotemos:

- $N_A(t_1, t_2)$ = número de conexiones del cliente A en el intervalo $(t_1, t_2)$
- $N_B(t_1, t_2)$ = número de conexiones del cliente B en el intervalo $(t_1, t_2)$

Queremos calcular:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1)$$

Sabemos que $N_A(0,5) = N_A(0,2) + N_A(2,5) = 1 + N_A(2,5)$

Por lo tanto:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1) = P(1 + N_A(2,5) + N_B(0,5) \leq 2) = P(N_A(2,5) + N_B(0,5) \leq 1)$$

### Cálculo

Por la propiedad de independencia de incrementos del proceso de Poisson:

- $N_A(2,5)$ sigue una distribución Poisson con parámetro $\lambda_A \cdot 3 = 2 \cdot 3 = 6$
- $N_B(0,5)$ sigue una distribución Poisson con parámetro $\lambda_B \cdot 5 = 3 \cdot 5 = 15$

Por la propiedad de que la suma de variables Poisson independientes también es Poisson:

- $N_A(2,5) + N_B(0,5)$ sigue una distribución Poisson con parámetro $6 + 15 = 21$

Calculamos:
$$P(N_A(2,5) + N_B(0,5) \leq 1) = P(\text{Poisson}(21) \leq 1) = e^{-21} \cdot (1 + 21) = 22 \cdot e^{-21}$$

$$22 \cdot e^{-21} \approx 1.67 \times 10^{-8}$$

La probabilidad pedida es aproximadamente $1.67 \times 10^{-8}$, es decir, extremadamente pequeña (aproximadamente 1 en 60 millones).

# Problema de probabilidad condicional con cajas y bolas

Para resolver este problema, identificaré los eventos y aplicaré el teorema de Bayes.

## Eventos relevantes

- A₁: "Las dos bolas extraídas de C1 son blancas"
- A₂: "Las dos bolas extraídas de C1 son rojas"
- A₃: "Las dos bolas extraídas de C1 son de distinto color"
- B: "La tercera bola extraída es roja"

Necesitamos hallar P(A₂|B).

## Paso 1: Calcular probabilidades del primer evento

En C1 hay 6 bolas blancas y 4 rojas (total 10).

- P(A₁) = C(6,2)/C(10,2) = 15/45 = 1/3
- P(A₂) = C(4,2)/C(10,2) = 6/45 = 2/15
- P(A₃) = 1 - P(A₁) - P(A₂) = 1 - 1/3 - 2/15 = 8/15

## Paso 2: Calcular probabilidades condicionales de B dado cada caso

- Si ocurrió A₁ o A₂, sacamos de C2 (5 blancas, 3 rojas): P(B|A₁) = P(B|A₂) = 3/8
- Si ocurrió A₃, sacamos de C3 (3 blancas, 9 rojas): P(B|A₃) = 9/12 = 3/4

## Paso 3: Calcular P(B) usando la ley de probabilidad total

P(B) = P(B|A₁)P(A₁) + P(B|A₂)P(A₂) + P(B|A₃)P(A₃)
P(B) = (3/8)(1/3) + (3/8)(2/15) + (3/4)(8/15)
P(B) = 1/8 + 1/20 + 2/5 = 5/40 + 2/40 + 16/40 = 23/40

## Paso 4: Aplicar el teorema de Bayes

P(A₂|B) = P(B|A₂)P(A₂)/P(B)
P(A₂|B) = (3/8)(2/15)/(23/40) = (3×2×40)/(8×15×23) = 240/2760 = 2/23

Por lo tanto, la probabilidad de que las dos bolas extraídas de C1 hayan sido rojas, dado que la tercera bola extraída fue roja, es 2/23 ≈ 0.087 (aproximadamente 8.7%).

# Problema de probabilidad: tiempo de espera en el cine

## Enunciado

Nicolás quiere ir a ver su película favorita al cine, que tiene funciones a las 18:00 y a las 23:00. La hora a la que sale de su casa es una variable aleatoria con distribución uniforme entre las 16:00 y las 21:00. Independientemente de la hora de salida, el tiempo de viaje hasta el cine (en horas) es una variable aleatoria con distribución uniforme en el intervalo $(1,2)$. ¿Cuál es la probabilidad de que tenga que esperar más de media hora en el cine hasta que empiece su película?

## Solución

### Definición de variables

- $X$: hora de salida (uniforme en $[16,21]$)
- $Y$: tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: hora de llegada al cine

### Análisis del problema

Para que Nicolás tenga que esperar más de media hora, debe llegar al cine antes de las 17:30, ya que la primera función es a las 18:00.

Necesitamos calcular $P(X+Y < 17.5)$

### Densidades de probabilidad

- $f_X(x) = \frac{1}{21-16} = \frac{1}{5}$ para $16 \leq x \leq 21$
- $f_Y(y) = \frac{1}{2-1} = 1$ para $1 \leq y \leq 2$
- $f_{X,Y}(x,y) = \frac{1}{5} \cdot 1 = \frac{1}{5}$ (por independencia)

### Cálculo de la probabilidad

Identificamos la región donde $X+Y < 17.5$ dentro del dominio $[16,21] \times [1,2]$:

La recta $x+y=17.5$ interseca el dominio formando un triángulo con vértices en $(16,1)$, $(16,1.5)$ y $(16.5,1)$.

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (17.5-x-1) \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (16.5-x) \, dx$$

$$= \frac{1}{5} \cdot \left[16.5x - \frac{x^2}{2}\right]_{16}^{16.5}$$

$$= \frac{1}{5} \cdot \left[(16.5 \cdot 16.5 - \frac{16.5^2}{2}) - (16.5 \cdot 16 - \frac{16^2}{2})\right]$$

$$= \frac{1}{5} \cdot [272.25 - 136.125 - 264 + 128]$$

$$= \frac{1}{5} \cdot 0.125 = 0.025$$

### Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine hasta que empiece su película es $0.025$ o $2.5\%$.

# Análisis de probabilidad del tiempo de espera en el cine

Tienes razón, mi análisis anterior fue incorrecto. Debo considerar ambas funciones de cine (18:00 y 23:00) para determinar correctamente cuándo Nicolás esperará más de media hora.

## Planteamiento correcto

Analizaré los posibles escenarios de llegada de Nicolás al cine:

### Variables

- $X$: Hora de salida de casa ($X \sim U(16,21)$)
- $Y$: Tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: Hora de llegada al cine

### Casos a considerar

1. Si $X+Y < 17.5$: Llega para la función de 18:00 y espera más de media hora
2. Si $17.5 \leq X+Y < 18$: Llega para la función de 18:00 pero espera menos de media hora
3. Si $18 \leq X+Y < 22.5$: Llega después de la función de 18:00 y debe esperar a la de 23:00 (más de media hora)
4. Si $22.5 \leq X+Y \leq 23$: Llega para la función de 23:00 y espera menos de media hora

Por lo tanto, Nicolás esperará más de media hora en los casos 1 y 3, y la probabilidad buscada es:
$P(X+Y < 17.5) + P(18 \leq X+Y < 22.5)$

## Cálculo de la probabilidad

### Para $P(X+Y < 17.5)$:

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx = \frac{0.125}{5} = 0.025$$

### Para $P(18 \leq X+Y < 22.5)$:

Divido esta región en tres partes:

$$
\begin{align*}
P(18 \leq X+Y < 22.5) &= \int_{16}^{17} \int_{18-x}^{2} \frac{1}{5} \, dy \, dx + \int_{17}^{20.5} \int_{1}^{2} \frac{1}{5} \, dy \, dx + \int_{20.5}^{21} \int_{1}^{22.5-x} \frac{1}{5} \, dy \, dx\\
&= 0.1 + 0.7 + 0.075\\
&= 0.875
\end{align*}
$$

### Probabilidad total

$$P(\text{espera} > 30 \text{ min}) = 0.025 + 0.875 = 0.9$$

## Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine es $0.9$ o $90\%$.

# Problema de la Distribución de Cerezas

## Enunciado

El número de cerezas en una tarta es una variable aleatoria que puede valer 4, 5, 6 o 7; con probabilidades 0.2, 0.4, 0.3, 0.1 respectivamente. Calcular aproximadamente la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5.

## Solución

### Paso 1: Calcular la media y varianza de la variable aleatoria

Sea $X$ la variable aleatoria que representa el número de cerezas en una tarta.

$$P(X=4) = 0.2, \quad P(X=5) = 0.4, \quad P(X=6) = 0.3, \quad P(X=7) = 0.1$$

La **media** (valor esperado) de $X$ es:

$$\mu = E[X] = 4 \cdot 0.2 + 5 \cdot 0.4 + 6 \cdot 0.3 + 7 \cdot 0.1 = 5.3$$

Para calcular la **varianza**, primero hallamos $E[X^2]$:

$$E[X^2] = 4^2 \cdot 0.2 + 5^2 \cdot 0.4 + 6^2 \cdot 0.3 + 7^2 \cdot 0.1 = 28.9$$

Luego, la varianza es:

$$\sigma^2 = E[X^2] - (E[X])^2 = 28.9 - 5.3^2 = 28.9 - 28.09 = 0.81$$

La desviación estándar es $\sigma = \sqrt{0.81} = 0.9$

### Paso 2: Aplicar el Teorema Central del Límite

Sea $\bar{X}_{36}$ el promedio de cerezas en 36 tartas.

Por el Teorema Central del Límite, para $n$ grande (36 es suficientemente grande), la distribución de $\bar{X}_n$ se aproxima a una normal con:

$$\bar{X}_{36} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(5.3, \frac{0.81}{36}\right) = N(5.3, 0.0225)$$

### Paso 3: Calcular la probabilidad requerida

$$P(\bar{X}_{36} < 5.5) = P\left(\frac{\bar{X}_{36} - \mu}{\sigma/\sqrt{n}} < \frac{5.5 - 5.3}{0.9/\sqrt{36}}\right) = P(Z < 1.33)$$

Donde $Z$ es una variable aleatoria normal estándar.

Usando la tabla de la distribución normal o una calculadora:

$$P(Z < 1.33) \approx 0.9082$$

Por lo tanto, la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5 es aproximadamente **0.91** o **91%**.

# Problema de vendedores ambulantes en el subte

## Enunciado

Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos vendedores en el subte.

## Solución usando enfoque combinatorio

Planteamiento
Debemos calcular la probabilidad condicional de que todos los vendedores hayan subido en las estaciones 1-4, dado que exactamente uno subió en la estación 1.

Análisis del problema
Tenemos 8 vendedores que eligen independientemente entre 5 estaciones equiprobables
Ya sabemos que exactamente 1 vendedor subió en la estación 1
Para que todos estén en el subte al salir de la estación 4, los 7 vendedores restantes deben haber subido en las estaciones 2, 3 o 4
Cálculo de la probabilidad
Dado que cada vendedor elige su estación independientemente y con probabilidad uniforme ($p=\frac{1}{5}$ para cada estación), y que ya sabemos que uno subió en la estación 1, los 7 restantes deben elegir entre las estaciones 2, 3, 4 o 5.

Para los 7 vendedores restantes:

Probabilidad de subir en una estación específica (sin condiciones): $\frac{1}{5}$
Probabilidad de subir en las estaciones 2, 3 o 4: $\frac{3}{5}$
Probabilidad de subir en la estación 5: $\frac{1}{5}$
Probabilidad condicional de subir en las estaciones 2, 3 o 4 dado que no subió en la estación 1: $\frac{3/5}{4/5} = \frac{3}{4}$
Por lo tanto, la probabilidad de que todos los 7 vendedores restantes hayan subido en las estaciones 2, 3 o 4 es:

$$P(\text{todos los 7 en estaciones 2-4}) = \left(\frac{3}{4}\right)^7$$

Calculando:

$$\left(\frac{3}{4}\right)^7 = \frac{3^7}{4^7} = \frac{2187}{16384} \approx 0.1335$$

La probabilidad buscada es aproximadamente 13.35%.

Observación sobre Bose-Einstein
Si quisiéramos aplicar un enfoque tipo Bose-Einstein, estaríamos interesados en el número de formas de distribuir los 7 vendedores restantes en 3 estaciones (2, 3 y 4). Sin embargo, como los vendedores eligen independientemente, el enfoque de probabilidad condicional utilizado es más apropiado para este problema.

# Distribución de $W = \frac{Y-X}{2}$ para variables aleatorias uniformes

## Enunciado del problema

Sean las variables aleatorias $X,Y$ uniformes tal que:

$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Hallar y graficar la distribución de $W = \frac{Y-X}{2}$

## Solución

### Paso 1: Análisis del dominio

El dominio $D$ representa una banda diagonal de ancho 2 centrada en la recta $y = x$ y limitada horizontalmente por $x \in (0,4)$.

El área total del dominio es:

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

### Paso 2: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesito transformar la condición:

$$P\left(\frac{Y-X}{2} \leq w\right) = P(Y-X \leq 2w) = P(Y \leq X + 2w)$$

Consideraré diferentes casos según el valor de $w$:

#### Caso 1: $w \leq -\frac{1}{2}$

Si $w \leq -\frac{1}{2}$, entonces $2w \leq -1$.

Como $y > x-1$ (por definición del dominio) y $x+2w \leq x-1$ (ya que $2w \leq -1$), tenemos que $y > x-1 \geq x+2w$.

Por lo tanto, $Y$ siempre es mayor que $X+2w$, lo que significa:
$$F_W(w) = 0 \quad \text{para } w \leq -\frac{1}{2}$$

#### Caso 2: $-\frac{1}{2} < w < \frac{1}{2}$

En este caso, $-1 < 2w < 1$.
La región donde $Y \leq X+2w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+2w) < y < x+1$$

Como $-\frac{1}{2} < w < \frac{1}{2}$, tenemos que $x-1 < x+2w < x+1$, por lo que:
$$0 < x < 4, \quad x-1 < y \leq x+2w$$

El área de esta región es:
$$A = \int_0^4 \int_{x-1}^{x+2w} dy \, dx = \int_0^4 [(x+2w)-(x-1)] \, dx = \int_0^4 (2w+1) \, dx = 4(2w+1)$$

Por lo tanto:
$$F_W(w) = \frac{4(2w+1)}{8} = \frac{2w+1}{2} \quad \text{para } -\frac{1}{2} < w < \frac{1}{2}$$

#### Caso 3: $w \geq \frac{1}{2}$

Si $w \geq \frac{1}{2}$, entonces $2w \geq 1$.

Como $y < x+1$ (por definición del dominio) y $x+2w \geq x+1$ (ya que $2w \geq 1$), tenemos que $y < x+1 \leq x+2w$.

Por lo tanto, $Y$ siempre es menor o igual que $X+2w$, lo que significa:
$$F_W(w) = 1 \quad \text{para } w \geq \frac{1}{2}$$

### Paso 3: Función de distribución completa

La función de distribución acumulada de $W$ es:

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq -\frac{1}{2} \\
\frac{2w+1}{2} & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
1 & \text{si } w \geq \frac{1}{2}
\end{cases}
$$

### Paso 4: Función de densidad de probabilidad

Derivando la función de distribución acumulada, obtenemos la función de densidad:

$$
f_W(w) =
\begin{cases}
0 & \text{si } w < -\frac{1}{2} \\
1 & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
0 & \text{si } w > \frac{1}{2}
\end{cases}
$$

### Conclusión

La variable aleatoria $W = \frac{Y-X}{2}$ sigue una distribución uniforme en el intervalo $[-\frac{1}{2}, \frac{1}{2}]$.

### Gráfico de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq -\frac{1}{2}$: Constante igual a 0
- Para $-\frac{1}{2} < w < \frac{1}{2}$: Recta con pendiente 1, partiendo de $(−\frac{1}{2},0)$ hasta $(\frac{1}{2},1)$
- Para $w \geq \frac{1}{2}$: Constante igual a 1

# Problema de Procesos de Poisson: Clientes conectándose a un servidor

## Enunciado del problema

A y B se conectan a un servidor. Las conexiones que realiza el cliente A ocurren según un proceso de Poisson de 2 por minuto, mientras que para el cliente B ocurren según un proceso de Poisson de 3 por minuto. Los dos procesos de Poisson son independientes. Sabiendo que entre 3:00 y las 3:02 hubo exactamente una conexión al servidor por el cliente A, calcular la probabilidad de que entre 3:00 y 3:05 hayan realizado como máximo 2 conexiones en total.

## Solución

### Datos del problema

- Cliente A: proceso de Poisson con tasa $\lambda_A = 2$ conexiones/minuto
- Cliente B: proceso de Poisson con tasa $\lambda_B = 3$ conexiones/minuto
- Entre 3:00 y 3:02, el cliente A realizó exactamente 1 conexión

### Análisis

Denotemos:

- $N_A(t_1, t_2)$ = número de conexiones del cliente A en el intervalo $(t_1, t_2)$
- $N_B(t_1, t_2)$ = número de conexiones del cliente B en el intervalo $(t_1, t_2)$

Queremos calcular:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1)$$

Sabemos que $N_A(0,5) = N_A(0,2) + N_A(2,5) = 1 + N_A(2,5)$

Por lo tanto:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1) = P(1 + N_A(2,5) + N_B(0,5) \leq 2) = P(N_A(2,5) + N_B(0,5) \leq 1)$$

### Cálculo

Por la propiedad de independencia de incrementos del proceso de Poisson:

- $N_A(2,5)$ sigue una distribución Poisson con parámetro $\lambda_A \cdot 3 = 2 \cdot 3 = 6$
- $N_B(0,5)$ sigue una distribución Poisson con parámetro $\lambda_B \cdot 5 = 3 \cdot 5 = 15$

Por la propiedad de que la suma de variables Poisson independientes también es Poisson:

- $N_A(2,5) + N_B(0,5)$ sigue una distribución Poisson con parámetro $6 + 15 = 21$

Calculamos:
$$P(N_A(2,5) + N_B(0,5) \leq 1) = P(\text{Poisson}(21) \leq 1) = e^{-21} \cdot (1 + 21) = 22 \cdot e^{-21}$$

$$22 \cdot e^{-21} \approx 1.67 \times 10^{-8}$$

La probabilidad pedida es aproximadamente $1.67 \times 10^{-8}$, es decir, extremadamente pequeña (aproximadamente 1 en 60 millones).

# Problema de probabilidad condicional con cajas y bolas

Para resolver este problema, identificaré los eventos y aplicaré el teorema de Bayes.

## Eventos relevantes

- A₁: "Las dos bolas extraídas de C1 son blancas"
- A₂: "Las dos bolas extraídas de C1 son rojas"
- A₃: "Las dos bolas extraídas de C1 son de distinto color"
- B: "La tercera bola extraída es roja"

Necesitamos hallar P(A₂|B).

## Paso 1: Calcular probabilidades del primer evento

En C1 hay 6 bolas blancas y 4 rojas (total 10).

- P(A₁) = C(6,2)/C(10,2) = 15/45 = 1/3
- P(A₂) = C(4,2)/C(10,2) = 6/45 = 2/15
- P(A₃) = 1 - P(A₁) - P(A₂) = 1 - 1/3 - 2/15 = 8/15

## Paso 2: Calcular probabilidades condicionales de B dado cada caso

- Si ocurrió A₁ o A₂, sacamos de C2 (5 blancas, 3 rojas): P(B|A₁) = P(B|A₂) = 3/8
- Si ocurrió A₃, sacamos de C3 (3 blancas, 9 rojas): P(B|A₃) = 9/12 = 3/4

## Paso 3: Calcular P(B) usando la ley de probabilidad total

P(B) = P(B|A₁)P(A₁) + P(B|A₂)P(A₂) + P(B|A₃)P(A₃)
P(B) = (3/8)(1/3) + (3/8)(2/15) + (3/4)(8/15)
P(B) = 1/8 + 1/20 + 2/5 = 5/40 + 2/40 + 16/40 = 23/40

## Paso 4: Aplicar el teorema de Bayes

P(A₂|B) = P(B|A₂)P(A₂)/P(B)
P(A₂|B) = (3/8)(2/15)/(23/40) = (3×2×40)/(8×15×23) = 240/2760 = 2/23

Por lo tanto, la probabilidad de que las dos bolas extraídas de C1 hayan sido rojas, dado que la tercera bola extraída fue roja, es 2/23 ≈ 0.087 (aproximadamente 8.7%).

# Problema de probabilidad: tiempo de espera en el cine

## Enunciado

Nicolás quiere ir a ver su película favorita al cine, que tiene funciones a las 18:00 y a las 23:00. La hora a la que sale de su casa es una variable aleatoria con distribución uniforme entre las 16:00 y las 21:00. Independientemente de la hora de salida, el tiempo de viaje hasta el cine (en horas) es una variable aleatoria con distribución uniforme en el intervalo $(1,2)$. ¿Cuál es la probabilidad de que tenga que esperar más de media hora en el cine hasta que empiece su película?

## Solución

### Definición de variables

- $X$: hora de salida (uniforme en $[16,21]$)
- $Y$: tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: hora de llegada al cine

### Análisis del problema

Para que Nicolás tenga que esperar más de media hora, debe llegar al cine antes de las 17:30, ya que la primera función es a las 18:00.

Necesitamos calcular $P(X+Y < 17.5)$

### Densidades de probabilidad

- $f_X(x) = \frac{1}{21-16} = \frac{1}{5}$ para $16 \leq x \leq 21$
- $f_Y(y) = \frac{1}{2-1} = 1$ para $1 \leq y \leq 2$
- $f_{X,Y}(x,y) = \frac{1}{5} \cdot 1 = \frac{1}{5}$ (por independencia)

### Cálculo de la probabilidad

Identificamos la región donde $X+Y < 17.5$ dentro del dominio $[16,21] \times [1,2]$:

La recta $x+y=17.5$ interseca el dominio formando un triángulo con vértices en $(16,1)$, $(16,1.5)$ y $(16.5,1)$.

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (17.5-x-1) \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (16.5-x) \, dx$$

$$= \frac{1}{5} \cdot \left[16.5x - \frac{x^2}{2}\right]_{16}^{16.5}$$

$$= \frac{1}{5} \cdot \left[(16.5 \cdot 16.5 - \frac{16.5^2}{2}) - (16.5 \cdot 16 - \frac{16^2}{2})\right]$$

$$= \frac{1}{5} \cdot [272.25 - 136.125 - 264 + 128]$$

$$= \frac{1}{5} \cdot 0.125 = 0.025$$

### Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine hasta que empiece su película es $0.025$ o $2.5\%$.

# Análisis de probabilidad del tiempo de espera en el cine

Tienes razón, mi análisis anterior fue incorrecto. Debo considerar ambas funciones de cine (18:00 y 23:00) para determinar correctamente cuándo Nicolás esperará más de media hora.

## Planteamiento correcto

Analizaré los posibles escenarios de llegada de Nicolás al cine:

### Variables

- $X$: Hora de salida de casa ($X \sim U(16,21)$)
- $Y$: Tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: Hora de llegada al cine

### Casos a considerar

1. Si $X+Y < 17.5$: Llega para la función de 18:00 y espera más de media hora
2. Si $17.5 \leq X+Y < 18$: Llega para la función de 18:00 pero espera menos de media hora
3. Si $18 \leq X+Y < 22.5$: Llega después de la función de 18:00 y debe esperar a la de 23:00 (más de media hora)
4. Si $22.5 \leq X+Y \leq 23$: Llega para la función de 23:00 y espera menos de media hora

Por lo tanto, Nicolás esperará más de media hora en los casos 1 y 3, y la probabilidad buscada es:
$P(X+Y < 17.5) + P(18 \leq X+Y < 22.5)$

## Cálculo de la probabilidad

### Para $P(X+Y < 17.5)$:

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx = \frac{0.125}{5} = 0.025$$

### Para $P(18 \leq X+Y < 22.5)$:

Divido esta región en tres partes:

$$
\begin{align*}
P(18 \leq X+Y < 22.5) &= \int_{16}^{17} \int_{18-x}^{2} \frac{1}{5} \, dy \, dx + \int_{17}^{20.5} \int_{1}^{2} \frac{1}{5} \, dy \, dx + \int_{20.5}^{21} \int_{1}^{22.5-x} \frac{1}{5} \, dy \, dx\\
&= 0.1 + 0.7 + 0.075\\
&= 0.875
\end{align*}
$$

### Probabilidad total

$$P(\text{espera} > 30 \text{ min}) = 0.025 + 0.875 = 0.9$$

## Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine es $0.9$ o $90\%$.

# Problema de la Distribución de Cerezas

## Enunciado

El número de cerezas en una tarta es una variable aleatoria que puede valer 4, 5, 6 o 7; con probabilidades 0.2, 0.4, 0.3, 0.1 respectivamente. Calcular aproximadamente la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5.

## Solución

### Paso 1: Calcular la media y varianza de la variable aleatoria

Sea $X$ la variable aleatoria que representa el número de cerezas en una tarta.

$$P(X=4) = 0.2, \quad P(X=5) = 0.4, \quad P(X=6) = 0.3, \quad P(X=7) = 0.1$$

La **media** (valor esperado) de $X$ es:

$$\mu = E[X] = 4 \cdot 0.2 + 5 \cdot 0.4 + 6 \cdot 0.3 + 7 \cdot 0.1 = 5.3$$

Para calcular la **varianza**, primero hallamos $E[X^2]$:

$$E[X^2] = 4^2 \cdot 0.2 + 5^2 \cdot 0.4 + 6^2 \cdot 0.3 + 7^2 \cdot 0.1 = 28.9$$

Luego, la varianza es:

$$\sigma^2 = E[X^2] - (E[X])^2 = 28.9 - 5.3^2 = 28.9 - 28.09 = 0.81$$

La desviación estándar es $\sigma = \sqrt{0.81} = 0.9$

### Paso 2: Aplicar el Teorema Central del Límite

Sea $\bar{X}_{36}$ el promedio de cerezas en 36 tartas.

Por el Teorema Central del Límite, para $n$ grande (36 es suficientemente grande), la distribución de $\bar{X}_n$ se aproxima a una normal con:

$$\bar{X}_{36} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(5.3, \frac{0.81}{36}\right) = N(5.3, 0.0225)$$

### Paso 3: Calcular la probabilidad requerida

$$P(\bar{X}_{36} < 5.5) = P\left(\frac{\bar{X}_{36} - \mu}{\sigma/\sqrt{n}} < \frac{5.5 - 5.3}{0.9/\sqrt{36}}\right) = P(Z < 1.33)$$

Donde $Z$ es una variable aleatoria normal estándar.

Usando la tabla de la distribución normal o una calculadora:

$$P(Z < 1.33) \approx 0.9082$$

Por lo tanto, la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5 es aproximadamente **0.91** o **91%**.

# Problema de vendedores ambulantes en el subte

## Enunciado

Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos vendedores en el subte.

## Solución usando enfoque combinatorio

Planteamiento
Debemos calcular la probabilidad condicional de que todos los vendedores hayan subido en las estaciones 1-4, dado que exactamente uno subió en la estación 1.

Análisis del problema
Tenemos 8 vendedores que eligen independientemente entre 5 estaciones equiprobables
Ya sabemos que exactamente 1 vendedor subió en la estación 1
Para que todos estén en el subte al salir de la estación 4, los 7 vendedores restantes deben haber subido en las estaciones 2, 3 o 4
Cálculo de la probabilidad
Dado que cada vendedor elige su estación independientemente y con probabilidad uniforme ($p=\frac{1}{5}$ para cada estación), y que ya sabemos que uno subió en la estación 1, los 7 restantes deben elegir entre las estaciones 2, 3, 4 o 5.

Para los 7 vendedores restantes:

Probabilidad de subir en una estación específica (sin condiciones): $\frac{1}{5}$
Probabilidad de subir en las estaciones 2, 3 o 4: $\frac{3}{5}$
Probabilidad de subir en la estación 5: $\frac{1}{5}$
Probabilidad condicional de subir en las estaciones 2, 3 o 4 dado que no subió en la estación 1: $\frac{3/5}{4/5} = \frac{3}{4}$
Por lo tanto, la probabilidad de que todos los 7 vendedores restantes hayan subido en las estaciones 2, 3 o 4 es:

$$P(\text{todos los 7 en estaciones 2-4}) = \left(\frac{3}{4}\right)^7$$

Calculando:

$$\left(\frac{3}{4}\right)^7 = \frac{3^7}{4^7} = \frac{2187}{16384} \approx 0.1335$$

La probabilidad buscada es aproximadamente 13.35%.

Observación sobre Bose-Einstein
Si quisiéramos aplicar un enfoque tipo Bose-Einstein, estaríamos interesados en el número de formas de distribuir los 7 vendedores restantes en 3 estaciones (2, 3 y 4). Sin embargo, como los vendedores eligen independientemente, el enfoque de probabilidad condicional utilizado es más apropiado para este problema.

# Distribución de $W = \frac{Y-X}{2}$ para variables aleatorias uniformes

## Enunciado del problema

Sean las variables aleatorias $X,Y$ uniformes tal que:

$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Hallar y graficar la distribución de $W = \frac{Y-X}{2}$

## Solución

### Paso 1: Análisis del dominio

El dominio $D$ representa una banda diagonal de ancho 2 centrada en la recta $y = x$ y limitada horizontalmente por $x \in (0,4)$.

El área total del dominio es:

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

### Paso 2: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesito transformar la condición:

$$P\left(\frac{Y-X}{2} \leq w\right) = P(Y-X \leq 2w) = P(Y \leq X + 2w)$$

Consideraré diferentes casos según el valor de $w$:

#### Caso 1: $w \leq -\frac{1}{2}$

Si $w \leq -\frac{1}{2}$, entonces $2w \leq -1$.

Como $y > x-1$ (por definición del dominio) y $x+2w \leq x-1$ (ya que $2w \leq -1$), tenemos que $y > x-1 \geq x+2w$.

Por lo tanto, $Y$ siempre es mayor que $X+2w$, lo que significa:
$$F_W(w) = 0 \quad \text{para } w \leq -\frac{1}{2}$$

#### Caso 2: $-\frac{1}{2} < w < \frac{1}{2}$

En este caso, $-1 < 2w < 1$.
La región donde $Y \leq X+2w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+2w) < y < x+1$$

Como $-\frac{1}{2} < w < \frac{1}{2}$, tenemos que $x-1 < x+2w < x+1$, por lo que:
$$0 < x < 4, \quad x-1 < y \leq x+2w$$

El área de esta región es:
$$A = \int_0^4 \int_{x-1}^{x+2w} dy \, dx = \int_0^4 [(x+2w)-(x-1)] \, dx = \int_0^4 (2w+1) \, dx = 4(2w+1)$$

Por lo tanto:
$$F_W(w) = \frac{4(2w+1)}{8} = \frac{2w+1}{2} \quad \text{para } -\frac{1}{2} < w < \frac{1}{2}$$

#### Caso 3: $w \geq \frac{1}{2}$

Si $w \geq \frac{1}{2}$, entonces $2w \geq 1$.

Como $y < x+1$ (por definición del dominio) y $x+2w \geq x+1$ (ya que $2w \geq 1$), tenemos que $y < x+1 \leq x+2w$.

Por lo tanto, $Y$ siempre es menor o igual que $X+2w$, lo que significa:
$$F_W(w) = 1 \quad \text{para } w \geq \frac{1}{2}$$

### Paso 3: Función de distribución completa

La función de distribución acumulada de $W$ es:

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq -\frac{1}{2} \\
\frac{2w+1}{2} & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
1 & \text{si } w \geq \frac{1}{2}
\end{cases}
$$

### Paso 4: Función de densidad de probabilidad

Derivando la función de distribución acumulada, obtenemos la función de densidad:

$$
f_W(w) =
\begin{cases}
0 & \text{si } w < -\frac{1}{2} \\
1 & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
0 & \text{si } w > \frac{1}{2}
\end{cases}
$$

### Conclusión

La variable aleatoria $W = \frac{Y-X}{2}$ sigue una distribución uniforme en el intervalo $[-\frac{1}{2}, \frac{1}{2}]$.

### Gráfico de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq -\frac{1}{2}$: Constante igual a 0
- Para $-\frac{1}{2} < w < \frac{1}{2}$: Recta con pendiente 1, partiendo de $(−\frac{1}{2},0)$ hasta $(\frac{1}{2},1)$
- Para $w \geq \frac{1}{2}$: Constante igual a 1

# Problema de Procesos de Poisson: Clientes conectándose a un servidor

## Enunciado del problema

A y B se conectan a un servidor. Las conexiones que realiza el cliente A ocurren según un proceso de Poisson de 2 por minuto, mientras que para el cliente B ocurren según un proceso de Poisson de 3 por minuto. Los dos procesos de Poisson son independientes. Sabiendo que entre 3:00 y las 3:02 hubo exactamente una conexión al servidor por el cliente A, calcular la probabilidad de que entre 3:00 y 3:05 hayan realizado como máximo 2 conexiones en total.

## Solución

### Datos del problema

- Cliente A: proceso de Poisson con tasa $\lambda_A = 2$ conexiones/minuto
- Cliente B: proceso de Poisson con tasa $\lambda_B = 3$ conexiones/minuto
- Entre 3:00 y 3:02, el cliente A realizó exactamente 1 conexión

### Análisis

Denotemos:

- $N_A(t_1, t_2)$ = número de conexiones del cliente A en el intervalo $(t_1, t_2)$
- $N_B(t_1, t_2)$ = número de conexiones del cliente B en el intervalo $(t_1, t_2)$

Queremos calcular:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1)$$

Sabemos que $N_A(0,5) = N_A(0,2) + N_A(2,5) = 1 + N_A(2,5)$

Por lo tanto:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1) = P(1 + N_A(2,5) + N_B(0,5) \leq 2) = P(N_A(2,5) + N_B(0,5) \leq 1)$$

### Cálculo

Por la propiedad de independencia de incrementos del proceso de Poisson:

- $N_A(2,5)$ sigue una distribución Poisson con parámetro $\lambda_A \cdot 3 = 2 \cdot 3 = 6$
- $N_B(0,5)$ sigue una distribución Poisson con parámetro $\lambda_B \cdot 5 = 3 \cdot 5 = 15$

Por la propiedad de que la suma de variables Poisson independientes también es Poisson:

- $N_A(2,5) + N_B(0,5)$ sigue una distribución Poisson con parámetro $6 + 15 = 21$

Calculamos:
$$P(N_A(2,5) + N_B(0,5) \leq 1) = P(\text{Poisson}(21) \leq 1) = e^{-21} \cdot (1 + 21) = 22 \cdot e^{-21}$$

$$22 \cdot e^{-21} \approx 1.67 \times 10^{-8}$$

La probabilidad pedida es aproximadamente $1.67 \times 10^{-8}$, es decir, extremadamente pequeña (aproximadamente 1 en 60 millones).

# Problema de probabilidad condicional con cajas y bolas

Para resolver este problema, identificaré los eventos y aplicaré el teorema de Bayes.

## Eventos relevantes

- A₁: "Las dos bolas extraídas de C1 son blancas"
- A₂: "Las dos bolas extraídas de C1 son rojas"
- A₃: "Las dos bolas extraídas de C1 son de distinto color"
- B: "La tercera bola extraída es roja"

Necesitamos hallar P(A₂|B).

## Paso 1: Calcular probabilidades del primer evento

En C1 hay 6 bolas blancas y 4 rojas (total 10).

- P(A₁) = C(6,2)/C(10,2) = 15/45 = 1/3
- P(A₂) = C(4,2)/C(10,2) = 6/45 = 2/15
- P(A₃) = 1 - P(A₁) - P(A₂) = 1 - 1/3 - 2/15 = 8/15

## Paso 2: Calcular probabilidades condicionales de B dado cada caso

- Si ocurrió A₁ o A₂, sacamos de C2 (5 blancas, 3 rojas): P(B|A₁) = P(B|A₂) = 3/8
- Si ocurrió A₃, sacamos de C3 (3 blancas, 9 rojas): P(B|A₃) = 9/12 = 3/4

## Paso 3: Calcular P(B) usando la ley de probabilidad total

P(B) = P(B|A₁)P(A₁) + P(B|A₂)P(A₂) + P(B|A₃)P(A₃)
P(B) = (3/8)(1/3) + (3/8)(2/15) + (3/4)(8/15)
P(B) = 1/8 + 1/20 + 2/5 = 5/40 + 2/40 + 16/40 = 23/40

## Paso 4: Aplicar el teorema de Bayes

P(A₂|B) = P(B|A₂)P(A₂)/P(B)
P(A₂|B) = (3/8)(2/15)/(23/40) = (3×2×40)/(8×15×23) = 240/2760 = 2/23

Por lo tanto, la probabilidad de que las dos bolas extraídas de C1 hayan sido rojas, dado que la tercera bola extraída fue roja, es 2/23 ≈ 0.087 (aproximadamente 8.7%).

# Problema de probabilidad: tiempo de espera en el cine

## Enunciado

Nicolás quiere ir a ver su película favorita al cine, que tiene funciones a las 18:00 y a las 23:00. La hora a la que sale de su casa es una variable aleatoria con distribución uniforme entre las 16:00 y las 21:00. Independientemente de la hora de salida, el tiempo de viaje hasta el cine (en horas) es una variable aleatoria con distribución uniforme en el intervalo $(1,2)$. ¿Cuál es la probabilidad de que tenga que esperar más de media hora en el cine hasta que empiece su película?

## Solución

### Definición de variables

- $X$: hora de salida (uniforme en $[16,21]$)
- $Y$: tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: hora de llegada al cine

### Análisis del problema

Para que Nicolás tenga que esperar más de media hora, debe llegar al cine antes de las 17:30, ya que la primera función es a las 18:00.

Necesitamos calcular $P(X+Y < 17.5)$

### Densidades de probabilidad

- $f_X(x) = \frac{1}{21-16} = \frac{1}{5}$ para $16 \leq x \leq 21$
- $f_Y(y) = \frac{1}{2-1} = 1$ para $1 \leq y \leq 2$
- $f_{X,Y}(x,y) = \frac{1}{5} \cdot 1 = \frac{1}{5}$ (por independencia)

### Cálculo de la probabilidad

Identificamos la región donde $X+Y < 17.5$ dentro del dominio $[16,21] \times [1,2]$:

La recta $x+y=17.5$ interseca el dominio formando un triángulo con vértices en $(16,1)$, $(16,1.5)$ y $(16.5,1)$.

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (17.5-x-1) \, dx$$

$$= \int_{16}^{16.5} \frac{1}{5} \cdot (16.5-x) \, dx$$

$$= \frac{1}{5} \cdot \left[16.5x - \frac{x^2}{2}\right]_{16}^{16.5}$$

$$= \frac{1}{5} \cdot \left[(16.5 \cdot 16.5 - \frac{16.5^2}{2}) - (16.5 \cdot 16 - \frac{16^2}{2})\right]$$

$$= \frac{1}{5} \cdot [272.25 - 136.125 - 264 + 128]$$

$$= \frac{1}{5} \cdot 0.125 = 0.025$$

### Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine hasta que empiece su película es $0.025$ o $2.5\%$.

# Análisis de probabilidad del tiempo de espera en el cine

Tienes razón, mi análisis anterior fue incorrecto. Debo considerar ambas funciones de cine (18:00 y 23:00) para determinar correctamente cuándo Nicolás esperará más de media hora.

## Planteamiento correcto

Analizaré los posibles escenarios de llegada de Nicolás al cine:

### Variables

- $X$: Hora de salida de casa ($X \sim U(16,21)$)
- $Y$: Tiempo de viaje en horas (uniforme en $[1,2]$)
- $X+Y$: Hora de llegada al cine

### Casos a considerar

1. Si $X+Y < 17.5$: Llega para la función de 18:00 y espera más de media hora
2. Si $17.5 \leq X+Y < 18$: Llega para la función de 18:00 pero espera menos de media hora
3. Si $18 \leq X+Y < 22.5$: Llega después de la función de 18:00 y debe esperar a la de 23:00 (más de media hora)
4. Si $22.5 \leq X+Y \leq 23$: Llega para la función de 23:00 y espera menos de media hora

Por lo tanto, Nicolás esperará más de media hora en los casos 1 y 3, y la probabilidad buscada es:
$P(X+Y < 17.5) + P(18 \leq X+Y < 22.5)$

## Cálculo de la probabilidad

### Para $P(X+Y < 17.5)$:

$$P(X+Y < 17.5) = \int_{16}^{16.5} \int_{1}^{17.5-x} \frac{1}{5} \, dy \, dx = \frac{0.125}{5} = 0.025$$

### Para $P(18 \leq X+Y < 22.5)$:

Divido esta región en tres partes:

$$
\begin{align*}
P(18 \leq X+Y < 22.5) &= \int_{16}^{17} \int_{18-x}^{2} \frac{1}{5} \, dy \, dx + \int_{17}^{20.5} \int_{1}^{2} \frac{1}{5} \, dy \, dx + \int_{20.5}^{21} \int_{1}^{22.5-x} \frac{1}{5} \, dy \, dx\\
&= 0.1 + 0.7 + 0.075\\
&= 0.875
\end{align*}
$$

### Probabilidad total

$$P(\text{espera} > 30 \text{ min}) = 0.025 + 0.875 = 0.9$$

## Respuesta

La probabilidad de que Nicolás tenga que esperar más de media hora en el cine es $0.9$ o $90\%$.

# Problema de la Distribución de Cerezas

## Enunciado

El número de cerezas en una tarta es una variable aleatoria que puede valer 4, 5, 6 o 7; con probabilidades 0.2, 0.4, 0.3, 0.1 respectivamente. Calcular aproximadamente la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5.

## Solución

### Paso 1: Calcular la media y varianza de la variable aleatoria

Sea $X$ la variable aleatoria que representa el número de cerezas en una tarta.

$$P(X=4) = 0.2, \quad P(X=5) = 0.4, \quad P(X=6) = 0.3, \quad P(X=7) = 0.1$$

La **media** (valor esperado) de $X$ es:

$$\mu = E[X] = 4 \cdot 0.2 + 5 \cdot 0.4 + 6 \cdot 0.3 + 7 \cdot 0.1 = 5.3$$

Para calcular la **varianza**, primero hallamos $E[X^2]$:

$$E[X^2] = 4^2 \cdot 0.2 + 5^2 \cdot 0.4 + 6^2 \cdot 0.3 + 7^2 \cdot 0.1 = 28.9$$

Luego, la varianza es:

$$\sigma^2 = E[X^2] - (E[X])^2 = 28.9 - 5.3^2 = 28.9 - 28.09 = 0.81$$

La desviación estándar es $\sigma = \sqrt{0.81} = 0.9$

### Paso 2: Aplicar el Teorema Central del Límite

Sea $\bar{X}_{36}$ el promedio de cerezas en 36 tartas.

Por el Teorema Central del Límite, para $n$ grande (36 es suficientemente grande), la distribución de $\bar{X}_n$ se aproxima a una normal con:

$$\bar{X}_{36} \sim N\left(\mu, \frac{\sigma^2}{n}\right) = N\left(5.3, \frac{0.81}{36}\right) = N(5.3, 0.0225)$$

### Paso 3: Calcular la probabilidad requerida

$$P(\bar{X}_{36} < 5.5) = P\left(\frac{\bar{X}_{36} - \mu}{\sigma/\sqrt{n}} < \frac{5.5 - 5.3}{0.9/\sqrt{36}}\right) = P(Z < 1.33)$$

Donde $Z$ es una variable aleatoria normal estándar.

Usando la tabla de la distribución normal o una calculadora:

$$P(Z < 1.33) \approx 0.9082$$

Por lo tanto, la probabilidad de que el número promedio de cerezas en 36 tartas sea menor que 5.5 es aproximadamente **0.91** o **91%**.

# Problema de vendedores ambulantes en el subte

## Enunciado

Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos vendedores en el subte.

## Solución usando enfoque combinatorio

Planteamiento
Debemos calcular la probabilidad condicional de que todos los vendedores hayan subido en las estaciones 1-4, dado que exactamente uno subió en la estación 1.

Análisis del problema
Tenemos 8 vendedores que eligen independientemente entre 5 estaciones equiprobables
Ya sabemos que exactamente 1 vendedor subió en la estación 1
Para que todos estén en el subte al salir de la estación 4, los 7 vendedores restantes deben haber subido en las estaciones 2, 3 o 4
Cálculo de la probabilidad
Dado que cada vendedor elige su estación independientemente y con probabilidad uniforme ($p=\frac{1}{5}$ para cada estación), y que ya sabemos que uno subió en la estación 1, los 7 restantes deben elegir entre las estaciones 2, 3, 4 o 5.

Para los 7 vendedores restantes:

Probabilidad de subir en una estación específica (sin condiciones): $\frac{1}{5}$
Probabilidad de subir en las estaciones 2, 3 o 4: $\frac{3}{5}$
Probabilidad de subir en la estación 5: $\frac{1}{5}$
Probabilidad condicional de subir en las estaciones 2, 3 o 4 dado que no subió en la estación 1: $\frac{3/5}{4/5} = \frac{3}{4}$
Por lo tanto, la probabilidad de que todos los 7 vendedores restantes hayan subido en las estaciones 2, 3 o 4 es:

$$P(\text{todos los 7 en estaciones 2-4}) = \left(\frac{3}{4}\right)^7$$

Calculando:

$$\left(\frac{3}{4}\right)^7 = \frac{3^7}{4^7} = \frac{2187}{16384} \approx 0.1335$$

La probabilidad buscada es aproximadamente 13.35%.

Observación sobre Bose-Einstein
Si quisiéramos aplicar un enfoque tipo Bose-Einstein, estaríamos interesados en el número de formas de distribuir los 7 vendedores restantes en 3 estaciones (2, 3 y 4). Sin embargo, como los vendedores eligen independientemente, el enfoque de probabilidad condicional utilizado es más apropiado para este problema.

# Distribución de $W = \frac{Y-X}{2}$ para variables aleatorias uniformes

## Enunciado del problema

Sean las variables aleatorias $X,Y$ uniformes tal que:

$$D = \{(x,y) \in \mathbb{R}^2 : 0 < x < 4, \, x-1 < y < x+1\}$$

Hallar y graficar la distribución de $W = \frac{Y-X}{2}$

## Solución

### Paso 1: Análisis del dominio

El dominio $D$ representa una banda diagonal de ancho 2 centrada en la recta $y = x$ y limitada horizontalmente por $x \in (0,4)$.

El área total del dominio es:

$$A_{total} = \int_0^4 \int_{x-1}^{x+1} dy \, dx = \int_0^4 2 \, dx = 8$$

### Paso 2: Análisis de la función de distribución $F_W(w) = P(W \leq w)$

Para calcular $P(W \leq w)$, necesito transformar la condición:

$$P\left(\frac{Y-X}{2} \leq w\right) = P(Y-X \leq 2w) = P(Y \leq X + 2w)$$

Consideraré diferentes casos según el valor de $w$:

#### Caso 1: $w \leq -\frac{1}{2}$

Si $w \leq -\frac{1}{2}$, entonces $2w \leq -1$.

Como $y > x-1$ (por definición del dominio) y $x+2w \leq x-1$ (ya que $2w \leq -1$), tenemos que $y > x-1 \geq x+2w$.

Por lo tanto, $Y$ siempre es mayor que $X+2w$, lo que significa:
$$F_W(w) = 0 \quad \text{para } w \leq -\frac{1}{2}$$

#### Caso 2: $-\frac{1}{2} < w < \frac{1}{2}$

En este caso, $-1 < 2w < 1$.
La región donde $Y \leq X+2w$ está delimitada por:
$$0 < x < 4, \quad \max(x-1, x+2w) < y < x+1$$

Como $-\frac{1}{2} < w < \frac{1}{2}$, tenemos que $x-1 < x+2w < x+1$, por lo que:
$$0 < x < 4, \quad x-1 < y \leq x+2w$$

El área de esta región es:
$$A = \int_0^4 \int_{x-1}^{x+2w} dy \, dx = \int_0^4 [(x+2w)-(x-1)] \, dx = \int_0^4 (2w+1) \, dx = 4(2w+1)$$

Por lo tanto:
$$F_W(w) = \frac{4(2w+1)}{8} = \frac{2w+1}{2} \quad \text{para } -\frac{1}{2} < w < \frac{1}{2}$$

#### Caso 3: $w \geq \frac{1}{2}$

Si $w \geq \frac{1}{2}$, entonces $2w \geq 1$.

Como $y < x+1$ (por definición del dominio) y $x+2w \geq x+1$ (ya que $2w \geq 1$), tenemos que $y < x+1 \leq x+2w$.

Por lo tanto, $Y$ siempre es menor o igual que $X+2w$, lo que significa:
$$F_W(w) = 1 \quad \text{para } w \geq \frac{1}{2}$$

### Paso 3: Función de distribución completa

La función de distribución acumulada de $W$ es:

$$
F_W(w) =
\begin{cases}
0 & \text{si } w \leq -\frac{1}{2} \\
\frac{2w+1}{2} & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
1 & \text{si } w \geq \frac{1}{2}
\end{cases}
$$

### Paso 4: Función de densidad de probabilidad

Derivando la función de distribución acumulada, obtenemos la función de densidad:

$$
f_W(w) =
\begin{cases}
0 & \text{si } w < -\frac{1}{2} \\
1 & \text{si } -\frac{1}{2} < w < \frac{1}{2} \\
0 & \text{si } w > \frac{1}{2}
\end{cases}
$$

### Conclusión

La variable aleatoria $W = \frac{Y-X}{2}$ sigue una distribución uniforme en el intervalo $[-\frac{1}{2}, \frac{1}{2}]$.

### Gráfico de la función de distribución

La gráfica de $F_W(w)$ es:

- Para $w \leq -\frac{1}{2}$: Constante igual a 0
- Para $-\frac{1}{2} < w < \frac{1}{2}$: Recta con pendiente 1, partiendo de $(−\frac{1}{2},0)$ hasta $(\frac{1}{2},1)$
- Para $w \geq \frac{1}{2}$: Constante igual a 1

# Problema de Procesos de Poisson: Clientes conectándose a un servidor

## Enunciado del problema

A y B se conectan a un servidor. Las conexiones que realiza el cliente A ocurren según un proceso de Poisson de 2 por minuto, mientras que para el cliente B ocurren según un proceso de Poisson de 3 por minuto. Los dos procesos de Poisson son independientes. Sabiendo que entre 3:00 y las 3:02 hubo exactamente una conexión al servidor por el cliente A, calcular la probabilidad de que entre 3:00 y 3:05 hayan realizado como máximo 2 conexiones en total.

## Solución

### Datos del problema

- Cliente A: proceso de Poisson con tasa $\lambda_A = 2$ conexiones/minuto
- Cliente B: proceso de Poisson con tasa $\lambda_B = 3$ conexiones/minuto
- Entre 3:00 y 3:02, el cliente A realizó exactamente 1 conexión

### Análisis

Denotemos:

- $N_A(t_1, t_2)$ = número de conexiones del cliente A en el intervalo $(t_1, t_2)$
- $N_B(t_1, t_2)$ = número de conexiones del cliente B en el intervalo $(t_1, t_2)$

Queremos calcular:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1)$$

Sabemos que $N_A(0,5) = N_A(0,2) + N_A(2,5) = 1 + N_A(2,5)$

Por lo tanto:
$$P(N_A(0,5) + N_B(0,5) \leq 2 \mid N_A(0,2) = 1) = P(1 + N_A(2,5) + N_B(0,5) \leq 2) = P(N_A(2,5) + N_B(0,5) \leq 1)$$

### Cálculo

Por la propiedad de independencia de incrementos del proceso de Poisson:

- $N_A(2,5)$ sigue una distribución Poisson con parámetro $\lambda_A \cdot 3 = 2 \cdot 3 = 6$
- $N_B(0,5)$ sigue una distribución Poisson con parámetro $\lambda_B \cdot 5 = 3 \cdot 5 = 15$

Por la propiedad de que la suma de variables Poisson independientes también es Poisson:

- $N_A(2,5) + N_B(0,5)$ sigue una distribución Poisson con parámetro $6 + 15 = 21$

Calculamos:
$$P(N_A(2,5) + N_B(0,5) \leq 1) = P(\text{Poisson}(21) \leq 1) = e^{-21} \cdot (1 + 21) = 22 $$

4. **Obtener la distribución de la suma**  
   $\sum_{i=1}^{10} Y_i \sim \text{Gamma}(10, 1/24)$

5. **Calcular el p-valor**  
   El p-valor es la probabilidad de observar un valor de $S$ tan extremo (o más) como el observado, bajo $H_0$:

   $$
   \text{p-valor} = P\left(\sum_{i=1}^{10} Y_i \geq S_{\text{obs}}\right)
   $$

   donde $S_{\text{obs}}$ es el valor observado en la muestra.

6. **Cálculo numérico**  
   Puedes calcular esta probabilidad usando la función de cola superior de la distribución gamma, por ejemplo con una calculadora estadística o software como R, Python (scipy.stats.gamma), etc.

---

**En resumen:**  
El p-valor es la probabilidad de que la suma de 10 variables gamma (o exponenciales) sea mayor o igual al valor observado, bajo la hipótesis nula.

¡Perfecto! Para un test genérico, el **algoritmo para calcular el p-valor** es:

---

### **Algoritmo para calcular el p-valor en un test de hipótesis**

1. **Plantear las hipótesis**

   - Hipótesis nula $H_0$
   - Hipótesis alternativa $H_1$

2. **Elegir el estadístico de test**

   - Ejemplo: media muestral, suma, razón de verosimilitudes, etc.

3. **Calcular el valor observado del estadístico**

   - Usar los datos de la muestra para obtener $T_{\text{obs}}$

4. **Determinar la distribución del estadístico bajo $H_0$**

   - Puede ser normal, t, chi-cuadrado, binomial, etc.

5. **Calcular el p-valor**

   - **Test unilateral superior:**  
     $p$-valor $= P(T \geq T_{\text{obs}} \mid H_0)$
   - **Test unilateral inferior:**  
     $p$-valor $= P(T \leq T_{\text{obs}} \mid H_0)$
   - **Test bilateral:**  
     $p$-valor $= 2 \cdot \min\{P(T \geq T_{\text{obs}}),\ P(T \leq T_{\text{obs}})\}$

6. **Interpretar el p-valor**
   - Si $p$-valor $< \alpha$, rechazar $H_0$
   - Si $p$-valor $\geq \alpha$, no rechazar $H_0$

---

**En resumen:**  
El p-valor es la probabilidad, bajo $H_0$, de observar un estadístico tan extremo (o más) como el obtenido en la muestra.

Perfecto, aquí va la resolución paso a paso, usando solo signos de dólar para las fórmulas KaTeX:

---

Antes del año 2000, la proporción de muertes por cáncer era $p_0 = 0.20$.  
Se toma una muestra de $n = 200$ fallecidos después del año 2000 y se observa $x = 50$ muertes por cáncer.

---

**1. Planteo de hipótesis**

- $H_0: p = 0.20$
- $H_1: p > 0.20$

---

**2. Estadístico de test**

La variable $X$ (número de muertes por cáncer) es binomial: $X \sim \text{Binomial}(n, p)$.

El estadístico es la proporción muestral:  
$\hat{p} = \frac{X}{n} = \frac{50}{200} = 0.25$

---

**3. Región crítica (nivel asintótico 0.05)**

Para $n$ grande, bajo $H_0$,  
$\hat{p} \sim N\left(p_0, \frac{p_0(1-p_0)}{n}\right)$

Calculamos el valor crítico:

$\sigma_0 = \sqrt{\frac{0.20 \times 0.80}{200}} = \sqrt{0.0016} = 0.04$

El valor crítico para $\alpha = 0.05$ (unilateral derecha) es $z_{0.95} \approx 1.645$.

Región crítica:  
Rechazo $H_0$ si  
$\frac{\hat{p} - 0.20}{0.04} > 1.645$

---

**4. Cálculo con la muestra**

$\frac{0.25 - 0.20}{0.04} = \frac{0.05}{0.04} = 1.25$

Como $1.25 < 1.645$, **no se rechaza $H_0$**.

---

**5. p-valor**

El p-valor es  
$p$-valor $= P_{H_0}\left( \frac{\hat{p} - 0.20}{0.04} \geq 1.25 \right) = 1 - \Phi(1.25) \approx 1 - 0.8944 = 0.1056$

---

**Resumen:**

- Estadístico observado: $z = 1.25$
- Decisión: **No se rechaza $H_0$**
- p-valor aproximado: $0.106$

Claro, aquí tienes la resolución usando solo signos de dólar para las fórmulas KaTeX:

---

Sea $X_i$ la duración (en minutos) de la llamada $i$, con $X_i \sim \text{Exp}(1/10)$, independientes.

El costo de cada llamada es $C_i = \lceil X_i / 2 \rceil$, donde $\lceil \cdot \rceil$ es el techo (redondeo hacia arriba).

El dinero total facturado es $S = C_1 + C_2 + C_3 + C_4$.

---

**Distribución de $C_i$**

Para $k = 1, 2, 3, \ldots$:

$P(C_i = k) = P(2(k-1) < X_i \leq 2k) = P(X_i > 2(k-1)) - P(X_i > 2k)$

Sabemos que $P(X_i > t) = e^{-t/10}$.

Entonces,

$P(C_i = k) = e^{-2(k-1)/10} - e^{-2k/10} = e^{-0.2(k-1)} - e^{-0.2k}$

---

**Distribución de $S$**

$S$ es la suma de 4 variables independientes, cada una con la distribución discreta dada arriba.

La distribución de $S$ es la convolución de 4 veces la distribución de $C_i$:

$P(S = n) = \sum_{k_1 + k_2 + k_3 + k_4 = n} \prod_{j=1}^4 P(C_j = k_j)$

donde cada $k_j \geq 1$.

---

**Resumen**

- Cada llamada se factura como $C_i$, con $P(C_i = k) = e^{-0.2(k-1)} - e^{-0.2k}$ para $k = 1, 2, 3, \ldots$
- El total facturado $S$ es la suma de 4 variables independientes con esa distribución.

No hay una fórmula cerrada simple para $S$, pero su distribución es la suma de 4 variables independientes con la ley anterior.

¡Sí, tu razonamiento es correcto!

Te resumo lo que hiciste y te marco los puntos clave:

1. Definiste $X \sim \text{Exp}(10)$ (media 10 minutos).
2. Definiste $D$ como el dinero facturado por llamada: $D = \lceil X/2 \rceil$.
3. Calculaste la función de distribución de $D$:
   $$
   F_D(d) = P(D \leq d) = P\left(X \leq 2d\right) = 1 - e^{-2d/10}
   $$
   para $d = 1, 2, 3, \ldots$
4. Calculaste la probabilidad puntual:

   $$
   P(D = k) = F_D(k) - F_D(k-1) = \left[1 - e^{-0.2k}\right] - \left[1 - e^{-0.2(k-1)}\right] = e^{-0.2(k-1)} - e^{-0.2k}
   $$

   que es lo correcto.

5. Para el total facturado en 4 llamadas, $S = D_1 + D_2 + D_3 + D_4$, aclaraste que es la suma de 4 variables independientes con esa ley, y que la distribución de $S$ es la convolución de esas 4.

**Conclusión:**  
Tu planteo es correcto y la deducción de la ley de $D$ es precisa.  
La distribución de $S$ es la suma de 4 variables independientes con esa ley, y no tiene una forma cerrada simple.

¡Bien hecho!

Perfecto, aquí va la resolución usando solo signos de dólar para las fórmulas KaTeX:

---

En la ruleta hay 18 rojas, 18 negras y 1 verde.  
Nerea apuesta siempre al rojo.

Sea $N$ la cantidad de juegos hasta ganar por primera vez (es decir, hasta que salga rojo por primera vez).  
Sea $M$ la cantidad de verdes observados en esos $N$ juegos.

Queremos hallar la recta de regresión de $M$ dado $N$, es decir, $E[M|N]$.

---

**1. Distribución de $N$**

La probabilidad de rojo es $p = \frac{18}{37}$.

$N$ tiene distribución geométrica:  
$P(N = n) = (1-p)^{n-1} p$

---

**2. Distribución de $M$ dado $N$**

En los $N$ juegos, hay exactamente 1 rojo (en la jugada $N$), y $N-1$ juegos previos que no fueron rojos (fueron negros o verdes).

En esos $N-1$ juegos, cada uno puede ser verde con probabilidad $q = \frac{1}{19}$ (porque, condicionado a no ser rojo: negro o verde, y verde es $1/19$ de esos).

Demostración:

- $P(\text{verde}) = \frac{1}{37}$
- $P(\text{no rojo}) = \frac{19}{37}$
- $P(\text{verde} \mid \text{no rojo}) = \frac{1/37}{19/37} = \frac{1}{19}$

Entonces, dado $N=n$, $M$ es binomial:  
$M \mid N=n \sim \text{Binomial}(n-1, 1/19)$

---

**3. Recta de regresión**

$E[M|N=n] = (n-1) \cdot \frac{1}{19}$

La recta de regresión es:

$$
E[M|N] = \frac{N-1}{19}
$$

---

**Respuesta final:**

La recta de regresión de $M$ dado $N$ es

$$
E[M|N] = \frac{N-1}{19}
$$

Perfecto, aquí va la resolución usando solo signos de dólar para las fórmulas KaTeX:

---

Sea $X_i \sim \text{Rayleigh}(\sqrt{\theta})$, $i=1,\ldots,20$.  
Se observa $\sum_{i=1}^{20} x_i^2 = 500$.

La función de densidad es  
$f(x) = \frac{x}{\theta} e^{-x^2/(2\theta)}$ para $x > 0$.

---

**1. Distribución pivotal**

Sabemos que si $X \sim \text{Rayleigh}(\sqrt{\theta})$, entonces $X^2 \sim \text{Exp}(\theta/2)$.

Por lo tanto,  
$\sum_{i=1}^{20} X_i^2 \sim \text{Gamma}(20, \theta/2)$  
o equivalentemente,  
$\frac{2}{\theta} \sum_{i=1}^{20} X_i^2 \sim \chi^2_{40}$

---

**2. Intervalo de confianza**

Queremos un intervalo de confianza para $\theta$ de nivel $0.99$.

Sea $S = \sum_{i=1}^{20} x_i^2 = 500$.

Sabemos que  
$\frac{2S}{\theta} \sim \chi^2_{40}$

Entonces,  
$P\left( a < \frac{2S}{\theta} < b \right) = 0.99$

donde $a = \chi^2_{40,\,0.005}$ y $b = \chi^2_{40,\,0.995}$ (cuantiles de la chi-cuadrado con 40 grados de libertad).

Despejando $\theta$:

$P\left( \frac{2S}{b} < \theta < \frac{2S}{a} \right) = 0.99$

---

**3. Respuesta final**

El intervalo de confianza de nivel $0.99$ para $\theta$ es

$$
\left( \frac{2 \times 500}{\chi^2_{40,\,0.995}},\ \frac{2 \times 500}{\chi^2_{40,\,0.005}} \right )
$$

donde $\chi^2_{40,\,0.995}$ y $\chi^2_{40,\,0.005}$ son los percentiles 0.5% y 99.5% de la chi-cuadrado con 40 grados de libertad.

Buena observación, pero hay un pequeño error en la parametrización.

Si $X \sim \text{Rayleigh}(\sigma)$, entonces la densidad es:

$$
f(x) = \frac{x}{\sigma^2} e^{-x^2/(2\sigma^2)}, \quad x > 0
$$

En este caso, la variable $Y = X^2$ tiene distribución exponencial con parámetro $\lambda = \frac{1}{2\sigma^2}$, es decir:

$$
Y \sim \text{Exp}\left(\frac{1}{2\sigma^2}\right)
$$

Pero en el enunciado, la Rayleigh está parametrizada con $\sqrt{\theta}$, es decir, $\sigma = \sqrt{\theta}$, así que:

$$
Y = X^2 \sim \text{Exp}\left(\frac{1}{2\theta}\right)
$$

La media de esta exponencial es $2\theta$.

Por eso, en la resolución se usa que $X^2 \sim \text{Exp}(1/(2\theta))$, y por lo tanto, la suma $\sum X_i^2$ es Gamma$(n, 1/(2\theta))$ o, lo que es lo mismo, $2\sum X_i^2/\theta \sim \chi^2_{2n}$.

**Resumen:**

- $X \sim \text{Rayleigh}(\sqrt{\theta})$
- $X^2 \sim \text{Exp}(1/(2\theta))$

¡Tu intuición era correcta, solo que el parámetro es $1/(2\theta)$, no $1/(2\theta^2)$!

El intervalo de confianza de nivel $0.99$ para $\theta$ queda así:

Sabemos que si $X_i \sim \text{Rayleigh}(\sqrt{\theta})$, entonces $X_i^2 \sim \text{Exp}(1/(2\theta))$.

Por lo tanto,  
$\frac{1}{2\theta} \sum_{i=1}^{20} X_i^2 \sim \chi^2_{40}$

Sea $S = \sum_{i=1}^{20} x_i^2 = 500$.

Entonces, usando los percentiles $a = \chi^2_{40,\,0.005}$ y $b = \chi^2_{40,\,0.995}$:

$$
P\left( a < \frac{1}{2\theta} S < b \right) = 0.99
$$

Despejando $\theta$:

$$
P\left( \frac{S}{2b} < \theta < \frac{S}{2a} \right) = 0.99
$$

**Respuesta final:**

El intervalo de confianza de nivel $0.99$ para $\theta$ es

$$
\left( \frac{500}{2\,\chi^2_{40,\,0.995}},\ \frac{500}{2\,\chi^2_{40,\,0.005}} \right )
$$

donde $\chi^2_{40,\,0.995}$ y $\chi^2_{40,\,0.005}$ son los percentiles 0.5% y 99.5% de la chi-cuadrado con 40 grados de libertad.

Perfecto, aquí va la resolución usando solo signos de dólar para las fórmulas KaTeX:

---

**Datos:**

- Proceso de Poisson de intensidad $\lambda$ por hora.
- En 30 minutos ($t = 0.5$ horas) se observaron $k = 3$ partículas.
- Priori: $\lambda \sim \text{Exp}(1/2)$ (media 2).

---

**1. Verosimilitud**

La probabilidad de observar $k$ partículas en $t$ horas es:

$$
P(k \mid \lambda) = \frac{(\lambda t)^k}{k!} e^{-\lambda t}
$$

---

**2. Priori**

$$
\pi(\lambda) = \frac{1}{2} e^{-\lambda/2}
$$

---

**3. Posterior**

La distribución a posteriori es proporcional a:

$$
\pi(\lambda \mid k) \propto P(k \mid \lambda) \cdot \pi(\lambda)
$$

Sustituyendo:

$$
\pi(\lambda \mid k) \propto (\lambda t)^k e^{-\lambda t} \cdot e^{-\lambda/2}
= \lambda^k e^{-\lambda (t + 1/2)}
$$

Para $t = 0.5$, $k = 3$:

$$
\pi(\lambda \mid k) \propto \lambda^3 e^{-\lambda (1)}
$$

Esto es la densidad de una Gamma con parámetros $(4, 1)$ (porque $\lambda^{a-1} e^{-\lambda/b}$, aquí $a=4$, $b=1$).

---

**4. Media a posteriori**

La media de una Gamma$(a, b)$ es $ab$.

Aquí, $a = 4$, $b = 1$.

$$
E[\lambda \mid \text{datos}] = 4 \times 1 = 4
$$

---

**Respuesta final:**

La media a posteriori para $\lambda$ es

$$
\boxed{4}
$$

Claro, vamos a resolver el problema paso a paso y de forma clara:

---

**Problema:**  
Sobre un segmento de 1 metro se marcan dos puntos seleccionados al azar y de forma independiente. Calcular la probabilidad de que alguno de los tres segmentos resultantes mida menos de 20 cm.

---

**Planteo:**

Llamemos $X$ y $Y$ a las posiciones de los dos puntos, con $X, Y \sim U(0,1)$ independientes.  
Sin pérdida de generalidad, supongamos $X < Y$ (la probabilidad es la misma si $Y < X$).

Los tres segmentos son:

- $L_1 = X$
- $L_2 = Y - X$
- $L_3 = 1 - Y$

Queremos calcular $P(\min\{L_1, L_2, L_3\} < 0.2)$.

---

**Cálculo de la probabilidad:**

Primero, calculemos la probabilidad complementaria:  
$P(\min\{L_1, L_2, L_3\} \geq 0.2)$, es decir, que los tres segmentos midan al menos 20 cm.

Esto ocurre si:

- $X \geq 0.2$
- $Y - X \geq 0.2 \implies Y \geq X + 0.2$
- $1 - Y \geq 0.2 \implies Y \leq 0.8$

Como $X < Y$, el dominio es $0 < X < Y < 1$.

Entonces, el conjunto favorable es:

- $0.2 \leq X \leq 0.6$
- $X + 0.2 \leq Y \leq 0.8$

(Para que $X + 0.2 \leq 0.8 \implies X \leq 0.6$)

La probabilidad es el área de este conjunto dividido por el área total del triángulo $0 < X < Y < 1$, que es $1/2$.

Calculamos el área favorable:

$$
\int_{X=0.2}^{0.6} \int_{Y=X+0.2}^{0.8} dY\,dX
= \int_{0.2}^{0.6} [0.8 - (X+0.2)]\,dX
= \int_{0.2}^{0.6} (0.6 - X)\,dX
$$

$$
= \left[0.6X - \frac{1}{2}X^2\right]_{0.2}^{0.6}
$$

Calculamos los valores:

Para $X=0.6$: $0.6 \times 0.6 - 0.5 \times 0.6^2 = 0.36 - 0.18 = 0.18$

Para $X=0.2$: $0.6 \times 0.2 - 0.5 \times 0.2^2 = 0.12 - 0.02 = 0.10$

Entonces, el área es $0.18 - 0.10 = 0.08$

La probabilidad pedida es:

$$
P(\min\{L_1, L_2, L_3\} < 0.2) = 1 - \frac{0.08}{0.5} = 1 - 0.16 = 0.84
$$

---

**Respuesta final:**

La probabilidad de que alguno de los tres segmentos mida menos de 20 cm es $0.84$ (o $84\%$).

¡Muy buena observación! Veamos cómo se interpreta tu planteo y por qué el resultado es el mismo.

---

Si planteás la integral así:

$$
\int_{X=0.2}^{0.6} \int_{Y=X+0.2}^{0.8} dY\,dX
$$

Eso corresponde al área donde los tres segmentos miden al menos $0.2$.

Pero si lo planteás como:

$$
\int_{X=0.2}^{1} \int_{Y=0.8}^{X-0.2} dY\,dX
$$

o similar, hay que tener cuidado con los límites, porque para que $Y > X$ y $Y \leq 0.8$ y $Y \geq X+0.2$, necesariamente $X \leq 0.6$.

Por eso, el rango correcto para $X$ es de $0.2$ a $0.6$, y para cada $X$, $Y$ va de $X+0.2$ a $0.8$.

Si extendés $X$ hasta $1$, la integral da cero fuera de $X \leq 0.6$ porque $Y$ no puede ser mayor que $1$ ni menor que $X+0.2$.

---

**Resumen:**  
Tu planteo es correcto si ajustás los límites para que $X \leq 0.6$.  
La forma estándar y más directa es:

$$
\int_{X=0.2}^{0.6} \int_{Y=X+0.2}^{0.8} dY\,dX
$$

que es lo que se usó antes.  
Ambos caminos llevan al mismo resultado si los límites son consistentes con las condiciones del problema.

Vamos a resolver el ejercicio paso a paso:

---

La vara se corta en un punto $X$ con densidad

$$
f_X(x) = \frac{e^{-x}}{1 - e^{-1}} \quad \text{para } 0 \leq x \leq 1
$$

Los dos segmentos resultantes miden $X$ y $1-X$.

Queremos calcular la probabilidad de que el segmento más largo supere en más de tres veces al más corto, es decir:

$$
\max(X, 1-X) > 3 \min(X, 1-X)
$$

Esto ocurre si $X > 3(1-X)$ o $1-X > 3X$.

Resolvamos ambas desigualdades:

1. $X > 3(1-X) \implies X > 3 - 3X \implies 4X > 3 \implies X > \frac{3}{4}$
2. $1-X > 3X \implies 1 > 4X \implies X < \frac{1}{4}$

Entonces, la condición es $X < \frac{1}{4}$ o $X > \frac{3}{4}$.

La probabilidad pedida es:

$$
P\left(X < \frac{1}{4}\right) + P\left(X > \frac{3}{4}\right)
$$

Calculamos cada término usando la función de distribución acumulada:

$$
F_X(x) = \int_0^x \frac{e^{-t}}{1 - e^{-1}} dt = \frac{1 - e^{-x}}{1 - e^{-1}}
$$

Por lo tanto,

- $P\left(X < \frac{1}{4}\right) = F_X\left(\frac{1}{4}\right) = \frac{1 - e^{-1/4}}{1 - e^{-1}}$
- $P\left(X > \frac{3}{4}\right) = 1 - F_X\left(\frac{3}{4}\right) = \frac{e^{-3/4} - e^{-1}}{1 - e^{-1}}$

Sumando ambas probabilidades:

$$
P = \frac{1 - e^{-1/4} + e^{-3/4} - e^{-1}}{1 - e^{-1}}
$$

---

**Respuesta final:**

La probabilidad de que el segmento más largo supere en más de tres veces al más corto es

$$
\frac{1 - e^{-1/4} + e^{-3/4} - e^{-1}}{1 - e^{-1}}
$$

Vamos a resolver el ejercicio paso a paso, explicando cada parte:

---

Sean $S$, $M$ y $J$ las cantidades de Probamons capturados por Steven, Marc y Jake respectivamente.  
$S \sim \text{Poisson}(3)$, $M \sim \text{Poisson}(5)$, $J \sim \text{Poisson}(6)$, independientes.

Queremos hallar:

$$
P(S > M + J \mid S + M + J = 5)
$$

---

**1. Distribución condicional**

Dado que la suma $S + M + J = 5$, el vector $(S, M, J)$ tiene distribución multinomial:

$$
(S, M, J) \mid S + M + J = 5 \sim \text{Multinomial}\left(5; p_1, p_2, p_3\right)
$$

donde

- $p_1 = \frac{3}{3+5+6} = \frac{3}{14}$
- $p_2 = \frac{5}{14}$
- $p_3 = \frac{6}{14}$

---

**2. Probabilidad pedida**

Queremos $P(S > M + J \mid S + M + J = 5)$.

Pero $S + M + J = 5 \implies S + (M + J) = 5$.  
La condición $S > M + J$ implica $S > 5 - S \implies S > 2.5 \implies S \geq 3$ (ya que $S$ es entero).

Para cada valor posible de $S$:

- Si $S = 3$, $M + J = 2$, pero $3 > 2$ sí cumple.
- Si $S = 4$, $M + J = 1$, $4 > 1$ sí cumple.
- Si $S = 5$, $M + J = 0$, $5 > 0$ sí cumple.

Entonces, los casos posibles son $S = 3, 4, 5$.

---

**3. Cálculo de la probabilidad**

La probabilidad es la suma de las probabilidades de los casos favorables:

$$
P = \sum_{k=3}^{5} P(S = k, M + J = 5 - k)
$$

Como es multinomial, la probabilidad de $(S = k, M + J = 5 - k)$ es:

$$
P(S = k) = \binom{5}{k} p_1^k (1 - p_1)^{5 - k}
$$

Pero necesitamos que $M$ y $J$ sumen $5 - k$, y su distribución condicional es multinomial de dos categorías con probabilidades relativas $p_2$ y $p_3$.

Entonces:

$$
P(S = k, M + J = 5 - k) = \binom{5}{k} p_1^k (1 - p_1)^{5 - k}
$$

Pero para cada $k$, la probabilidad de que $M + J = 5 - k$ es absorbida en la fórmula, ya que sólo hay una forma de que $S = k$ y $M + J = 5 - k$.

Pero para ser precisos, la probabilidad total de cada caso es:

$$
P(S = k, M + J = 5 - k) = \binom{5}{k} p_1^k (p_2 + p_3)^{5 - k}
$$

Pero como $p_2 + p_3 = 1 - p_1$, esto es simplemente:

$$
P(S = k) = \binom{5}{k} p_1^k (1 - p_1)^{5 - k}
$$

Así que la probabilidad pedida es:

$$
P = \sum_{k=3}^{5} \binom{5}{k} \left(\frac{3}{14}\right)^k \left(\frac{11}{14}\right)^{5 - k}
$$

---

**4. Cálculo numérico**

Calculamos cada término:

- Para $k = 3$:
  $$
  \binom{5}{3} \left(\frac{3}{14}\right)^3 \left(\frac{11}{14}\right)^2 = 10 \cdot \frac{27}{2744} \cdot \frac{121}{196}
  $$
- Para $k = 4$:
  $$
  \binom{5}{4} \left(\frac{3}{14}\right)^4 \left(\frac{11}{14}\right)^1 = 5 \cdot \frac{81}{38416} \cdot \frac{11}{14}
  $$
- Para $k = 5$:
  $$
  \binom{5}{5} \left(\frac{3}{14}\right)^5 \left(\frac{11}{14}\right)^0 = 1 \cdot \frac{243}{537824}
  $$

Sumando estos valores se obtiene la probabilidad pedida.

---

**Respuesta final:**

La probabilidad de que Steven haya capturado más Probamons que Marc y Jake juntos, dado que entre todos capturaron exactamente 5, es

$$
\sum_{k=3}^{5} \binom{5}{k} \left(\frac{3}{14}\right)^k \left(\frac{11}{14}\right)^{5 - k}
$$

o sea,

$$
P = \binom{5}{3} \left(\frac{3}{14}\right)^3 \left(\frac{11}{14}\right)^2 + \binom{5}{4} \left(\frac{3}{14}\right)^4 \left(\frac{11}{14}\right) + \binom{5}{5} \left(\frac{3}{14}\right)^5
$$

Vamos a resolver el ejercicio paso a paso:

---

Las carretas llegan según un proceso de Poisson de intensidad $\lambda = 3$ por hora.  
El peso de cada carreta es una variable aleatoria independiente de media $2$ toneladas.

Sea $N$ la cantidad de carretas que llegan en una hora, $N \sim \text{Poisson}(3)$.  
Sea $X_i$ el peso de la $i$-ésima carreta, con $E[X_i] = 2$.

El peso total a trasladar en una hora es  
$S = X_1 + X_2 + \cdots + X_N$

Queremos calcular $E[S]$.

---

**Usamos la ley de la esperanza total:**

$$
E[S] = E[E[S \mid N]]
$$

Dado $N = n$, $S$ es la suma de $n$ variables independientes de media $2$, así que  
$E[S \mid N = n] = 2n$

Por lo tanto,

$$
E[S] = E[2N] = 2 E[N] = 2 \times 3 = 6
$$

---

**Respuesta final:**

El peso total esperado que deberá trasladar la balsa en un viaje es $6$ toneladas.

Para calcular el **error cuadrático medio (ECM)** de un estimador de máxima verosimilitud (EMV), seguí estos pasos:

---

1. **Definí el estimador EMV:**  
   Sea $\hat{\theta}$ el EMV para el parámetro $\theta$.

2. **Calculá el sesgo:**

   $$
   \text{Sesgo} = E[\hat{\theta}] - \theta
   $$

3. **Calculá la varianza:**

   $$
   \text{Var}(\hat{\theta}) = E\left[(\hat{\theta} - E[\hat{\theta}])^2\right]
   $$

4. **Sumá ambos términos:**  
   El error cuadrático medio es
   $$
   \text{ECM}(\hat{\theta}) = E\left[(\hat{\theta} - \theta)^2\right] = \text{Var}(\hat{\theta}) + (\text{Sesgo})^2
   $$

---

**En resumen:**  
El ECM del EMV es la suma de la varianza del estimador y el cuadrado de su sesgo respecto al parámetro verdadero.  
Si el EMV es insesgado, el ECM coincide con la varianza.

Vamos a resolver el ejercicio paso a paso:

---

**Datos:**

- $n = 30$ (tamaño de muestra)
- $\bar{x} = 497.735\ \text{kg/m}^3$ (media muestral)
- $s = 6.680\ \text{kg/m}^3$ (desvío muestral)
- $\mu_0 = 500\ \text{kg/m}^3$ (media poblacional según el proveedor)
- Nivel de significación: $\alpha = 0.05$

---

**1. Planteo de hipótesis**

- $H_0: \mu = 500$
- $H_1: \mu \neq 500$

Es un test bilateral.

---

**2. Estadístico de test**

Como la varianza poblacional es desconocida y la muestra es pequeña, usamos el estadístico $t$:

$$
t = \frac{\bar{x} - \mu_0}{s / \sqrt{n}}
$$

---

**3. Cálculo del estadístico**

$$
t = \frac{497.735 - 500}{6.680 / \sqrt{30}}
= \frac{-2.265}{6.680 / 5.477}
= \frac{-2.265}{1.219}
\approx -1.858
$$

---

**4. Región crítica**

Para $\alpha = 0.05$ y $n-1 = 29$ grados de libertad, el valor crítico es $t_{0.025,\,29} \approx 2.045$.

Región de rechazo: $|t| > 2.045$

---

**5. Decisión**

Como $|t| = 1.858 < 2.045$, **no se rechaza $H_0$**.

---

**Conclusión:**  
No es posible refutar la afirmación del proveedor al 5% de significación.

Por supuesto, te muestro la resolución detallada y las combinaciones de cada caso:

---

**Problema:**  
Ocho vendedores ambulantes suben al subte en alguna de las primeras 5 estaciones, eligiendo al azar entre estas. Si en la primera estación subió solo uno, hallar la probabilidad de que al salir de la cuarta estación ya estén todos los vendedores en el subte.

---

**Paso 1: Entendiendo el problema**

- Hay 8 vendedores.
- Uno subió en la estación 1 (ya está fijo).
- Los otros 7 eligen, al azar e independientemente, entre las estaciones 2, 3, 4 y 5.

Queremos la probabilidad de que **todos los vendedores hayan subido antes o en la cuarta estación**, es decir, que ninguno de los 7 suba en la estación 5.

---

**Paso 2: Espacio muestral**

Cada uno de los 7 vendedores puede elegir entre 4 estaciones (2, 3, 4, 5):

- Total de combinaciones posibles: $4^7$

Ejemplo de una combinación:  
(2, 2, 3, 4, 5, 2, 3)  
Esto significa:

- El segundo vendedor sube en la estación 2
- El tercero en la 2
- El cuarto en la 3
- El quinto en la 4
- El sexto en la 5
- El séptimo en la 2
- El octavo en la 3

---

**Paso 3: Casos favorables**

Queremos que **ninguno** suba en la estación 5.  
Entonces, cada uno de los 7 vendedores puede elegir solo entre las estaciones 2, 3 o 4.

- Total de combinaciones favorables: $3^7$

Ejemplo de una combinación favorable:  
(2, 2, 3, 4, 2, 3, 4)  
Aquí, todos suben entre la estación 2 y la 4.

---

**Paso 4: Probabilidad**

La probabilidad pedida es:

$$
P = \frac{3^7}{4^7} = \left(\frac{3}{4}\right)^7
$$

Calculando el valor numérico:

$$
\left(\frac{3}{4}\right)^7 = \frac{2187}{16384} \approx 0.1335
$$

---

**Resumen de combinaciones:**

- **Total de combinaciones posibles:**  
  Todas las formas en que los 7 vendedores pueden elegir entre 4 estaciones:  
  $(2,2,2,2,2,2,2),\ (2,2,2,2,2,2,3),\ \ldots,\ (5,5,5,5,5,5,5)$

- **Combinaciones favorables:**  
  Todas las formas en que los 7 vendedores eligen solo entre 2, 3 y 4:  
  $(2,2,2,2,2,2,2),\ (2,2,2,2,2,2,3),\ \ldots,\ (4,4,4,4,4,4,4)$

---

**Respuesta final:**  
La probabilidad de que al salir de la cuarta estación ya estén todos los vendedores en el subte es

$$
\left(\frac{3}{4}\right)^7 \approx 0.1335
$$

y las combinaciones favorables son todas aquellas donde los 7 vendedores restantes eligen únicamente entre las estaciones 2, 3 y 4.

¡Perfecto! Ahora te resuelvo el ejercicio de Hera vs Viper, mostrando todas las combinaciones posibles de partidas para el caso pedido y explicando cada paso como profesor:

---

**Enunciado:**  
Hera y Viper juegan al mejor de 7 partidas (gana el primero en llegar a 4). La probabilidad de que Hera gane una partida es $0.7$. Sabiendo que Viper ganó la primera partida, ¿cuál es la probabilidad de que la final se haya definido exactamente en 5 partidas?

---

### Paso 1: ¿Cuándo la serie termina en 5 partidas?

Para que la serie termine en 5 partidas, uno de los jugadores debe llegar a 4 victorias recién en la quinta partida.  
Como Viper ganó la primera, las únicas posibilidades son:

- Hera gana 4-1 (Viper solo gana la primera)
- Viper gana 4-1 (Viper gana la primera y 3 de las 4 siguientes, siendo la quinta su cuarta victoria)

---

### Paso 2: Listar todas las combinaciones posibles

#### a) Hera gana 4-1

La única forma es que Hera gane las partidas 2, 3, 4 y 5:

- V H H H H

#### b) Viper gana 4-1

Viper debe ganar la primera y exactamente 2 de las partidas 2, 3, 4, y la quinta partida también debe ser de Viper (para que sea su cuarta victoria).

Veamos las combinaciones para partidas 2, 3, 4 (llamémoslas X, Y, Z), donde Viper gana exactamente 2 y Hera 1:

- V V V H V (Viper gana 2 y 3, Hera gana 4, Viper gana 5)
- V V H V V (Viper gana 2 y 4, Hera gana 3, Viper gana 5)
- V H V V V (Viper gana 3 y 4, Hera gana 2, Viper gana 5)

En resumen, las combinaciones posibles de 5 partidas, sabiendo que la primera es de Viper y la serie termina en 5, son:

- V H H H H
- V V V H V
- V V H V V
- V H V V V

---

### Paso 3: Calcular la probabilidad de cada combinación

- Para V H H H H:  
  $P = 0.3 \times 0.7 \times 0.7 \times 0.7 \times 0.7$

- Para cada de las otras tres (por ejemplo, V V V H V):  
  $P = 0.3 \times 0.3 \times 0.3 \times 0.7 \times 0.3$  
  (hay 3 combinaciones así)

---

### Paso 4: Probabilidad total de terminar en 5 partidas

Sumamos todas las probabilidades:

$
P = 0.3 \times 0.7^4 + 3 \times (0.3^4 \times 0.7)
$

Calculamos:

- $0.7^4 = 0.2401$
- $0.3^4 = 0.0081$

Entonces:

- $0.3 \times 0.2401 = 0.07203$
- $3 \times 0.0081 \times 0.7 = 3 \times 0.00567 = 0.01701$

$
P = 0.07203 + 0.01701 = 0.08904
$

---

### Respuesta final

La probabilidad de que la final se haya definido exactamente en 5 partidas, sabiendo que Viper ganó la primera y que la probabilidad de que gane una partida Hera es $0.7$, es

$$
P = 0.3 \times 0.7^4 + 3 \times (0.3^4 \times 0.7) \approx 0.089
$$

Las combinaciones posibles de partidas son:

- V H H H H
- V V V H V
- V V H V V
- V H V V V

donde V es victoria de Viper y H de Hera.

¡Por supuesto! Te explico cómo resolver el problema paso a paso, como profesor de probabilidad y estadística, usando solo fórmulas entre signos de dólar para que se rendericen en KaTeX:

---

**Problema:**  
Hera y Viper juegan al mejor de 7 partidas (gana el primero en llegar a 4). La probabilidad de que Hera gane una partida es $0.7$. Sabiendo que Viper ganó la primera partida, ¿cuál es la probabilidad de que la final se haya definido exactamente en 5 partidas?

---

**Paso 1: Identificar el evento condicional**

Queremos calcular  
$P(\text{la serie termina en 5 partidas} \mid \text{Viper gana la primera})$

Por la fórmula de probabilidad condicional:

$$
P(A \mid B) = \frac{P(A \cap B)}{P(B)}
$$

Aquí,  
$A$: "la serie termina en 5 partidas"  
$B$: "Viper gana la primera"

---

**Paso 2: Calcular $P(A \cap B)$**

Esto es la probabilidad de que la serie termine en 5 partidas y la primera la gane Viper.

Como vimos antes, las combinaciones posibles son:

- V H H H H
- V V V H V
- V V H V V
- V H V V V

Donde V es victoria de Viper y H de Hera.

La probabilidad de cada combinación es:

- Para V H H H H: $0.3 \times 0.7^4$
- Para cada una de las otras tres: $0.3 \times 0.3^3 \times 0.7$

Sumando:

$$
P(A \cap B) = 0.3 \times 0.7^4 + 3 \times (0.3^4 \times 0.7)
$$

---

**Paso 3: Calcular $P(B)$**

La probabilidad de que Viper gane la primera partida es simplemente $0.3$.

---

**Paso 4: Probabilidad condicional**

Entonces,

$$
P(\text{la serie termina en 5 partidas} \mid \text{Viper gana la primera}) = \frac{0.3 \times 0.7^4 + 3 \times (0.3^4 \times 0.7)}{0.3}
$$

Calculando los valores numéricos:

- $0.7^4 = 0.2401$
- $0.3^4 = 0.0081$
- $0.3 \times 0.2401 = 0.07203$
- $3 \times 0.0081 \times 0.7 = 0.01701$
- $0.07203 + 0.01701 = 0.08904$
- $0.08904 / 0.3 \approx 0.297$

---

**Respuesta final:**

La probabilidad de que la final se haya definido exactamente en 5 partidas, sabiendo que Viper ganó la primera, es

$$
\frac{0.3 \times 0.7^4 + 3 \times (0.3^4 \times 0.7)}{0.3} \approx 0.297
$$

Es decir, aproximadamente $29.7\%$.

Te ayudo a entender qué tienes que calcular en este problema, actuando como tu profesor de probabilidad y estadística:

---

## Análisis del Problema

**Situación planteada:**

- Un cargador entrega una cantidad aleatoria de energía $X$ (en mAh)
- $X$ tiene función de densidad: $f_X(x) = \frac{2(10-x)}{100} \cdot 1_{\{0<x<10\}}$
- La batería tiene capacidad máxima de 6 mAh
- **Todo exceso se disipa como calor**

---

## ¿Qué es la "energía desperdiciada"?

La energía desperdiciada es la cantidad que se pierde cuando el cargador entrega más de lo que la batería puede almacenar.

Si definimos $Y$ = energía desperdiciada, entonces:

$$
Y = \begin{cases}
0 & \text{si } X \leq 6 \text{ (no hay desperdicio)} \\
X - 6 & \text{si } X > 6 \text{ (el exceso se desperdicia)}
\end{cases}
$$

O más compactamente: $Y = \max(0, X - 6)$

---

## ¿Qué tienes que calcular?

Necesitas encontrar la **función de distribución** de $Y$, es decir:

$$F_Y(y) = P(Y \leq y)$$

para todos los valores posibles de $y$.

---

## Pasos que debes seguir:

### 1. Determinar el rango de $Y$

- ¿Cuál es el valor mínimo de $Y$?
- ¿Cuál es el valor máximo de $Y$?

### 2. Calcular $F_Y(y)$ por casos

Tendrás que considerar diferentes intervalos de $y$ y para cada uno calcular $P(Y \leq y)$.

### 3. Para cada caso, traducir el evento en términos de $X$

Por ejemplo: $P(Y \leq y) = P(\max(0, X-6) \leq y)$

### 4. Usar la distribución conocida de $X$

Convertir las probabilidades en términos de $X$ y usar $f_X(x)$ para calcular.

### 5. Graficar $F_Y(y)$

La función de distribución debe ser continua, creciente, y ir de 0 a 1.

---

## En resumen:

Debes encontrar cómo se distribuye la cantidad de energía que se desperdicia, considerando que solo hay desperdicio cuando $X > 6$.

¿Te queda claro el enfoque? ¿Quieres que procedamos con la resolución paso a paso?

Te resuelvo este ejercicio paso a paso, actuando como tu profesor de probabilidad y estadística:

---

## Ejercicio 5: Prueba de hipótesis para la desviación estándar

**Enunciado:**
Se toman 6 muestras de una sustancia contaminante y se les mide el pH, obteniéndose una media muestral de 7.85 y una desviación estándar muestral de 0.15. Suponiendo que la muestra fue tomada de una población normal, ¿se puede concluir que el desvío estándar del pH es menor a 0.18 con significación 0.05?

---

### Paso 1: Planteo de hipótesis

Este es un test de hipótesis para la varianza (o desviación estándar) poblacional.

**Hipótesis:**

- $H_0: \sigma \geq 0.18$ (la desviación estándar es mayor o igual a 0.18)
- $H_1: \sigma < 0.18$ (la desviación estándar es menor a 0.18)

**Nivel de significación:** $\alpha = 0.05$

---

### Paso 2: Estadístico de prueba

Para probar hipótesis sobre la varianza cuando la población es normal, usamos el estadístico chi-cuadrado:

$$\chi^2 = \frac{(n-1)s^2}{\sigma_0^2}$$

Donde:

- $n = 6$ (tamaño de muestra)
- $s = 0.15$ (desviación estándar muestral)
- $\sigma_0 = 0.18$ (valor bajo $H_0$)

---

### Paso 3: Cálculo del estadístico

$$\chi^2 = \frac{(6-1)(0.15)^2}{(0.18)^2} = \frac{5 \times 0.0225}{0.0324} = \frac{0.1125}{0.0324} = 3.472$$

---

### Paso 4: Región crítica

Como es un test de cola izquierda ($H_1: \sigma < 0.18$), rechazamos $H_0$ si:

$$\chi^2 < \chi^2_{(1-\alpha, n-1)} = \chi^2_{(0.95, 5)}$$

Buscando en tabla: $\chi^2_{(0.95, 5)} = 1.145$

**Región crítica:** $\chi^2 < 1.145$

---

### Paso 5: Decisión

Nuestro estadístico calculado es $\chi^2 = 3.472$

Como $3.472 > 1.145$, **NO rechazamos** $H_0$.

---

### Paso 6: Conclusión

**Con un nivel de significación del 5%, NO hay evidencia suficiente para concluir que la desviación estándar del pH es menor a 0.18.**

En otras palabras, los datos no proporcionan evidencia estadísticamente significativa de que $\sigma < 0.18$.

---

### Interpretación práctica

El valor muestral de $s = 0.15$ es menor que $0.18$, pero esta diferencia podría deberse simplemente a la variabilidad muestral. El tamaño de muestra pequeño ($n = 6$) hace que sea difícil detectar diferencias pequeñas en la varianza poblacional.

Te explico la regla de decisión de manera más clara, actuando como tu profesor de probabilidad y estadística:

---

## Regla de Decisión - Explicación Detallada

### ¿Qué es la regla de decisión?

La regla de decisión nos dice **cuándo rechazar** la hipótesis nula $H_0$ basándose en el valor del estadístico de prueba.

---

### En nuestro problema:

**Hipótesis:**

- $H_0: \sigma \geq 0.18$
- $H_1: \sigma < 0.18$ (cola izquierda)

**Estadístico de prueba:** $\chi^2 = 3.472$

---

### ¿Por qué es cola izquierda?

Porque queremos probar si $\sigma < 0.18$.

Si la desviación estándar poblacional fuera realmente menor que 0.18, entonces esperaríamos que nuestro estadístico $\chi^2$ sea **pequeño** (valores bajos).

---

### La regla de decisión es:

$$\text{Rechazar } H_0 \text{ si } \chi^2 < \chi^2_{0.95, 5} = 1.145$$

**¿Qué significa esto?**

- Si nuestro estadístico calculado es **menor** que 1.145, entonces rechazamos $H_0$
- Si nuestro estadístico calculado es **mayor o igual** que 1.145, entonces NO rechazamos $H_0$

---

### En nuestro caso:

- Estadístico calculado: $\chi^2 = 3.472$
- Valor crítico: $\chi^2_{0.95, 5} = 1.145$
- Como $3.472 > 1.145$, **NO rechazamos** $H_0$

---

### Interpretación intuitiva:

Un valor de $\chi^2 = 3.472$ es **demasiado grande** para ser consistente con la hipótesis de que $\sigma < 0.18$.

Si realmente $\sigma < 0.18$, esperaríamos un valor de chi-cuadrado mucho más pequeño (menor que 1.145).

---

### Resumen de la regla:

**Regla:** Rechazar $H_0$ si $\chi^2 < 1.145$

**Decisión:** Como $\chi^2 = 3.472 \not< 1.145$, NO rechazamos $H_0$

**Conclusión:** No hay evidencia suficiente para afirmar que $\sigma < 0.18$

¿Te queda más claro ahora?
