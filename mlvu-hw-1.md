**1.Gradient Descent**
**(a) Write the log-likelihood of N i.i.d samples from Beta distribution.**
The beta distribution is parameterized in terms of two positive parameters, alpha, beta:
$$
p_\theta(x)={1 \over B(\alpha, \beta)} x^{\alpha - 1}(1-x)^{\beta -1}, \\
where \ \theta=(\alpha, \beta) and  \ \text{B is normalization constant}.
$$

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
**(b) Derive the partial derivative of log likelihood with regards to alpha.**
$$
{\partial l(\theta) \over \partial \alpha}={-N \over B(\alpha, \beta)}B(\alpha, \beta)(\psi(\alpha)-\psi(\alpha + \beta))+\sum_{i=1}^N {log x_i} \\
=-N (\psi(\alpha)-\psi(\alpha + \beta))+\sum_{i=1}^N {log x_i}
$$
**\(c\) Derive the partial derivative of log likelihood with regards to beta.**
$$
{\partial l(\theta) \over \partial \beta}={-N \over B(\alpha, \beta)}B(\alpha, \beta)(\psi(\beta)-\psi(\alpha + \beta))+\sum_{i=1}^N {log (1-x_i)} \\
=-N (\psi(\beta)-\psi(\alpha + \beta))+\sum_{i=1}^N {log (1-x_i)}
$$
**(d) Implement a gradient descent procedure for maximizing the likelihood. Submit the source code.**
Function explanation
1\) calculate_log_likelihood_of_beta_distribution(alpha, beta, samples)
Calculate log likelihood of beta distribution with alpha, beta and samples.
$$
-Nlog({B(\alpha, \beta)})+ (\alpha-1)\sum_{i=1}^N {log x_i} + (\beta-1)\sum_{i=1}^N {log(1-x_i)}
$$
2\) generate_samples_from_beta_distribution(initial_alpha, initial_beta, sample_count)
Extracts beta distribution samples as much as sample count with alpha and beta.
3\) update_parameters_in_beta_distribution_using_gradient_descent(alpha, beta, samples)
Update gradients in the direction of maximizing log likelihood with alpha, beta and samples.
$$
{\partial l(\theta) \over \partial \alpha}
=-N (\psi(\alpha)-\psi(\alpha + \beta))+\sum_{i=1}^N {log x_i} \\
{\partial l(\theta) \over \partial \beta} =-N (\psi(\beta)-\psi(\alpha + \beta))+\sum_{i=1}^N {log (1-x_i)}
$$

![image](https://user-images.githubusercontent.com/11609881/112924128-8c287080-914a-11eb-9e7d-809ecfd64e11.png)

**(e) Generate 500 samples from a Beta distribution with parameters α = 2, β = 3, and estimate α and β using your gradient descent implementation in (d). Repeat this experiment 100 times and include histograms of the resulting estimates for the two parameters (two histograms total, each based on 100
estimates) in report. Submit the source code including (d) and (e) named h1.gd.py.**
Histograms:
![image](https://user-images.githubusercontent.com/11609881/112926304-38b82180-914e-11eb-84e9-37daf0f40185.png)
Source code:
![image](https://user-images.githubusercontent.com/11609881/112924160-96e30580-914a-11eb-9a6c-c4cd0f24f420.png)

**2. K-nearest Neighbor Classifiers**
**(a) Implement the train(self, X, y) method.**
![image](https://user-images.githubusercontent.com/11609881/112926923-1a065a80-914f-11eb-97f9-2f48ea779756.png)
**(b) Implement the inference(self, X, k) method. Specifically, predict a label for each test example in X using k nearest neighbors based on Euclidean (L2) distance.** 

**\(c\) Experiment with multiple values for k and report what you observe.**

**(d) Repeat (b) and \(c\) with the dot-product similarity when you compute the k nearest neighbors, and compare the result with the L2 distance.**
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MjM2MzYxMTAsLTE2MzUyMTA3NjQsLT
c3OTQ5MzI5OSwtNDY1ODE4Mzk0LDE1OTUzNjY1MTEsLTgzNDkz
ODY5MiwtMjAwODQ0MTA0NCwxNDgzOTUwNDk1LC0xODIzMTc0NT
A2XX0=
-->