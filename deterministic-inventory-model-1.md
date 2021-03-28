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
### Holding cost
재고를 보유하는 비용을 의미합니다. 물리적으로 공간을 차지하는 것 뿐만 아니라, 세금, 보험, 그리고 기회 비용까지 포함합니다. 종종 1년 단위로 제품의 가치치의 비율로 표현됩니다.
### Stockout cost
수요를 충족 시킬 수 있는 충분한 재고가 없을 때 발생하는 비용입니다. 재고가 없어서 떠나는 수요의 양과, 예약 구매자를 위한 비용, 지연 비용 등이 포함됩니다.
### Fixed cost
주문마다 발생하는 고정된 비용을 의미합니다. 제품의 크기와는 무관하게 주문을 발주하면서 발생하는 관리 비용, 배송 비용 등을 포함합니다.
### Purchase cost
제품의 단위마다 발생하는 구매 비용입니다.
## Measurement of Inventory Level
Inventory level은 현재 판매할 수 있는 재고의 양과 수요가 발생했지만 아직 물품을 주지 못한 양으로 결정됩니다. 현재 판매할 수 있는 재고의 양을 On-Hand inventory(OH), 수요가 발생했지만 아직 배송 못한 양을 Backorders(BO)라고 합니다. Inventory Level은 아래와 같이 정의 됩니다.
$$
IL = OH - BO
$$
그럼 우리는 주문하기 위한 요소들을 모두 고려했을까요? 주문이 완료되어, 지금 창고로 배송 오고 있는 양을 고려하지 않았습니다. 이를 On-Order(OO)이라고 하고, OO까지 고려한 개념을 Inventory Position(IP)이라고 합니다.
$$
IP = OH - BO + OO
$$
## Deterministic Inventory Models
Deterministic Inventory Model은 수요의 불확실성이 없음을 가정한 모델입니다. 재고의 주문이 연속적으로 이뤄지는 Continuous review와 특정한 주기마다 이뤄지는 Periodic review가 있습니다.

### Continuous review
Continuous review에서는 다음 조건들이 있습니다.
1. Demand rate \lambda per year
2. Lead time = **0**, so stockout is not allowed.
3. Fixed cost **K** per order
4. Purchase cost **c** per unit
5. Holding cost **h** per unit and per year

이런 제약 사항 속에서
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc0Mzk5OTE5MSwxOTU4ODU5NjU5LC01Mj
QyNDI1NCwtMTE5NzQ3OTE3NSw4MDkwNDI1ODEsMTU2NjIzNTQ4
OCwtNDg0MjUwMDMyLC0xMTM2NDE0Njk5LDgxMDk4MTA1NF19
-->