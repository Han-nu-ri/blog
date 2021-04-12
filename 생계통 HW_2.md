1. (a)
$$
g(Q, x)={K\lambda \over Q} + {hQ(1-x)^2 \over 2} + \lambda x p +\lambda(1-x)c
$$
(b)
g는 Q와 x의 함수입니다. 따라서 이를 최소화하기 위해서 Q와 x 각각으로 함수 g를 편미분해야 하고 그 값이 0으로 되어야 합니다.
g를 x에 대해서 편미분하게 되면 다음 식이 유도됩니다:
$$
{\partial g(Q, x) \over \partial x}=hQx-hQ+\lambda(p-c)=0 \\
hQ(1-x)=\lambda(p-c)
$$
g를 Q에 대해서 편미분하게 되면 다음 식이 유도됩니다:
$$
{\partial g(Q, x) \over \partial Q}=h(1-x)^2Q^2-2K\lambda=0 \\
Q^*=\sqrt {2K\lambda \over h} {1 \over (1-x)} \\
$$
Q*를 g(Q, x)에 대입하고 전개하면:
$$
g(Q, x)={K\lambda \over Q} + {hQ(1-x)^2 \over 2} + \lambda x p +\lambda(1-x)c \\
= K\lambda(1-x)\sqrt{h\over2K\lambda}+h\sqrt {2K\lambda \over h}{(1-x) \over 2}+\lambda xp+\lambda (1-x)c \\
= x(\lambda p-\lambda c-\sqrt {hK\lambda \over 2}
$$
$$
\lambda(p-c)=\sqrt {2K\lambda}
$$
하기 부등식이 이 성립하게 되면 x\*은 stockout을 허용하면 optimal에 solution이 되지 못하므로, x\*은 0이 됩니다.
$$
\lambda(p-c) \gt \sqrt {2K\lambda}
$$
하기 부등식이 이 성립하게 되면 x\* 은 주문을 하는 것이 손해가 되므로  x\*은 1이 됩니다.
$$
\lambda(p-c) \lt \sqrt {2K\lambda}
$$
(c\) 아래 부등식이 성립하는 경우 lost sale을 허용하지 않는 것이 더 싸다는 의미입니다. 
$$
\lambda(p-c) \gt \sqrt {2K\lambda}
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
eyJoaXN0b3J5IjpbMTEwMDIyMzg4MywxNzYxOTIxMzUwLDIwND
gyOTczMjYsMjExNzc0NDc5MCwtMTM2Mjc5NzAzMyw0Njc4ODAy
NzYsNjI5NDc2NTc2LC0xNjE2MDM2Mzk5LDIxMjE4MDQ0MiwxMT
c5NzI2NjAsLTE3NzE0NDk1ODksMTM1MzY0OTQxNiwxNjUyNDk3
MzY5LC02MTc3NDE3MzMsLTE3NDczMTI2NzcsLTEzODE2NDM5MT
EsLTYwOTYwNTUzOF19
-->