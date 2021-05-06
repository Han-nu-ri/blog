생계통 HW#3
학번: 2021-21051
이름: 한누리

1.1)
X가 T 보다 큰 경우 Penalty cost가 발생하고, X가 T 이하인 경우 Fixed cost가 발생합니다.  f와 P는 각각 X의 pdf, cdf이므로 아래와 같은 cost 식이 성립합니다:
$$
g(T)=(1-F(T))K + F(T)pT
$$
1.2)
위 g(T)의 일계 도함수, 이계 도함수를 구하여 g가 볼록인지 확인합니다.
g(T)의 일계 도함수:
$$
g'(T)=-f(T)K+f(T)pT+F(T)p 
$$
g(T)의 이계 도함수:
$$
g''(T)=-f'(T)K+f'(T)pT+f(T)p+f(T)p \\
= f'(T)(pT-K) + 2f(T)p
$$
T < E[X]이므로, g''(T)는 양수입니다. 따라서 g느
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTkzMzYwMzcyLDE4ODI5OTY4MDRdfQ==
-->