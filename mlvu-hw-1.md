1.Gradient Descent
The beta distribution is parameterized in terms of two positive parameters, alpha, beta:
$$
p_\theta(x)={1 \over B(\alpha, \beta)} x^{\alpha - 1}(1-x)^{\beta -1}, \\
where \ \theta=(\alpha, \beta) and  \ \text{B is normalization constant}.
$$

(a) Write the log-likelihood of N i.i.d samples from Beta distribution.
Likelihood of N i.i.d samples from Beta distribution is
$$
L(\theta)=\prod_{i=1}^N p_\theta(x_i)
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkyMzExODg4NV19
-->