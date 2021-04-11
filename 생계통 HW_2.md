1. EOQ model
. allowed to stock out
. excess demands are lost
. x: fraction of demand that is lost
. p: cost per each lost unit
. c: cost to order per each unit. We should consider c because some demands are lost.

Since it is EOQ model, suppose:
. L = 0
. Fixed   cost = K
. 
Basic EOQ model
$$
g(Q)={K\lambda \over Q}+h
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
\theta_4 = K+\theta_5 =200 (s(4)=5)\\
\theta_3=min\{K+\theta_4, K+h(1-q)d_4+pqd_4+\theta_5\} \\
= min\{400, 200+0.2(0.75)175+3(0.25)175\} \\
= min\{400, 357.5\}
= 357.5 (s(3)=5)\\
\theta_2=min\{K+\theta_3, K+h(1-q)d_3+pqd_3+\theta_4, \\
K+h(1-q)d_3+pqd_3+h(1-q)^2d_4+(1-q)qd_4(p+h)+pqd_4+\theta_5\} \\
= min\{557.5, 625, 680.9375\} \\
= 557.5 (s(2)=3) \\
\theta_1 = min\{K+\theta_2, \\
K+h(1-q)d_2+pqd_2+\theta_3,\\
K+h(1-q)d_2+pqd_2+h(1-q)^2d_3+(1-q)qd_3(p+h)+pqd_3+\theta_4,\\
K+h(1-q)d_2+pqd_2+h(1-q)^2d_3+(1-q)qd_3(p+h)+pqd_3+\\
h(1-q)^3d_4+qd_4((1-q)^2(p+2h)+(1-q)(p+h)+p)+\theta_5\} \\
= min\{757.5, 670,  878.125, \}
$$

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MTYwMzYzOTksMjEyMTgwNDQyLDExNz
k3MjY2MCwtMTc3MTQ0OTU4OSwxMzUzNjQ5NDE2LDE2NTI0OTcz
NjksLTYxNzc0MTczMywtMTc0NzMxMjY3NywtMTM4MTY0MzkxMS
wtNjA5NjA1NTM4XX0=
-->