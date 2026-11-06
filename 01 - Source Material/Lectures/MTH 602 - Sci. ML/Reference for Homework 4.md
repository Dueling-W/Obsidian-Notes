## MLE for $\boldsymbol{\mu}_1$ (two-class Gaussian, shared $\Sigma$)

**Setup**
- $t_n \in \{0,1\}$: $t_n = 1$ if $\mathbf{x}_n \in \mathcal{C}_1$, $t_n = 0$ if $\mathbf{x}_n \in \mathcal{C}_2$
- $\Sigma$ is shared and symmetric, so $\Sigma^{-1}$ is symmetric
- Only the following log-likelihood term depends on $\boldsymbol{\mu}_1$:

$$
-\frac{1}{2}\sum_{n=1}^{N} t_n\,(\mathbf{x}_n-\boldsymbol{\mu}_1)^\top \Sigma^{-1}(\mathbf{x}_n-\boldsymbol{\mu}_1)
$$

**Step 1: Expand the quadratic form** (keep $\Sigma^{-1}$ in the middle)

$$
(\mathbf{x}_n-\boldsymbol{\mu}_1)^\top \Sigma^{-1}(\mathbf{x}_n-\boldsymbol{\mu}_1)
= \mathbf{x}_n^\top\Sigma^{-1}\mathbf{x}_n - 2\,\boldsymbol{\mu}_1^\top\Sigma^{-1}\mathbf{x}_n + \boldsymbol{\mu}_1^\top\Sigma^{-1}\boldsymbol{\mu}_1
$$

- The two cross terms combine because each is a scalar and $\Sigma^{-1}$ is symmetric

**Step 2: Differentiate with respect to $\boldsymbol{\mu}_1$**
- $\frac{\partial}{\partial \boldsymbol{\mu}}\left(\boldsymbol{\mu}^\top A\mathbf{x}\right) = A\mathbf{x}$
- $\frac{\partial}{\partial \boldsymbol{\mu}}\left(\boldsymbol{\mu}^\top A\boldsymbol{\mu}\right) = 2A\boldsymbol{\mu}$ for symmetric $A$
- $\mathbf{x}_n^\top\Sigma^{-1}\mathbf{x}_n$ does not depend on $\boldsymbol{\mu}_1$, so its derivative is $0$

$$
\frac{\partial}{\partial \boldsymbol{\mu}_1}\Big[\cdots\Big] = -2\,\Sigma^{-1}\mathbf{x}_n + 2\,\Sigma^{-1}\boldsymbol{\mu}_1 = 2\,\Sigma^{-1}(\boldsymbol{\mu}_1-\mathbf{x}_n)
$$

- Shortcut: $\frac{\partial}{\partial \boldsymbol{\mu}}(\mathbf{x}-\boldsymbol{\mu})^\top A(\mathbf{x}-\boldsymbol{\mu}) = -2A(\mathbf{x}-\boldsymbol{\mu})$ for symmetric $A$

**Step 3: Set the full gradient to zero**

$$
-\frac{1}{2}\sum_{n=1}^{N} t_n\, 2\,\Sigma^{-1}(\boldsymbol{\mu}_1-\mathbf{x}_n)
= \Sigma^{-1}\sum_{n=1}^{N} t_n(\mathbf{x}_n-\boldsymbol{\mu}_1) = \mathbf{0}
$$

- $\Sigma^{-1}$ does not depend on $n$, so it factors out of the sum

**Step 4: Left-multiply by $\Sigma$** (no "dividing" by a matrix)

$$
\sum_{n=1}^{N} t_n\mathbf{x}_n = \sum_{n=1}^{N} t_n\boldsymbol{\mu}_1 = \boldsymbol{\mu}_1\sum_{n=1}^{N} t_n
$$

- $\boldsymbol{\mu}_1$ does not depend on $n$, so it factors out of the sum

**Step 5: Identify $N_1$**
- $N_1 = \sum_{n=1}^{N} t_n$ counts the points in $\mathcal{C}_1$, since each $t_n$ is $1$ or $0$

$$
\boxed{\boldsymbol{\mu}_1 = \frac{1}{N_1}\sum_{n=1}^{N} t_n\,\mathbf{x}_n}
$$

**Interpretation**
- $\boldsymbol{\mu}_1$ is the sample mean of the inputs assigned to class $\mathcal{C}_1$

**Ref:** Bishop PRML §4.2.2