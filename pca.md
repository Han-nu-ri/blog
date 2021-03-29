주성분 분석 (PCA, Principle Component Analysis)


차원 축소 시 많이 사용되는 주성분 분석에 대한 포스트입니다. 위키피디아와 StatQuest(https://www.youtube.com/watch?v=FgakZw6K1QQ)를 참고했음을 밝힙니다. 

주성분이란 데이터를 어떤 축에 projection 하였을 때 그 분산이 큰 축들을 말합니다. 분산이 크다는 것은 데이터가 퍼져 있는 것을 잘 설명하기 때문에 주요하다고 보는 것 입니다.
아래 데이터들을 주성분들은 오른쪽 위로 향하는 화살표로 표현되는 축과 왼쪽 위로 향하는 화살표로 표현되는 축입니다. 축이기 때문에 x축과 y축처럼 서로 직교해야 합니다. 따라서 분산이 가장 큰 오른쪽 위로 향하는 화살표가 첫 번째 주성분으로 정해지면, 이 주성분과 직교한 축 중 가장 분산이 큰 선을 찾습니다. 예시의 데이터는 이차원이기 때문에 정해져 있습니다.
![image](https://user-images.githubusercontent.com/11609881/112843195-4aadac00-90dd-11eb-8b6d-f81a1e87cbdf.png)
이미지 출처: https://en.wikipedia.org/wiki/Principal_component_analysis




<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIzNzUxMzA4OCwtMTc5OTY4NTUyOCwtMT
g5Nzc0NjEwOF19
-->