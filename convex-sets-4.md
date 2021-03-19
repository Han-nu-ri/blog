# convex-sets-4: 선형 독립, 선형 종속, 평면 독립, 평면 종속
선형 독립, 선형 종속, 평면 독립, 평면 종속에 관한 포스트입니다. 서울대 홍성필 교수님의 최적화 원론 강의와 위키피디아를 정리했음을 밝힙니다. 
## 선형 독립과 선형 종속 (Linearly dependent, linearly independent)
벡터들의 집합 V이 있습니다.  V에 속하는 하나의 벡터가 다른 벡터들의 선형 결합으로 표현된다고 해보죠. 그럼 집합 V을 선형 종속이라고 합니다. 하나의 벡터를 다른 벡터들의 선형 결합으로 표현할 수 있는 경우가 없다면, 집합 V를 선형 독립이라고 합니다.
선형 종속의 예를 들어보죠. 
$$
V=\{v_1, v_2, v_3\}
=\{
\begin{pmatrix} 1 \\ 0 \end{pmatrix}, 
\begin{pmatrix} 0 \\ 1 \end{pmatrix},
\begin{pmatrix} 2\\ 2 \end{pmatrix}
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
\begin{pmatrix} 1 \\ 0 \\ 0\end{pmatrix}, 
\begin{pmatrix} 0 \\ 1 \\ 0\end{pmatrix},
\begin{pmatrix} 0 \\ 0 \\ 1 \end{pmatrix}
\}
$$
위와 같은 집합 V에서, 다른 두 벡터의 선형 결합으로 하나의 벡터를 표현할 수 없습니다. 따라서 V는 선형 독립입니다.

예시를 잘 살펴보면 직관적으로 아래와 같이 이해할 수 있습니다.
> 벡터들의 집합의 원소들이 span을 생성하는데 필요한 최소한의 벡터들보다 더 있다면 선형 종속이고, 필요한 최소한의 벡터들만 있다면 선형 독립이다.

## 평면 독립과 평면 종속 (Affinely dependent, affinely independent)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1ODA5NzYzNDAsMTUzMTIyMDcxMywtOT
Q2ODU3OTFdfQ==
-->