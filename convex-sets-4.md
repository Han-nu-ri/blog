# convex-sets-4: 선형 독립, 선형 종속, 평면 독립, 평면 종속
선형 독립, 선형 종속, 평면 독립, 평면 종속에 관한 포스트입니다. 서울대 홍성필 교수님의 최적화 원론 강의와 위키피디아를 정리했음을 밝힙니다. 
## 선형 독립과 선형 종속 (Linearly dependent, linearly independent)
벡터들의 집합 V이 있습니다.  V에 속하는 하나의 벡터가 다른 벡터들의 선형 결합으로 표현된다고 해보죠. 그럼 집합 V을 선형 종속이라고 합니다. 하나의 벡터를 다른 벡터들의 선형 결합으로 표현할 수 있는 경우가 없다면, 집합 V를 선형 독립이라고 합니다.
선형 종속의 예를 들어보죠. 
$$
V=\{v_1, v_2, v_3\}
=\{
\begin{bmatrix} 1 \\ 0 \end{bmatrix}, 
\begin{bmatrix} 0 \\ 1 \end{bmatrix},
\begin{bmatrix} 2\\ 2 \end{bmatrix}
\}
$$
위와 같은 집합 V에서, v3은 다른 두 벡터의 선형 결합으로 표현될 수 있습니다.
$$
v_3=2v_1+2v_2
$$
따라서 V는 선형 종속입니다.
선형 독립의 예를 들어보죠.
$$
V=\{v_1, v_2, v_3\}
=\{
\begin{bmatrix} 1 \\ 0 \\ 0\end{bmatrix}, 
\begin{bmatrix} 0 \\ 1 \\ 0\end{bmatrix},
\begin{bmatrix} 0 \\ 0 \\ 1\end{bmatrix}
\}
$$
위와 같은 집합 V에서, 다른 두 벡터의 선형 결합으로 하나의 벡터를 표현할 수 없습니다. 따라서 V는 선형 독립입니다.

예시를 잘 살펴보면 직관적으로 아래와 같이 이해할 수 있습니다.
> 벡터들의 집합에 span을 생성하는데 필요한 최소한의 벡터들보다 더 있다면 선형 종속이고, 필요한 최소한의 벡터들만 있다면 선형 독립이다.

## 평면 독립과 평면 종속 (Affinely dependent, affinely independent)
선형 독립과 종속을 직관적으로 이해한 것처럼, 평면 독립과 종속을 이해할 수 있습니다.
> 벡터들의 집합에 그들의 평면 덮개(Affine hull)을 생성하는데 필요한 벡터들보다 더 있다면 평면 종속, 필요한 최소한의 벡터들만 있다면 평면 독립이다.

평면 독립의 예를 들어보겠습니다.
$$
V=\{v_1, v_2, v_3\}
=\{
\begin{pmatrix} 1 \\ 0 \end{pmatrix}, 
\begin{pmatrix} 0 \\ 1 \end{pmatrix},
\begin{pmatrix} 2\\ 2 \end{pmatrix}
\}
$$
집합 V의 모든 점이 남은 점들로 생성된 affine hull에 속하지 않습니다. 따라서 평면 독립(affine independent)입니다.
![image](https://user-images.githubusercontent.com/11609881/111814553-f4db4600-891d-11eb-9c39-e9a478eae763.png)

평면 종속의 예를 들어보겠습니다.
$$
V=\{v_1, v_2, v_3\}
=\{
\begin{pmatrix} 1 \\ 0 \end{pmatrix}, 
\begin{pmatrix} 0 \\ 1 \end{pmatrix},
\begin{pmatrix} {1 \over 2}\\ {1 \over 2} \end{pmatrix}
\}
$$
집합 V의 점 (1/2, 1/2)은 남은 점들로 생성된 affine hull에 속합니다. 따라서 평면 종속(affine dependent)입니다.
![image](https://user-images.githubusercontent.com/11609881/111814599-0290cb80-891e-11eb-9a33-3e56f46cf894.png)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMjU1OTM3NDAsLTEyMjU1OTM3NDAsMz
A2NDA5OTU2LDIyMDQyNjE0MSwxNTMxMjIwNzEzLC05NDY4NTc5
MV19
-->