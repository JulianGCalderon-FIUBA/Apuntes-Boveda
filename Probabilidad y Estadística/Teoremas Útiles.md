## Teorema de Combinación Lineal

Sean $X_1, \cdots, X_n$ variables aleatorias independientes con $X_i \sim \mathcal N(\mu_i, \sigma_i^2)$, y sea $Y = \sum_{i = 1}^n a_i X_i$, entonces $Y$ tendrá distribución normal de parámetros:

$$
\mu_ = \sum_{i=1}^n a_i\mu_i
$$

$$
\sigma^2 = \sum_{i=1}^n a_i^2 \sigma_i^2
$$

Es decir, pensamos $Y$ como combinación lineal de distribuciones normales independientes

## Ley de los Grandes Límites

Se dice que si se tiene una sucesión de variables aleatorias independientes $(X_n)_{n \geq 1}$con $E[X_i] = \mu < \infty$, y $\text{var}[x_i] = \sigma^2 < \infty$, entonces $\overline X_n = \frac{1}{n}\sum_{i = 1}^n X_i$, entonces este promedio tiende a $\mu$

### Ley Débil de los Grandes Números (Markov)

$$
P( |\overline X_n - \mu | > \varepsilon) \to 0
$$

La probabilidad de que la aproximación se aleje de $\mu$ tiende a $0$ a mayor $n$

$$
E(\overline X_n) = \mu
$$

$$
\text{Var}(\overline X_n) = \sigma^2 / n
$$
