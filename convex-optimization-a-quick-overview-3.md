# convex-optimization-a-quick-overview-3
이전 게시물에 이어, 볼록최적화와 관련된 여러 주제들을 다루는 글 입니다. 서울대 홍성필 교수님 최적화 원론 강의를 정리했음을 밝힙니다.

이번 포스팅에서는 최적화 방법 중 First-order method, Second-order method에 대하여 적어보려고 합니다.
## First-order method: 일계 방법
First-order method는 최적화 문제에서 목적 함수의 1차 미분(gradient)를 활용하여 최적해를 찾습니다. 그래서 First-order 이라는 이름이 붙였겠죠? 딥러닝에서 많이 활용되고 있는 gradient descent도, 손실 함수를 각 파라미터로 편미분한 gradient를 활용하여 손실 함수가 줄어드는 방향으로 파라미터를 업데이트하죠.  gradient descent가 바로 First-order method 입니다.
$$
x^{k+1}=x^{k}-\sigma^{k}{\nabla f(x^k)}
$$
## Second-order method: 이계 방법
Second-order method는 뉴튼 방식이라고도 불립니다. 목적 함수를 이차 근사 한 후에, 이차 근사 함수를 최소로 하는 점인 기울기 벡터가 0인 점을 향하도록 움직입니다.
이차 근사에 대한 기울기 벡터를 구하기 쉽게 구하기 위해, 다음 이차 함수를 생각해보죠.
$$
f(x)=c+bx+{1 \over 2} x^TQx
$$
위 이차 함수의 기울기 벡터를 구하면
$$
\nabla f(x)=b+Qx
$$
가 됩니다. 만약 f(x)가 제약 없는 볼록 함수라면, 안장점이 최소점이 되겠죠.
$$
\nabla f(x)=b+Qx=0 \\
x=-Q^{-1}b
$$
이제 일반적인 함수 f 의 점 x^k에서의 이차 근사해보면,
$$
\tilde{f}(x)= f(x^k)+\nabla f(x^k)(x-x^k)+{1 \over 2}(x-x^k)\nabla^2f(x^k)(x-x^k)
$$
입니다.
$$
\nabla {\tilde{f}(x^k)} = b, x-x^k=z, \nabla^2f(x^k)=Q
$$
라 하면,
$$
\tilde{f}(x)=f(x^k)+bz+{1 \over 2}z^TQz \\
\nabla {\tilde{f}(x)}=b+Qz=\nabla f(x^k)+\nabla^2f(x^k)({x-x^k})
$$
안장점을 향하는 방향은 아래와 같습니다.
$$
\nabla {\tilde{f}(x)}=\nabla f(x^k)+\nabla^2f(x^k)({x-x^k})=0 \\
x=x^k-(\nabla^2f(x^k))^{-1}\nabla f(x^k)
$$
함수 f가 이차 근사식이 아니라, 일반적인 이차 식이라면 바로 x를 위의 식으로 구하면 되겠죠. 이차 함수의 미분 값이 0인 지점이 최적해인 것처럼요. 
그런데 우리의 함수 f를 이차 근사한 것이기 때문에 바로 이동하는 것이 아니라 learning rate 만큼 이동해주어야 합니다.
$$
x^{k+1} \leftarrow x^k-(\nabla^2f(x^k))^{-1}\nabla f(x^k)
$$

지금까지 배운 것을 토대로, 다음 문제를 풀어보세요.
> 다음 함수의 현재 점 x^k에서 뉴튼 방향을 구하라.
$$
f(x)={{e^{x_1}+e^{-x_1}} \over 2} + {{e^{x_2}+e^{-x_2}} \over 2}
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExODUzODM5ODQsLTE2NTg0MDQ3NjIsLT
Y4ODI1MTI5Niw5NzEzOTMwMTgsMzExMjU5ODMzLDIwMTM2MDY5
MDMsOTczNzY5NzA2XX0=
-->