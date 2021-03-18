# convex-optimization-a-quick-overview-4: 장벽 함수
이전 게시물에 이어, 볼록최적화와 관련된 여러 주제들을 다루는 글 입니다. 서울대 홍성필 교수님 최적화 원론 강의를 정리했음을 밝힙니다

이번 포스트에서는 barrier function에 대해 다루고자 합니다.
## Barrier function
$$
I(u)=\begin{cases}
0, & u \ge 0 \\
\infty, & u \lt 0 \\
\end{cases}
$$
위 식을 사용하여 아래 최적화 문제를 다시 써보죠.
$$
min\{f(x):g_i(x) \ge 0, 1 \le i \le m\} \\
= min \ f(x) + \sum_{i=1}^m I(g_i(x))
$$
만약 제약식 g(x)가 0보다 작게 되면, 함수 I에 의해 무한대가 됩니다. 쉽게 목적 함수와 제약식을 I를 통해 합칠 수 있는 것이 이해가 됩니다.
이렇게 제약식 있는 최적화 문제에서, barrier function은 최적화 문제의 Feasible region의 경계로 갈수록 무한대로 증가하는 함수를 말합니다.

## Logarithmic barrier function
위의 I가 무한대로 가기 때문에 계산적으로 다루기 어려워, 대신 이를 근사한 다음 함수를 사용할 수 있습니다.
$$
I(u)=-({1 \over t})log(u), \ t \gt 0.
$$
t는 조정 파라미터로 클수록 정확한 근사가 됩니다.
![Iu](https://user-images.githubusercontent.com/11609881/111646763-45cb3b80-8845-11eb-8a03-35fb0b8e97c7.gif)

예를 통해 t가 증가함에 따라 로그 배리어가 어떻게 변하는지 살펴보죠. 어떤 최적화 문제에 두 개의 제약식이 있다고 하면,
$$
g_1(x)=x \ge 0, \ g_2(x)=10 - x \ge 0. \\
$$
로그 배리어 함수는 아래와 같습니다.
$$
\sum_{i=1}^2 I(g_i(x))={1 \over t}(-ln(g_1(x))-ln(g_2(x)))={1 \over t}(-ln(x)-ln(10-x))
$$
![Iu](https://user-images.githubusercontent.com/11609881/111649736-ffc3a700-8847-11eb-8c57-31581d29daf7.gif)

> t > 0를 조정 파라미터로 하는 로그 장벽을 사용하여, 아래 문제 P를 제약식 없는 최적화 문제 (BP)로 변환하고, t가 무한히 커질 때 (BP)의 최적해가 P의 최적해로 수렴함을 보여라.
$$
\min {x_1^2+x_2^2} \\
s.t. \ x_1+x_2 \ge1.
$$


<!--stackedit_data:
eyJoaXN0b3J5IjpbMjExNTA2ODY1MSwtMTk4ODgyMDg5NiwyMD
E1NjA3NzAwLC0yMjU5NzI4MzQsLTEwNjIzODUyMTEsNjQ0ODIy
MzU5LDI4NjU3NTc2OV19
-->