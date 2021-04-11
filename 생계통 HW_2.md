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
K+h\sum_{i=t}^{s-1}(1-q)^{i-t}d_i+\sum_{i=t}^{s-1}\sum_{j=0}^{i-t-1}(1-q)^jq(d_ip+jh)
$$
초기 주문 계획이 셋업 되면 변경하지 않으므로, Wagner-Within problem에서 DP algorithm을 활용한 것과 마지막 period부터 backtracking하며 최적의 비용을 구할 수 있습니다.
$$
\theta_t=min_{t \lt s \le T+1}(K+h\sum_{i=t}^{s-1}(1-q)^{i-t}d_i+\sum_{i=t}^{s-1}\sum_{j=0}^{i-t-1}(1-q)^jq(d_ip+jh)+\theta_s)
$$
(b) Wagner-Whitin algorithm과 (a)의 식을 활용하여, 다음과 같이 풀 수 있습니다:
$$
\theta_5 = 0 \\
\theta_4 = K+\theta_5 \\
\theta_3=min\{K+\theta_4, K+(1-q)+\theta_5\}
$$

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExNzg0MDAwODUsMTM1MzY0OTQxNiwxNj
UyNDk3MzY5LC02MTc3NDE3MzMsLTE3NDczMTI2NzcsLTEzODE2
NDM5MTEsLTYwOTYwNTUzOF19
-->