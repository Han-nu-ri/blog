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
![image](https://user-images.githubusercontent.com/11609881/112927021-4b7f2600-914f-11eb-90e7-3d8dc1a6759f.png)
**(b) Implement the inference(self, X, k) method. Specifically, predict a label for each test example in X using k nearest neighbors based on Euclidean (L2) distance.** 
![image](https://user-images.githubusercontent.com/11609881/112927069-605bb980-914f-11eb-9e8b-a104ae0b6dd1.png)
**\(c\) Experiment with multiple values for k and report what you observe.**

![image](https://user-images.githubusercontent.com/11609881/112928249-3acfaf80-9151-11eb-8c75-1b5e86c73ce5.png)
![image](https://user-images.githubusercontent.com/11609881/112928294-5044d980-9151-11eb-921a-830454d10b95.png)
I measured the accuracy by increasing k from 1 to 20. As a result, it was confirmed that when k is 3, the accuracy is the highest at 89.50%.
**(d) Repeat (b) and \(c\) with the dot-product similarity when you compute the k nearest neighbors, and compare the result with the L2 distance.**
![image](https://user-images.githubusercontent.com/11609881/112930951-2f32b780-9156-11eb-89b0-942ec69adeb5.png)
![image](https://user-images.githubusercontent.com/11609881/112931183-99e3f300-9156-11eb-9c8c-81359bb73609.png)
![image](https://user-images.githubusercontent.com/11609881/112931048-57221b00-9156-11eb-9036-e6f0669cf027.png)
I measured the accuracy by increasing k from 1 to 20. As a result, it was confirmed that when k is 1, the accuracy is the highest at 93.50%.
**3. Two-layer Neural Networks**
**(a) Implement the init (self, ...) method. This function needs to do two things: 1) initializing model parameters, and 2) storing hyperparameters. You may add additional arguments of this method.**
![image](https://user-images.githubusercontent.com/11609881/112932280-981b2f00-9158-11eb-9561-404d5bdcaf22.png)
**(b) Implement the feed forward(self, X) method, which performs the forward pass and output a dictionary containing all intermediate outputs that are necessary for backpropagation.**
![image](https://user-images.githubusercontent.com/11609881/112932400-ca2c9100-9158-11eb-8417-6556c216ca67.png)
**\(c\) Implement the back propagate(self, X, Y, ff dict) method, which performs the backpropagation steps and output a dictionary of gradients for all model parameters. Here, ff dict is the output from the forward step.**
![image](https://user-images.githubusercontent.com/11609881/112932734-6b1b4c00-9159-11eb-921d-2b536866377a.png)
**(d) Implement the train(self, X, Y) method, which performs forward pass, backpropagation, and gradient descent with mini-batches.**
![image](https://user-images.githubusercontent.com/11609881/112932801-8be3a180-9159-11eb-8547-5e3f519fa15f.png)
**(e) Implement the evaluate(self, X, Y) method, which takes a test set and returns the classification accuracy.**
![image](https://user-images.githubusercontent.com/11609881/112932876-ab7aca00-9159-11eb-8d34-193318f5c22c.png)
**(f) Set aside some training examples as validation set, and tune the hyperparameters (e.g., learning rate, hidden dimensions, number of epochs, batch size) to optimize the validation accuracy. Report the best combination of hyperparameters you found, along with your final test accuracy.**

**(g) (Bonus) Change the activation function to ReLU (or other ones we learned in the class), and repeat (f). Compare the final performance and training speed against softmax.**
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjEyODQ4OTI3NCwxODYwODg1MDUwLC00OD
Y4ODA4NDQsMTcwMzg0ODYzMiw4MjIzOTY3NzIsLTE4NDc3OTYy
NCwtMTU5OTMyODkwMSw1OTI1ODI0OTAsLTExMDg4NDQzNDgsLT
E2MzUyMTA3NjQsLTc3OTQ5MzI5OSwtNDY1ODE4Mzk0LDE1OTUz
NjY1MTEsLTgzNDkzODY5MiwtMjAwODQ0MTA0NCwxNDgzOTUwND
k1LC0xODIzMTc0NTA2XX0=
-->