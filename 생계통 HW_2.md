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

2. (a) arc(t, s)는 수요를 충족 시킨
$$
\theta_t=min_{t \lt s \le T+1}(K+h\sum_{i=t}^{s-1}(1-q)^{i-t}d_i+\sum_{i=t}^{s-1}\sum_{j=0}^{i-t-1}(1-q)^jq(d_ip+jh)+\theta_s)
$$

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYxNzEyMDEyNSwxMzUzNjQ5NDE2LDE2NT
I0OTczNjksLTYxNzc0MTczMywtMTc0NzMxMjY3NywtMTM4MTY0
MzkxMSwtNjA5NjA1NTM4XX0=
-->