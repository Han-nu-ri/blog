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
재고를 보유하는 비용을 의미합니다. 물리적으로 공간을 차지하는 것 뿐만 아니라, 세금, 보험, 그리고 기회 비용까지 포함합니다. 종종 1년 단위로 제품의 가치의 비율로 표현됩니다.
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

## Continuous review: EOQ model
Economic Order Quantity(EOQ) Problem은 1년에 평균 비용을 최소화하기 위한 최적의 주문량을 정하는 문제입니다. 다음 제약 조건들이 있습니다.
1. Demand rate \lambda per year
2. Lead time = **0**, so stockout is not allowed.
3. Fixed cost **K** per order
4. Purchase cost **c** per unit
5. Holding cost **h** per unit and per year

위 조건들을 만족하는 최적의 IL은 자연스럽게 두 가지 속성들을 만족하게 됩니다.

>Zero-Inventory Ordering(ZIO): Lead time이 0이기 때문에, Inventory가 0이 될 때 주문하는 것이 Holding cost를 줄일 수 있습니다.
Constant order size: 최적의 주문량 Q를 찾았다면, 다음 주문 시에도 최적의 주문량은 같은 Q가 됩니다.

수요량은 일정하므로, 주문 주기는 아래와 같이 나타낼 수 있습니다.
$$
T={Q \over \lambda}
$$
### Optimal Q*
그럼 최적의 주문량 Q를 찾기 위해 우리가 고려해야 하는 비용은 무엇일까요? H, S, F, P 중 Lead time이 0이기 때문에 Stockout cost은 고려 대상이 아닙니다. 또한 Purchase cost은 매년 발생하는 수요량에 정확히 맞춰야 하기 때문에, Q를 어떻게 하든 정해져 있습니다. 그러므로 이 문제에서 전체 비용은 Total cost = Fixed cost + Holding cost 와 같이 표현할 수 있습니다.
Fixed cost는 K에, 1년에 주문하는 빈도를 곱하면 됩니다. 따라서 K / T가 됩니다. 또한 평균 재고량은 Q/2이므로, 평균 Holding cost는 h*Q/2가 됩니다.  따라서 Total cost g(Q)는 아래와 같습니다.
$$
g(Q)={K \over T} + {hQ \over 2}
$$
Q에 대한 두 cost와 total cost를 그려보면, g(Q)를 최소화하는 Q*은, K/T와 hQ/2 두 비용이 만나는 지점임을 알 수 있습니다.
$$
{K\lambda \over Q^*} = {hQ^* \over 2} \\
Q^* = \sqrt{2K\lambda \over h}
$$
또한 g(Q*)는 아래와 같습니다.
$$
g(Q)={K \over T^*} + {hQ^* \over 2} \\
={K\lambda \over Q^*} + {hQ^* \over 2} \\
=\sqrt {2K\lambda h}
$$
### EOQ Sensitivity
현실적으로, 최적의 Q*를 정확히 주문하기는 쉽지 않습니다. Q*을 주문했을 때의 최적의 비용 대비 Q를 주문했을 때 비용이 변하는 정도를 EOQ Sensitivity라고 합니다.
EOQ Sensitivity
$$
{g(Q) \over g(Q^*)} = \cdots = {1 \over 2}({Q^* \over Q} + {Q \over Q^*})
$$
아래는 EOQ Sensitivity의 그래프입니다. 1을 기준으로 오른쪽 이동할 때의 경사가 왼쪽 이동할 때 보다 더 큽니다. 덜 주문하는 것보다는 더 주문하는 것이 낫다는 것이지요.
또한 최적의 Q 근방에서는 비용이 생각보다 별로 증가하지 않습니다.
![image](https://user-images.githubusercontent.com/11609881/112757047-e62e1680-9022-11eb-9c33-ffff85d929bc.png)
### Lead time이 0이 아닌 고정 상수인 경우
Lead Time이 0이  아니라  고정  상수 L이라고  해도, 별로  복잡하질게  없습니다. 주문해야 하는 시점 측면에서는  재고가 떨어질 시점 보다 L 전에  미리  주문만 하면 되니깐요.  또한 재고의 양  측면에서는 L * lambda가  남았을  때  주문하면  됩니다. L * lambda를 reorder point r 이라고 합니다.
### Power-of-Two Policies
하나의 Supplier와 여러 Retailer가 있다고 해보죠. 이 Retailer들이 모두 최적의 T*를 맞추기는 어렵습니다. 따라서 Supplier가 Base Period를 정하고 2의 지수승과 Base Period의 곱의 형태로 주문을 해달라고 정책을 정할 수 있습니다. 이렇게만 정책을 정해도 비용을 계산하기가 쉬워집니다.
$$
T=T_B2^k. k = \cdots -2, -1, 0, 1, 2, 3, ...
$$
### Error bound of Power-of-Two Policies
Power-of-Two 정책을 따를 때의 최적의 비용과 따르지 않을 때의 최적의 비용은 최대 얼마나 차이가 날까요?
먼저 Q에 대한 비용의 함수는 T로 표현할 수 있습니다.
$$
g(Q)={K\lambda \over Q}+{hQ \over 2} \\
f(T)={K \over T}+{h \lambda T \over 2}
$$
Power-of-Two 정책을 따를 때 최적의 비용을 만드는 optimal k라고 하면 다음 두 부등식을 만족하게 됩니다.
$$
f(T_B2^k) \le f(T_B2^{k-1}) \cdots (1) \\
f(T_B2^k) \le f(T_B2^{k+1}) \cdots (2) \\
$$
(1) 부등식을 전개하면 아래 부등식을 얻을 수 있고,
$$
T_B2^k \le \sqrt {2} T^*
$$
(2) 부등식을 전개하면 아래 부등식을 얻을 수 있습니다.
$$
{1 \over \sqrt {2}} T^* \le T_B2^k 
$$
Power-of-Two 정책을 따르는 Optimal T가 T*에 가장 멀리 떨어진 최악의 두 상황에서의 EOQ Sensitivity를 계산하면,
$$
{f(T_B2^k) \over f(T^*)} = {1 \over 2}({T_B2^k \over T^*}+{T^* \over T_B2^k}) \\
= {3 \over 2 \sqrt 2}
$$
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2NjcxMzYwMDYsLTgyNTYyODgzNCw0NT
kwNTgzMjIsODQzNzk0MzYxLDE4NDM0MjQzNSwxNTM5MzUwNjQx
LDE0Mjg0NTkyMzgsLTIwNjE1MzA4OTksLTIwNzU3NzcyMzUsLT
YwOTA1MDU2MSw5Nzc2MTE0MDMsMTI0MjEzMDgzOCwtODU3NzI5
NTkxLC0xMTUwOTc1MzQxLC0xMTkxMjAwNDYyLC0xMTc2ODU5NT
AsMTM3NDEyMjU3OSwtNDQzMTQzODM1LC0xNDE2MDQ4NDMsLTI0
MDYzNjQ3M119
-->