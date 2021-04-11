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
log(g_\theta(x|z))
$$

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU4NzQ5NzkyNiwtMTc4NTkxNCwtMTYwNT
A2NzYyNCw4NjA2OTA3MDIsLTk2MTA1MzQzNV19
-->