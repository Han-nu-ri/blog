# deterministic-inventory-model-1

## Introduction

정확한 시간에 적절한 양의 제품을 공급하는 것은 쉽지 않습니다. 평창 올림픽 때 유형했던 하얀색 롱패딩을 기억하시나요? 그 인기가 엄청 나서, 제품을 만드는 공급 업체는 다음해에 많이 만들어두었습니다. 그런데 하필 다음해 겨울은 매우 따뜻해서, 아웃도어업계는 넘쳐나는 재고에 힘들어했었죠.  
재고를 무조건 줄이는 것이 좋을까요? 요즘 수요 대비 공급이 현저히 부족하다고 이슈가 되는 차량 반도체를 생각해보죠. 이렇게 수요와 공급의 불균형이 언제 발생할 지 모르니, 일정량의 재고를 쌓는 것이 리스크를 피하는 길이겠죠.  
이렇게 최적의 재고량을 논하는 모델을 Deterministic Inventory Model이라고 합니다.

## Why holding inventory? Why is inventory important?
왜 우리는 재고가 필요한 것일까요? 여러 이유가 있습니다. 그 이유를 살펴보죠.
먼저 고객의 수요가 불확실합니다. 시장의 경쟁이 치열해짐에 따라 제품들의 라이프사이클이 굉장히 짧아지게 되고, 이런 경우 과거 데이터가 없어서 고객의 수요를 예측하기가 어렵습니다.
공급 측면에서도 품질이나 양, 비용 측면에서의 불확실성이 존재합니다. 제품의 원료 가격이 변동함에 따라 생산할 수 있는 양이 변하기도 하죠.
또한 주문 후 제품이 도착하는데 소요되는 lead time도 존재합니다.
아니면 규모의 경제 관점에서, 운송의 편함과 많은 양을 주문할 때 할인되는 정책 등을 활용하게 되면 이는 재고로 이어지게 됩니다.

재고가 필요한 이유를 살펴보면, 재고는 나쁜 것이 아닙니다. 여러 리스크를 줄이고, 보유 비용과 운송 비용 등 여러가지를 고려해서 재고의 양을 최적화하는 것이 필요하게 됩니다. 이렇게 여러 가지 요소를 고려해서 재고를 모델링하는 것을 Inventory model이라고 합니다.
## Relevant Costs
Inventory model을 살펴보기 앞서, 재고 관리와 관련된 여러 비용을 살펴보죠. Inventory model이 결국 비용을 최소화하는 것이니깐요.

## Measurement of Inventory Level
## Deterministic Inventory Models

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI1OTI2NDgzMiwtNDg0MjUwMDMyLC0xMT
M2NDE0Njk5LDgxMDk4MTA1NF19
-->