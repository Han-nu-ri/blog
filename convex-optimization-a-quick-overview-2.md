# convex-optimization-a-quick-overview-2
이전 게시물에 이어, 볼록최적화와 관련된 여러 주제들을 다루는 글 입니다. 서울대 홍성필 교수님 최적화 원론 강의를 정리했음을 밝힙니다.
## 헤시안 (Hessian)
위키피디아에서는 헤세 행렬로 나옵니다. 어떤 함수의 이계도함수를 행렬로 표현한 것 입니다.
$$
f(x)=f(x_1, x_2,... ,x_n),
H(f)= \begin{bmatrix}
{\partial^2f\over\partial x_1\partial x_1} & {\partial^2f\over\partial x_1\partial x_2} & \cdots & {\partial^2f\over\partial x_1\partial x_n} \\
{\partial^2f\over\partial x_2\partial x_1} & {\partial^2f\over\partial x_2\partial x_2} & \cdots & {\partial^2f\over\partial x_2\partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
{\partial^2f\over\partial x_n\partial x_1} & {\partial^2f\over\partial x_n\partial x_2} & \cdots & {\partial^2f\over\partial x_n\partial x_n} \\
\end{bmatrix}
$$
## Positive semidefinite (PSD)
어떤 n X n 대칭행렬 M이 있을 때, 아래를 만족하면 PSD라고 합니다.
$$
M\ PSD\Longleftrightarrow z^TMz \ge 0, \forall z \in R^n
$$
## 응용
> 선형 시스템 Ax = b의 해가 없는 경우, 대신 '오차'를 최소화하는 해를 구할 수 있다. 오차를 아래와 같이 정의하면 다음의 최적화 문제가 된다.
$$
\min \lVert Ax-b \rVert_2
$$

위 문제는 제약 조건이 없는 최적화 문제입니다. 먼저 목적 함수가 볼록 함수인지 확인해보고, 볼록이면 제약 조건이 없으므로 내부해(stationary point)가 최적해가  됩니다. 내부해와 관련된 내용은 https://nrhan.tistory.com/entry/convex-optimization-a-quick-overview-1 에 있습니다.

Ax = b의 해가 없다는 것은 Ax로 펼쳐지는 공간에 b가 존재하지 않는다는 뜻 입니다. 그럼 위 최적화 문제의 최소해는 무엇일까요? 쉽게 생각해서 b로부터 Ax의 공간에 projection한 점을 b*이라 두면, b*은 Ax 위의 공간이자 b와의 거리가 최소화되는 점 입니다. 따라서 최적해 x*은 b*을 A1, A2, ... , An으로 표현할 때의 계수가 됩니다.
![image](https://user-images.githubusercontent.com/11609881/111558792-ce5cc400-87d2-11eb-9a1c-43ed9448887a.png)

위 목적 함수를 L2 norm으로 바꿔도 최적해는 변하지 않으므로 우리의 최적화 문제를
$$
\min \lVert Ax-b \rVert_2^2
$$
으로 변경하죠. 목적 함수를 전개하면 아래와 같이 됩니다.
$$
\lVert Ax-b \rVert_2^2 = (Ax-b)^T(Ax-b)=x^TA^TAx-x^TA^Tb-b^TAx+b^Tb=x^TA^TAx-2b^TAx+b^Tb
$$
어떻게 볼록 함수인지 확인할 수 있을까요? 여러 방법이 있겠지만, 다음 성질을 사용해보죠.
> 이차 미분 가능 함수가 볼록일 필요 충분 조건은 헤시안이 모든 x에 대해서 PSD인 것이다.

목적 함수의 헤시안을 구해보면 아래와 같습니다.
$$
H(f)=\nabla^2f(x)=A^T
A$$
위 헤시안이 PSD인지 살펴볼까요? PSD라면 아래를 만족해야 합니다.
$$
A^TA \ PSD \Longleftrightarrow z^TA^TAz \ge 0, \forall z \in R^n
$$
그런데 위 부등식의 좌편의 항은 Az의 two norm입니다.
$$
z^TA^TAz=\lVert Az \rVert_2^2 \ge 0
$$
따라서 헤시안은 PSD입니다. 그러므로 이 목적 함수는 제약 조건 없는 볼록 함수가 되므로, 내부해가 최적해가 됩니다.

내부해는 기울기 벡터가 0인 해이므로,  기울기 벡터를 0 벡터로 만드는 x가 최적해가 됩니다.
$$
f(x)=x^TA^TAx-2b^TAx+b^Tb
$$
기울기 벡터를 구하기 위해 A와 x, b를 아래와 같이 둬보죠.
$$
A= \begin{bmatrix}
[[
\end{bmatrix}
$$
$$
\nabla f(x)=2A^TA
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAwMDM4NzkyOSwtMTg3ODY3MDgyMiw3MT
M5ODU0MTMsMTA3NDUzMzQyOCwyMDI5ODM5MjI4LC0xODI5NjA0
NjkyLDI1NzE3ODgyMCwtMTc2NzAzODI4NCwtNDk1NTQwNjM3LD
c0NTAzNTQ5NSwtMTgzODIxMDMxMV19
-->