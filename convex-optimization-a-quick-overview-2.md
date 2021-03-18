# convex-optimization-a-quick-overview-2
이전 게시물에 이어, 볼록최적화와 관련된 여러 주제들을 다루는 글 입니다. 서울대 홍성필 교수님 최적화 원론 강의를 정리했음을 밝힙니다.

> 선형 시스템 Ax = b의 해가 없는 경우, 대신 '오차'를 최소화하는 해를 구할 수 있다. 오차를 L2 norm으로 정의하면 다음의 최적화 문제가 된다.
$$
\min \lVert Ax-b \rVert_2
$$

Ax = b의 해가 없다는 것은 Ax로 펼쳐지는 공간에 b가 존재하지 않는다는 뜻 입니다. 그럼 위 최적화 문제의 최소해는 무엇일까요? 쉽게 생각하면, b로부터 A의 공간에 projection한 점을 b*이라 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgwMjU5ODM3Niw3NDUwMzU0OTUsLTE4Mz
gyMTAzMTFdfQ==
-->