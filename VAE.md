$$
log(g_\theta (x))=log(\int g_{\theta}(x|z)p(z)dz))
$$

$$
log(g_\theta (x))=log(\int g_{\theta}(x|z)p(z)dz)) = log(\int g_{\theta}(x|z){p(z) \over q_{\phi}(z|x)} q_{\phi}(z|x) dz)) \\
\ge \int log(g_{\theta}(x|z){p(z) \over q_{\phi}(z|x)})*q_{\phi}(z|x) dz \\
\ge \int (log(g_{\theta}(x|z))-log({q_{\phi}(z|x) \over p(z)}))*q_{\phi}(z|x) dz \\
\ge \int log(g_\theta(x|z))q_\phi(z|x)dz-\int log({q_{\phi}(z|x) \over p(z)})q_\phi(z|x)dz
$$
Reconstruction Error
$$
\int log(g_\theta(x|z))q_\phi(z|x)dz \approx {1 \over L}\sum_{l} log(g_\theta(x|z^{l})) \approx log(g_\theta(x|z))
$$
g(x|z) ~ Bernoulli
$$
log(g_\theta(x|z)) \\
= \sum_{j=1}^D log(g_\theta(x_j|z)) \\
= \sum_{j=1}^D log(p_j^{x_j}(1-p_j)^{1-x_j}) \\
= \sum_{j=1}^D x_jlog(p_j) + (1-x_j)log(1-p_j) \\
$$

g(x|z) ~ Gauissan(mu, 1)
$$
log(g_\theta(x|z)) \\
= \sum_{j=1}^D log(g_\theta(x_j|z)) \\
= \sum_{j=1}^D log({1 \over \sqrt{2\pi}}exp(-{(x_j-\mu_j)^2 \over 2})) \\
\propto \sum_{j=1}^D (x_j - \mu_j)^2
$$

KL Divergence
$$
\int log({q_{\phi}(z|x) \over p(z)})q_\phi(z|x)dz = D_{KL}(q_{\phi}(z|x) || p(z))
$$
When prior and posterior are multinormal distributions,
$$
D_{KL}(q_{\phi}(z|x)||p(z))
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzOTM0MTg1MCwxOTY5MzE5NjEwLDM5Nj
A0ODUwNywtNTg3NDk3OTI2LC0xNzg1OTE0LC0xNjA1MDY3NjI0
LDg2MDY5MDcwMiwtOTYxMDUzNDM1XX0=
-->