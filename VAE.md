$$
log(g_\theta (x))=log(\int g_{\theta}(x|z)p(z)dz))
$$

$$
log(g_\theta (x))=log(\int g_{\theta}(x|z)p(z)dz)) = log(\int g_{\theta}(x|z){p(z) \over q_{\phi}(z|x)} q_{\phi}(z|x) dz)) \\
\ge \int log(g_{\theta}(x|z){p(z) \over q_{\phi}(z|x)})*q_{\phi}(z|x) dz \\
\ge \int (log(g_{\theta}(x|z))-log({q_{\phi}(z|x) \over p(z)}))*q_{\phi}(z|x) dz \\
\ge \int log(g_\theta(x|z))q_\phi(z|x)dz-\int log({q_{\phi}(z|x) \over p(z)})q_\phi(z|x)dz
$$

$$
\int log(g_\theta(x|z))q_\phi(z|x)dz \approx {1 \over L}\sum_{i, l} log(g_\theta(x_{i}|z^{i, l})) \approx {1 \over L}\sum_{i} log(g_\theta(x_{i}|z^{i}))
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTcwOTc2MDcyMSwtMTYwNTA2NzYyNCw4Nj
A2OTA3MDIsLTk2MTA1MzQzNV19
-->