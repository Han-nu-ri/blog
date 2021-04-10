$$
log(g_\theta (x))=log(\int g_{\theta}(x|z)p(z)dz))
$$

$$
log(g_\theta (x))=log(\int g_{\theta}(x|z)p(z)dz)) = log(\int g_{\theta}(x|z){p(z) \over q_{\phi}(z|x)} q_{\phi}(z|x) dz)) \\
\ge \int log(g_{\theta}(x|z){p(z) \over q_{\phi}(z|x)})*q_{\phi}(z|x) dz \\
\ge \int (log(g_{\theta}(x|z))log({p(z) \over q_{\phi}(z|x)})*q_{\phi}(z|x) dz \\
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUzMTIwNjgzOSw4NjA2OTA3MDIsLTk2MT
A1MzQzNV19
-->