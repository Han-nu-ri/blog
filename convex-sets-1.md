# convex-sets-1: 
볼록 집합과 볼록 덮개에 관한 포스트입니다. 서울대 홍성필 교수님의 최적화 원론 강의를 정리했음을 밝힙니다.
## 볼록 조합
두 개의 벡터 x, y를 연결하는 직선을 \lambda의 함수로 표현하면 아래와 같습니다.
$$
x+\lambda (y-x)=(1-\lambda)x + \lambda y
$$
위 식을 x와 y의 평면 조합이라고 합니다. 특히, x와 y 사이 선분의 점이 되도록 
$$
0 \le \lambda \le 1
$$
이면 볼록 조합이라고 합니다.
![image](https://user-images.githubusercontent.com/11609881/111660340-51bcfa80-8851-11eb-882b-ac8bc545f481.png)
https://nrhan.tistory.com/entry/convex-optimization-a-quick-overview-1?category=1192042
에서 볼록 집합에 대해서 설명해두었는데요. 볼록 조합으로 볼록 집합을 설명하면, 
> 집합 S의 임의의 두 점에 대한 볼록 조합이 집합 S에 속하면 집합 S는 볼록 집합이다

입니다.

다시 볼록 조합으로 돌아와서, 볼록 조합을 세 개의 벡터로 확장해볼까요? 세 개의 벡터에 대한 볼록 조합은 아래와 같이 표현할 수 있습니다.
$$
\sum_{i=1}^3 \lambda_i x_i \\ 
\sum_{i=1}^3 \lambda_i=1, \forall \lambda_i \ge0, 1\le i \le 3.
$$
어떻게 저렇게 간단히 표현될 수 있을지 알아보죠. 위 식을 전개하면,
$$
\sum_{i=1}^3 \lambda_i x_i
= \lambda_1 x_1 + \lambda_2 x_2 + \lambda_3 x_3
= (\lambda_1 + \lambda_2){\lambda_1 x_1 + \lambda_2 x_2 \over \lambda_1 + \lambda_2} + \lambda_3 x_3
$$
입니다. 위 식 중 {\lambda_1 x_1 + \lambda_2 x_2 \over \lambda_1 + \lambda_2}를 분석해보면, x1과 x2 두 벡터 간 볼록 조합임을 알 수 있습니다. (왼쪽 그림)
$$
let \ {\lambda_2 \over \lambda_1 + \lambda_2} = \lambda_a\\
then
{\lambda_1 x_1 + \lambda_2 x_2 \over \lambda_1 + \lambda_2}
=(1-\lambda_a)x_1+\lambda_ax_2, \ 0 \le \lambda_a \le 1
$$
마찬가지로 나머지 식은 두 벡터의 볼록 조합과 점 x3간 볼록 조합임을 알 수 있습니다. (오른쪽 그림)
![image](https://user-images.githubusercontent.com/11609881/111662809-9c3f7680-8853-11eb-8e81-f2491b6a3edc.png)

이를 유한 개의 벡터로 확장하면 아래와 같습니다.
> 다음을 벡터 v1, v2, ... , vk의 볼록 조합이라고 한다.
$$
v=\lambda_1 v_1 + \cdots + \lambda_k v_k\\
\forall k \in N, \sum_{i=1}^k \lambda_i=1, \lambda_1 \ge 0, \lambda_2 \ge 0, ... , \lambda_k \ge 0
$$

ㅇ
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUyNzU2NDA4LC0zMDk1MDE1MSwxNzA5OT
M5ODY3LC04MDQ1NjI4OTRdfQ==
-->