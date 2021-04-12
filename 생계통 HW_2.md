1. (a)
$$
g(Q, x)={K\lambda \over Q} + {hQ(1-x)^2 \over 2} + \lambda x p +\lambda(1-x)c
$$
(b)
g
$$
{\partial g(Q, x) \over \partial x}=hQx-hQ+\lambda(p-c)=0 \\
hQ(1-x)=\lambda(p-c)
$$
$$
{\partial g(Q, x) \over \partial Q}=h(1-x)^2Q^2-2K\lambda=0
$$
2. (a) arc(t, s)는 수요를 충족 시키는 경우와 재고가 특정 시점에 사라져서 충족 시키지 못하는 경우를 고려해야 합니다. 따라서 arc(t, s)는 다음과 같이 표현할 수 있습니다:
$$
K+h\sum_{i=t}^{s-1}(1-q)^{i-t}d_i+\sum_{i=t}^{s-1}qd_i\sum_{j=0}^{i-t-1}(1-q)^j(p+jh)
$$
초기 주문 계획이 셋업 되면 변경하지 않으므로, Wagner-Within problem에서 DP algorithm을 활용한 것과 마지막 period부터 backtracking하며 최적의 비용을 구할 수 있습니다.
$$
\theta_t=min_{t \lt s \le T+1}(K+h\sum_{i=t}^{s-1}(1-q)^{i-t}d_i+\sum_{i=t}^{s-1}\sum_{j=0}^{i-t-1}(1-q)^jqd_i(p+jh)+\theta_s)
$$
(b) Wagner-Whitin algorithm과 (a)의 식을 활용하여, 다음과 같이 풀 수 있습니다:
$$
\theta_5 = 0 \\
\theta_4 = K+\theta_5 =200 [s(4)=5]\\
\theta_3=min\{K+\theta_4, K+h(1-q)d_4+pqd_4+\theta_5\} \\
= min\{400, 200+0.2(0.75)175+3(0.25)175\} \\
= min\{400, 357.5\}
= 357.5 [s(3)=5]\\
\theta_2=min\{K+\theta_3, K+h(1-q)d_3+pqd_3+\theta_4, \\
K+h(1-q)d_3+pqd_3+h(1-q)^2d_4+(1-q)qd_4(p+h)+pqd_4+\theta_5\} \\
= min\{557.5, 625, 680.9375\} \\
= 557.5 [s(2)=3] \\
\theta_1 = min\{K+\theta_2, \\
K+h(1-q)d_2+pqd_2+\theta_3,\\
K+h(1-q)d_2+pqd_2+h(1-q)^2d_3+(1-q)qd_3(p+h)+pqd_3+\theta_4,\\
K+h(1-q)d_2+pqd_2+h(1-q)^2d_3+(1-q)qd_3(p+h)+pqd_3+\\
h(1-q)^3d_4+qd_4((1-q)^2(p+2h)+(1-q)(p+h)+p)+\theta_5\} \\
= min\{757.5, 670,  878.125, 1012.813\} = 670 [s(1)=3]\\
$$
따라서 optimal solution은 s(1)=3, s(3)=5로 period 1에 325(d1+d2), period 3(d3+d4)에 425를 주문하는 것 입니다. 또한 total cost은 670이 됩니다.
(c\) 위에서 같이 optimal solution은 각 period의 수요와 모델의 파라미터에 따라 달라지게 됩니다. 다만 일반적으로, 미래의 수요에 대한 주문을 많이 할수록 위험이 큽니다. 해당 수요가 실현되기 직전까지 보유하다가 사라지게 될 수 있기 때문입니다. 따라서 Wagner-Whitin with perishability problem의 optimal solution은 without perishability의 것보다  주문량에 연관되어 있다고 볼 수 있습니다. 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM4MDMwNDEsNDY3ODgwMjc2LDYyOTQ3Nj
U3NiwtMTYxNjAzNjM5OSwyMTIxODA0NDIsMTE3OTcyNjYwLC0x
NzcxNDQ5NTg5LDEzNTM2NDk0MTYsMTY1MjQ5NzM2OSwtNjE3Nz
QxNzMzLC0xNzQ3MzEyNjc3LC0xMzgxNjQzOTExLC02MDk2MDU1
MzhdfQ==
-->