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
= \sum_{j=1}^D log({1 \over \sqrt{2\pi}}exp(-{(x_j-\mu})) \\
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1OTY3NTM1MiwtNTg3NDk3OTI2LC0xNz
g1OTE0LC0xNjA1MDY3NjI0LDg2MDY5MDcwMiwtOTYxMDUzNDM1
XX0=
-->