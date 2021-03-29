주성분 분석 (PCA, Principle Component Analysis)


주성분이란 데이터에 새로운 축을 긋고, 그 축에 데이터들을 사영 시켰을 때 분산이 큰 축을 의미합니다.

아래 데이터들을 주성분들은 오른쪽 위로 향하는 화살표로 표현되는 축과 왼쪽 위로 향하는 화살표로 표현되는 축입니다. 축이기 때문에 x축과 y축처럼 서로 직교해야 합니다. 따라서 분산이 가장 큰 오른쪽 위로 향하는 화살표가 첫 번째 주성분으로 정해지면, 이 주성분과 직교한 축 중 가장 분산이 큰 선을 찾습니다. 예시의 데이터는 이차원이기 때문에 정해져 있습니다.
![image](https://user-images.githubusercontent.com/11609881/112843195-4aadac00-90dd-11eb-8b6d-f81a1e87cbdf.png)
이미지 출처: https://en.wikipedia.org/wiki/Principal_component_analysis

PCA 방법
1. 데이터를 Zero-centered로 이동합니다.
2. 


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MDgyNzMxNDcsLTEyNzk5ODUzNDgsLT
E3OTk2ODU1MjgsLTE4OTc3NDYxMDhdfQ==
-->