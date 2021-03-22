1.Gradient Descent
The beta distribution is parameterized in terms of two positive parameters, alpha, beta:
$$
p_\theta(x)={1 \over B(\alpha, \beta)} x^{\alpha - 1}(1-x)^{\beta -1}, \\
where \ \theta=(\alpha, \beta) and  \ \text{B is normalization constant}.
$$

(a) Write the log-likelihood of N i.i.d samples from Beta distribution.
Likelihood of N i.i.d samples from Beta distribution is written as follow:
$$
L(\theta)=\prod_{i=1}^N p_\theta(x_i).
$$
Log likelihood is a log of likelihood:
$$
l(\theta)=log(L(\theta))=log(\prod_{i=1}^N p_\theta(x_i))=\sum_{i=1}^N log(p_\theta(x_i)) \\
= \sum_{i=1}^N log({1 \over B(\alpha, \beta)} x_i^{\alpha -1}(1-x_i)^{\beta -1}) \\
= log({1 \over B(\alpha, \beta)} x_1^{\alpha -1}(1-x_1)^{\beta -1}) + \\
log({1 \over B(\alpha, \beta)} x_2^{\alpha -1}(1-x_2)^{\beta -1}) + \\
\vdots \\
log({1 \over B(\alpha, \beta)} x_N^{\alpha -1}(1-x_N)^{\beta -1}) \\
= -Nlog({B(\alpha, \beta)})+ \sum_{i=1}^N {log(x_i^{\alpha-1})} + \sum_{i=1}^N {log(1-x_i)^{\beta-1}} \\
= -Nlog({B(\alpha, \beta)})+ (\alpha-1)\sum_{i=1}^N {log x_i} + (\beta-1)\sum_{i=1}^N {log(1-x_i)}
$$
(b) Derive the partial derivative of log likelihood with regards to alpha.
$$
{\partial l(\theta) \over \partial \alpha}={-N \over B(\alpha, \beta)}B(\alpha, \beta)(\psi(\alpha)-\psi(\alpha + \beta))+\sum_{i=1}^N {log x_i} \\
=-N (\psi(\alpha)-\psi(\alpha + \beta))+\sum_{i=1}^N {log x_i}
$$
(c) Derive the partial derivative of log likelihood with regards to beta.
$$
{\partial l(\theta) \over \partial \beta}={-N \over B(\alpha, \beta)}B(\alpha, \beta)(\psi(\beta)-\psi(\alpha + \beta))+\sum_{i=1}^N {log (1-x_i)} \\
=-N (\psi(\beta)-\psi(\alpha + \beta))+\sum_{i=1}^N {log (1-x_i)}
$$
(d) Implement a gradient descent procedure for maximizing the likelihood. Submit the source code.
참고: https://www.youtube.com/watch?v=tUXfxaB3EHs
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU5NTM2NjUxMSwtODM0OTM4NjkyLC0yMD
A4NDQxMDQ0LDE0ODM5NTA0OTUsLTE4MjMxNzQ1MDZdfQ==
-->