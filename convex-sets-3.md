# convex-sets-3: 평면집합의 성질, 기저, 빈공간, 가우스-조던 소거법
이전 포스트 (https://nrhan.tistory.com/entry/convex-sets-2-평면-집합-평면-덮개)에 이어, 평면집합의 성질, 기저, 빈공간, 가우스 조던 소거법에 관한 포스트입니다. 서울대 홍성필 교수님의 최적화 원론 강의와 위키피디아를 정리했음을 밝힙니다. 

## 평면집합 L을 임의의 자신의 원소 w로 평행이동한 집합은 부분 공간이다.

평면집합 L을 임의의 자신의 원소 w만큼 평행이동한 집합은 아래와 같습니다.
$$
L-w \equiv \{v-w : v\in L\}
$$
부분 공간은 원점을 지나야 하고, 덧셈과 실수 곱에 대하여 닫혀 있어야 합니다. w는 L의 원소이므로, L-w는 원점을 지납니다. 또한 L이 평면집합이므로, L은 덧셈과 실수 곱에 대하여 닫혀 있습니다. L-w는 단순히 L을 평행이동한 것이므로, L-w도 덧셈과 실수 곱에 대하여 닫혀 있음을 쉽게 알 수 있습니다.
![image](https://user-images.githubusercontent.com/11609881/111738805-5622fb00-88c5-11eb-89cc-15639cc6b46a.png)
구체적으로 집합 L-w이 부분 공간인지 볼까요?
1. 원점을 지나야 한다.
w는 L의 원소이므로, v가 w일 때 0이 됩니다. 따라서 원점을 지남을 알 수 있습니다.
2. 덧셈과 실수 곱에 대하여 닫혀 있어야 한다.
L에 속하는 두 벡터와, 임의의 스칼라를 세팅합니다.
$$
\forall u, v \in L, \forall \alpha \in R
$$
위 두 벡터를 w만큼의 평행 이동하고, 하나의 벡터에 스칼라 곱을 한 벡터가 L-w에 속함을 보이면 됩니다.
$$
y=(u-w)+\alpha(v-w)
$$
식의 순서를 바꿔서 전개하면 아래와 같고, 괄호의 u, v, w 벡터는 L에 속하고 계수의 합은 1이므로 평면조합이 되어 괄호 벡터가 L에 속함을 알 수 있습니다.
$$
y=(u-w)+\alpha(v-w) \\
= (u+\alpha v-\alpha w)-w
$$
따라서 y는 L-w에 속합니다.

위의 성질을 역으로 하면,
> 부분 공간 S를 임의의 벡터 w로 평행이동한 집합 S + w는 평면집합이다.

따라서 부분공간은 0을 포함하는 평면집합으로 이해할 수 있습니다.
## 기저(basis)
> 선형대수학에서, 어떤 벡터 공간의 기저(基底, 영어: basis)는 그 벡터 공간을 선형생성하는 선형독립인 벡터들이다.

이차원 평면을 떠올려보죠. 이 평면을 두 가지 벡터의 덧셈과 스칼라 곱의 조합으로 나타내보려고 합니다. 아래 세 가지 벡터 중 어떤 벡터 두 가지를 고르면 될까요?
$$
v_1=(1,0), v_2=(0,1), v_3=(1, 1)
$$
바로 v1과 v2입니다. v1과 v2에 임의의 스칼라를 곱하고, 둘을 더하면 이차원 평면을 모두 표현할 수 있습니다. 이들을 기저라고 합니다.
$$
av_1+bv_2, a, b\in R
$$
v2와 v3는 어떨까요? (1, 0)을 v2와 v3으로 나타낼 수 있나요?
$$
av_2+bv_3=(1, 0)?
$$

## 빈공간(영공간, null space)
행렬 A의 빈공간이란, Ax=0의 모든 해 집합 x를 빈공간이라고 합니다.
$$
A \in R^{m \times n}, N(A)=\{x|Ax=0\}.
$$
Ax=0의 선형 변환은 아래와 같은 그림으로 이해할 수 있습니다.
![image](https://user-images.githubusercontent.com/11609881/111743149-99349c80-88cc-11eb-910d-8e8b64e0e4f2.png)
## 가우스 조던 소거법
가우스 조던 소거법은 일차 연립 방정식의 해를 구하는 방법으로, 기본 행 연산(행의 치환, 상수곱, 행의 합)을 적용해도 연립 방정식의 해가 변하지 않는다는 사실을 활용하여 해를 쉽게 구하는 방법입니다. 각 행을 왼쪽부터 읽었을 때 첫 요소를 0이 나오다가 1로 만드는 과정을 거칩니다.
## 부분 공간의 기저를 사용하여 부분 공간을 빈공간으로 가지는 행렬 A를 구할 수 있다.
> 벡터 [2, 1, 0, 2], [-2, 1, 1, 0]가 기저가 되는 부분 공간을 빈공간으로 가지는 행렬 A를 구하라.

1.기저 벡터를 아래로 붙인 후 2. 가우스-조던 소거법을 하고 3. 소거되지 않은 행렬에 음수를 붙인 다음 4. Identity 행렬을 붙입니다. 5. Transpose를 합니다.

위의 순서에 따라 진행해보죠.
1.기저 벡터를 아래로 붙인 후 2. 가우스-조던 소거법을 하고
$$
\begin{pmatrix} 2 & 1 & 0 & 2 \\ -2 & 1 & 1 & 0 \end{pmatrix}
= \begin{pmatrix} 1 & 0 & {-1 \over 4} & {1 \over 2} \\ 0 & 1 & {1 \over 2} & 1 \end{pmatrix}
$$
3. 소거되지 않은 행렬(빨간색 박스)에 음수를 붙인 다음
![image](https://user-images.githubusercontent.com/11609881/111750968-3f859f80-88d7-11eb-8104-42815c3f1176.png)
$$
\begin{pmatrix} {1 \over 4} & {-1 \over 2} \\ {-1 \over 2} & -1 \end{pmatrix}
$$
4. Identity 행렬을 붙입니다.
$$
\begin{bmatrix} {1 \over 4} & {-1 \over 2} \\ {-1 \over 2} & -1  \\ 1 & 0 \\ 0 & 1 \end{bmatrix}
$$
5. Transpose를 합니다.
$$
\begin{pmatrix} {1 \over 4} & {-1 \over 2} & 1 & 0\\ 
{-1 \over 2} & -1 & 0 & 1  \\
\end{pmatrix}
$$
위 행렬 A는 벡터 [2, 1, 0, 2], [-2, 1, 1, 0]가 기저가 되는 부분 공간을 빈공간으로 가지게 됩니다.
확인해볼까요? 
$$
Ax= 
\begin{bmatrix} {1 \over 4} & {-1 \over 2} & 1 & 0\\ 
{-1 \over 2} & -1 & 0 & 1  \\
\end{bmatrix}
\begin{bmatrix} x_1 \\ x_2 \\ x_3 \\ x_4
\end{bmatrix}
=\begin{bmatrix} {1 \over 4} & {-1 \over 2} & 1 & 0\\ 
{-1 \over 2} & -1 & 0 & 1  \\
\end{bmatrix}
\begin{bmatrix} 2 \\ 1 \\ 0 \\ 2
\end{bmatrix}
= \begin{bmatrix} 0 \\ 0 \end{bmatrix}
$$

## 행렬 A의 빈공간 구하기
> 다음 행렬의 빈공간을 구하라
$$
A= \begin{pmatrix} 1 & 1 & 1 \\ 0 & -1 & 2 \end{pmatrix}
$$

빈공간의 정의에 따라, 
$$
Ax=0, \space
\begin{bmatrix} 1 & 1 & 1 \\ 0 & -1 & 2 \end{bmatrix}
\begin{bmatrix} x_1 \\ x_2 \\ x_3 \end{bmatrix}
= \begin{bmatrix} 0 \\ 0 \end{bmatrix}. \\
$$
과 같습니다. 각각의 식을 전개해보죠.
$$
x_1+x_2+x_3=0 \cdots 1), \space
-x_2+2x_3=0 \cdots 2)\\
$$
식 2)에서 x2를 우변으로 옮기면.
$$
2x_3=x_2 \\
$$
식 2)를 식 1)에 대입하면.
$$
x_1+3x_3=0 \\
x_1=-3x_3
$$
x3가 1이라 하면 x2는 2, x1은  -3 입니다. 따라서 빈공간은 아래와 같습니다.
$$
c {\begin{bmatrix} -3 \\ 2 \\ 1 \end{bmatrix}}, \forall c \in R,
$$
## 모든 평면 집합 L은 어떤 행렬 A의 선형 시스템 Ax=b의 해 집합이다.
x, w를 L의 원소라고 두면, L-w은 부분 공간이 됩니다. 위에서 보인 것처럼 부분 공간의 기저를 사용하면 부분 공간을 빈공간(영공간, null space)으로 하는 행렬 A를 구할 수 있습니다. A의 빈공간은 A에 의하여 0으로 변환되는 벡터들의 집합이므로,
$$
A(x-w)=0
$$
가 됩니다.
Aw를 b로 두면
$$
Ax=b
$$
가 되고, x는 L의 원소이므로 L은 선형 시스템 Ax=b의 해 집합입니다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU1MDE2OTMyLC0xOTIzMzc3MDY0LC0xNz
QxMjc3ODgwLC0xOTgxNzMyMjgwLC03NzYyNjU0MDYsMTY2NDQx
MjQxMiwtMTQ3NTY2MTQ0MiwtMTA5NDAzODgyMiwxMTQyNzI0MT
IxLDQ2MjIyNDM4NywxOTI2Njk0MzQ4LDc3MTQ3NDc3OSwtNTgz
MzA2ODI5LC0xNTQwNzI3NTIyLC0xODAxNTA2Nzg1LC0xMTE5OD
g3MTUsLTcyOTczOTg4Myw1MTY3NTM1MywyMDYyNzA5MTkzLC05
ODM4NzU5MjddfQ==
-->