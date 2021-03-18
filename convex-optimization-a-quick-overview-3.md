# convex-optimization-a-quick-overview-3
이전 게시물에 이어, 볼록최적화와 관련된 여러 주제들을 다루는 글 입니다. 서울대 홍성필 교수님 최적화 원론 강의를 정리했음을 밝힙니다.

이번 포스팅에서는 최적화 방법 중 First-order method, Second-order method에 대하여 적어보려고 합니다.
## First-order method: 일계 방법
First-order method는 최적화 문제에서 목적 함수의 1차 미분(gradient)를 활용하여 최적해를 찾습니다. 그래서 First-order 이라는 이름이 붙였겠죠? 딥러닝에서 많이 활용되고 있는 gradient descent도, 손실 함수를 각 파라미터로 편미분한 gradient를 활용하여 손실 함수가 줄어드는 방향으로 파라미터를 업데이트하죠.  gradient descent가 바로 First-order method 입니다.
## Second-order method: 이계 방법
Second-order method는 최적화 문제에서 목적 함수의 2차 미분(gradient)를 활용하여 최적해를 찾습니다.  뉴튼vex-optimization-a-quick-overview-3
이전 게시물에 이어, 볼록최적화와 관련된 여러 주제들을 다루는 글 입니다. 서울대 홍성필 교수님 최적화 원론 강의를 정리했음을 밝힙니다.이번 포스팅에서는 최적화 방법 중 First-order method, Second-order method에 대하여 적어보려고 합니다.## First-order method: 일계 방법First-order method는 최적화 문제에서 목적 함수의 1차 미분(gradient)를 활용하여 최적해를 찾습니다. 그래서 First-order 이라는 이름이 붙였겠죠? 딥러닝에서 많이 활용되고 있는 gradient descent도, 손실 함수를 각 파라미터로 편미분한 gradient를 활용하여 손실 함수가 줄어드는 방향으로 파라미터를 업데이트하죠.  gradient descent가 바로 First-order method 입니다.## Second-order method: 이계 방법Second-order method는 최적화 문제에서 목적 함수의 2차 미분(gradient)를 활용하여 최적해를 찾습니다.  뉴튼

<!--stackedit_data:
eyJoaXN0b3J5IjpbMzExMjU5ODMzLDIwMTM2MDY5MDMsOTczNz
Y5NzA2XX0=
-->