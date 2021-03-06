# [Paper review] From Here to Autonomy: Lessons Learned From Human-Automation Research

Endsley MR. From Here to Autonomy: Lessons Learned From Human–Automation Research. Human Factors. 2017;59(1):5-27.  논문을 읽고 정리한 게시물입니다.
## Introduction
자율 능력은 필요한 노동력을 줄이고, 인간의 능력을 확장하고 인간의 안전을 향상 시킬 수 있습니다. 대부분의 자율 시스템은 자율 시스템을 관리자들과의 interaction이 잘 이뤄져야 효과적인데요. 따라서 사람의 간섭을 줄이되, 꼭 필요한 시점에서 interaction이 이뤄지도록 하는 연구가 진행되어야만 합니다.

본 논문에서는 아래 내용을 다룹니다.
1. HASO(Human-Autonomy System Oversight)라는 모델을 통해, 자율 시스템의 성격과 인간의 인지 기능, 그리고 성공적인 자율 시스템 관리를 위한 능력 간의 관계를 묘사합니다.
2. HASO 모델은 자율화 레벨(Level Of Automation, LOA), Adaptive Automation (AA), 컨트롤의 단위 (Granularity Of Control, GOC)를 포함합니다.
3. 자율 그리고 부분자율 시스템을 디자인하는 가이드라인을 제공합니다.

## OOTL of Situation Awareness
OOTL은 Out-Of-The-Loop의 약자로, 사람이 어떤 환경이 변하거나 새로운 정보가 생겼을 때 일상적으로 쓰는 용어입니다. 현재 어떤 일이 발생하고 있는지 모르는 경우 OOTL이라고 합니다.
> Person1: Hey i didn't know steve irwin died
Person2: dude you're ootl

사람은 자율 시스템을 관리할 때, Situation Awareness(SA)가 약하기 때문에 문제를 효과적으로 해결하기 위한 간섭을 하기 까지 시간이 오래 걸립니다. 왜 자율 시스템 관리할 때 Low SA가 될까요? 본 논문에서는 세가지 이유를 말합니다.
1. 낮은 수준의 투명성
많은 자율 시스템은 어떤 일이 발생하고 있는지 필요한 정보들이나, 피드백들을 제공하고 있지 않습니다.
2. 자율시스템에 대한 믿음
자율 시스템에 대한 믿음이 커서, 자율 시스템은 모니터링하는데 노력을 덜 들이게 됩니다.
3. 수동적인 인지적 관여
인지적 관여는 학습자가 자신의 지식과 기술을 이해하고 사용하고 창조하려는 전략적인 노력입니다.  자율 시스템의 특성 상, 인지적 관여를 작게 하게 됩니다. 그래서 중요한 정보를 이해하고 활용하는데 적극적인 인지 관여를 하지 않게 됩니다.
## HASO (Human-Autonomy System Oversight)
![image](https://user-images.githubusercontent.com/11609881/113098195-24018980-9233-11eb-9467-d573ad36c5b2.png)
Figure 1은 HASO 모델 다이어그램입니다.
1. 자율화 신뢰성이 올라가게 되면 사람의 Attention 할당이 줄어들게 됩니다.
2. 자율화에 Interface는 Situation Awareness에 영향을 줍니다.
3. 자율화와 교류하는 틀, 체계 (Automation Interaction Paradigm)는 SA, 자율화 관리와 Interaction 능력에 영향을 줍니다.

Automation Interface는 SA에 영향을 주므로 효과적인 Interface가 중요한데요, 본 논문에서는 Operator의 이해를 증가 시킬 수 있는 가이드라인들을 제공합니다. 이 가이드라인들의 전반적인 목적은 시스템 투명성과 이해력, 그리고 예지력을 높이기 위함에 있습니다.

## Toward fully autonomous systems: research needs
### Effective automation interface for OOTL problem
자율화의 능력이 증가함에 따라, 사람의 간섭의 빈도가 줄어들 가능성이 있습니다. 하지만 OOTL과 같은 문제를 해결하기 위해서, 자율화 시스템은 사람과 자율 시스템 간 효과적인 Interface가 필요합니다.
### Learning system consistency
operator들 간 자율 시스템에 대한 이해가 차이가 있을 수 있기 때문에 이에 따른 혼란이 야기될 수 있습니다. 또한 자율 시스템은 시간이 흐를수록 새로운 것을 배우는데, 이것들을 operator들에게 전달할 수 있는 방법을 개발해야 합니다.
### Transparency of Learning Systems
자율 시스템이 Deep Learning과 같은 모델로 무언가를 배울 때, 모델의 특성 상 operator들이 어떻게 배운 것인지 투명하지가 않습니다. 그렇기 때문에operator들이 자율 시스템의 이해력과 예지력을 높이기 위해 투명한 Interface를 만드는 것이 중요합니다.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ5NTgwMzI0NCwtMTE3NzQ5MDg3Myw0Nj
E3ODM4NDgsMTA1MTE2MTk4Miw1OTMyNzM4NjgsLTE5NzEzNDQw
ODQsMTI5NTE5MDM5NV19
-->