---
title: "동태적 일반균형 시스템 (GES)"
author: "Jinseok Kim"
format:
  html:
    toc: true
    toc-depth: 4
    number-sections: true
    theme: cosmo
    code-fold: false
    html-math-method: mathjax
    self-contained: true
    smooth-scroll: true
    embed-resources: true
editor: visual
---

# Introduction

- 이 문서는 일반균형 시스템(GES)이 어떻게 작동하는지를 설명한다.

- GES는 중세 세계의 거시경제를 몰입감 있고 내적으로 일관된 방식으로 시뮬레이션하도록 설계되었다.

- 개념적으로 GES는 왈라스식 일반균형 체계의 직관을 모사하는 규칙 기반 구현이다. 완전히 형식화된 균형모형을 직접 푸는 대신, 경제 내에서 자원, 유인, 가격, 그리고 사회경제적 선택이 어떻게 상호작용하는지를 순차적으로 근사한다.

- GES는 시장 배분뿐 아니라 가구의 사회경제적 선택도 결정하며, 여기에는 출산, 교육, 노동공급, 직업선택, 승급, 강등, 투자 등이 포함된다.

- GES에서는 핵심 경제 결과의 대부분이 내생적으로 결정된다. 생산, 소비, 시장가격, 출산, 교육, 직업선택, 승급과 강등, 그리고 투자는 모두 시스템 내부의 규칙 기반 상호작용을 통해 결정된다. 반면 구조적 파라미터와 메뉴 비용, 운송비용, 운송시간과 같은 일부 마찰 요소는 외생적으로 주어진다.

- GES의 자원은 크게 유형재와 무형재의 두 범주로 나뉜다.

    - 유형재는 저장 가능하며 시간이 지나도 재고(stock)로 축적된다. 이러한 재고 보유 기능은 시장 마찰을 흡수하고 기간 간 경제조정을 완화하는 데 도움을 준다.

    - 무형재는 저장할 수 없으며 공급된 기간 내에 소비되어야 한다.

    - 소비재, 사치재, 내구재를 포함한 보다 세부적인 자원 분류는 이후 절에서 설명한다.

    - 유형재와 그에 연관된 경제행위 역시 이후 절에서 설명한다.

- GES는 미리 정의된 각 시간 간격마다 다음과 같은 순서로 진행된다.

    0) 기대형성

    1) 생산

    2) 공급

    3) 소비

    4) 사회경제적 선택

    5) 투자

- 기대형성 단계에서 경제주체들은 이전 기간의 정보, 특히 관측된 가격과 수요를 바탕으로 미래 시장상황에 대한 규칙 기반 기대를 형성한다. 이러한 기대는 이후 생산과 공급 결정을 이끈다.

- GES의 소비는 Stone-Geary 논리를 따른다. 사회적 신분 집단은 먼저 생존에 필요한 소비, 특히 생존에 필수적인 유형재 소비에 자원을 배분한다. 그 후 남은 자원은 무형재와 교육, 출산, 직업 이동성과 같은 보다 광범위한 사회경제적 선택에 배분된다.

- 사회경제적 선택은 소비에 기반한 수요를 통해 실현된다. 교육, 출산, 직업 전환에 대한 수요는 소비 단계에서 형성되며, 실현된 수요는 이후 인적자본, 인구, 그리고 사회적 신분 간 승급·강등과 같은 상태변수의 갱신으로 이어진다.

- GES는 가장 작은 지리 단위인 프로빈스 단위에서 작동한다.

    - 보다 상위의 지리적 위계는 프로빈스, 리전, 서브컨티넨트, 컨티넨트로 구성된다.

    - 이러한 지리적 위계와 프로빈스와의 관계는 이후 절에서 설명한다.

- 시장은 기본적으로 프로빈스 단위로 조직되지만, 완전히 고립되어 있지는 않다.

    - 상인은 프로빈스 내부에서 공급능력을 제공하며, 시장 공급은 그 능력을 초과할 수 없다.

    - 시간이 지나면서 상인들은 같은 리전 내 다른 프로빈스 시장에 대한 정보를 획득할 수 있다.

    - 상인들은 이러한 정보를 바탕으로 정보획득 비용, 운송시간, 운송비용을 고려하여 프로빈스 시장에 공급할지 더 넓은 리전 시장에 공급할지를 선택한다.

    - 따라서 리전 간 거래는 처음부터 완전히 주어지는 것이 아니라 점진적이고 내생적으로 형성된다.

- GES는 각 경제주체를 개별적으로 시뮬레이션하지 않는다. 대신 사회적 신분(social estate)에 따라 정의된 보다 넓은 범주의 집단을 모델링한다.

    0) 비자유민

    1) 평민

    2) 장인

    3) 상인

    4) 성직자

    5) 군인

    6) 예인

    7) 유목민

- 사회적 신분들은 공통의 선호구조를 공유하지만, 생산 접근성, 자산구성, 그리고 직업 이동 자격에서는 차이를 가진다.

    - 소비와 생산은 각 개인 수준이 아니라 각 사회적 신분 수준에서 결정된다.

    - 각 사회적 신분은 집계된 금융자산, 인적자본, 물적자본, 유형재 재고를 보유하며, 이러한 요소들이 해당 신분의 생산과 소비 결과를 함께 결정한다.

    - 사회적 신분별로 진입 가능한 직업 집합, 해당 직업에 머무를 수 있는 조건, 승급과 강등을 제약하는 조건 또한 서로 다르다.

    - 직업 이동 자격은 교육 선택과 누적 인적자본과 같은 내생적 조건뿐 아니라 제도와 인구구조와 같은 외생적 조건에도 부분적으로 의존한다.

    - 이러한 자격 조건은 시간에 따라 변화하므로, 특정 신분에 진입하는 난이도 역시 경제가 발전함에 따라 내생적으로 달라질 수 있다.

- GES는 기준 시장구조로 완전경쟁을 가정한다. 이 가정 아래에서 일정 기간 충분한 소득을 창출하지 못하면 시간이 지나면서 강등이나 직업 변경이 발생할 수 있다.

- GES에서 투자는 주로 생산 지향적 경제활동을 의미하며, 생산시설 건설, 자본축적, 그리고 미래 생산에 필요한 재료 조달을 포함한다.

- 각 사회적 신분의 경제적 역할과 행동 특성은 이후 절에서 논의한다.

# Taxonomy

## Time

- GES가 작동하는 각 시간 간격은 $t$로 표기하며, $t \in \mathbb{Z}_{+}$이다.

## Geographic Unit

- 각 지리 단위인 프로빈스, 리전, 서브컨티넨트, 컨티넨트는 각각 $G = \{p, r, s, c \}$로 표기한다.
- 경제주체가 속한 지리 단위는 $\{ p_0, r_0, s_0, c_0 \}$와 같이 $G_0$로 표기한다.

## Social Estate

- 각 경제주체 $i$의 사회적 신분은 $e$로 표기한다.

# GES Framework

- 이 절은 왜 GES가 필요한지, 어떻게 작동하는지, 그리고 어떤 결과가 외부에서 주어지는 것이 아니라 시스템 내부에서 결정되는지를 설명함으로써 GES의 핵심 프레임워크를 소개한다.

- GES는 형식적인 왈라스식 일반균형 모형은 아니지만, 규칙 기반이면서 계산 가능성이 높은 구조를 통해 유사한 경제적 직관을 반영하도록 설계되었다.

## Scope and Modeling Philosophy

### Design Objective: Depth Without Micromanagement

- GES의 일차적 목표는 의미 있는 깊이를 가지되, 과도한 미시관리로 이어지지 않을 만큼 추상화된 동태적 경제 시스템을 제공하는 것이다.

- 많은 경제 시뮬레이션 시스템은 수많은 개별 경제주체와 그들의 세부 의사결정을 직접 모델링함으로써 복잡성을 구현한다. 이러한 방식은 풍부한 국지적 행동을 만들어낼 수 있지만, 동시에 플레이어의 인지부담을 높이고 불필요한 관리 부담을 유발한다.

- GES는 대신 미시적 개연성을 유지하면서 거시적 수준의 통제를 제공하는 것을 목표로 한다. 플레이어는 모든 가구와 거래를 일일이 관리하는 사무원이 아니라, 사회의 더 큰 방향을 형성하는 통치자, 기획자, 혹은 후원자처럼 느껴져야 한다.

- 이러한 설계 선택은 장기적인 플레이 가능성에 중요하다. 시스템이 지나치게 정적이면 얕아지고, 지나치게 세밀하면 피로해진다. GES는 그 중간지대를 지향한다. 즉 구조적으로는 풍부하고, 행동적으로는 동태적이며, 전략적 의사결정 수준에서 관리 가능한 시스템이다.

### Gameplay Objective: Immersion Through Social and Economic Change

- GES는 경제발전이 게임 세계의 삶 속에서 가시적으로 드러나도록 설계되었다.

- 성공적인 경제 시스템은 배경에서 숫자만 바꾸는 데 그쳐서는 안 된다. 사람들의 생활, 노동, 소비, 그리고 사회적 이동 방식에서 식별 가능한 변화를 만들어내야 한다.

- 프로빈스가 더 번영해질수록 사회적 신분들은 플레이어가 읽어낼 수 있는 방식으로 행동을 바꾸어야 한다. 식단이 개선될 수 있고, 세련된 재화와 서비스에 대한 수요가 확대될 수 있으며, 교육투자가 증가하고, 새로운 형태의 직업 이동성이 등장할 수 있다.

- 이러한 변화는 몰입감의 핵심이다. 플레이어는 자신의 정책, 투자, 장기적 계획이 자신의 영지 내 일상생활의 구조를 실질적으로 변화시켰다는 점을 관찰할 수 있어야 한다.

### Systems Objective: Dynamic but Coherent Behavior

- GES는 경제적·사회적 변화를 만들어내되, 혼란스럽거나 해석 불가능한 시스템이 되지 않도록 설계되었다.

- 게임 설계의 관점에서, 좋은 관리 시스템은 흥미를 유지할 만큼 충분히 동태적이어야 하지만, 동시에 이해 가능할 만큼 일관적이어야 한다. 시스템이 지나치게 경직되면 반복 플레이 가치가 줄어든다. 반대로 지나치게 불안정하거나 불투명하면 공정하게 느껴지지 않으며 플레이어가 학습하기 어려워진다.

- 따라서 GES는 구조화된 내생적 행동을 강조한다. 가격, 생산, 소비, 그리고 사회경제적 선택은 시간에 따라 변화하지만, 그러한 변화는 임의적이거나 순전히 무작위적인 방식이 아니라 투명한 규칙 기반 메커니즘을 통해 이루어진다.

- 이러한 동태성과 일관성의 균형은 전략적 계획 가능성과 플레이어의 시스템 신뢰를 동시에 뒷받침하기 위한 것이다.

### Technical Objective: Pseudo-Walrasian Approximation for Performance

- GES는 왈라스식 일반균형 시스템의 논리에서 영감을 받았지만, 완전히 형식적인 균형모형을 직접 푸는 방식으로 구현되지는 않는다.

- 원론적으로 매우 세밀한 시장 시뮬레이션은 각 가구, 노동자, 생산자를 개별적으로 모델링하려 할 수 있다. 그러나 실제로 그러한 접근은 계산비용이 크고, 밸런싱이 어렵고, 이 프로젝트가 지향하는 게임 경험을 위해 반드시 필요한 것도 아니다.

- 따라서 GES는 준-왈라스식 구조를 채택한다. 이는 개별 경제주체 수준이 아니라 사회적 신분 수준에서 작동하면서도, 분권적 선택, 시장 상호작용, 자원 재배분의 핵심 경제적 함의를 근사한다.

- 이 방식은 성능, 튜닝, 구현 측면에서 시스템을 훨씬 더 다루기 쉽게 만들면서도, 내생적 시장조정이라는 보다 큰 직관은 유지한다.

### Modeling Unit: Estate-Level Aggregation

- GES는 모든 경제주체를 개별적으로 시뮬레이션하지 않는다. 대신 경제주체를 더 넓은 사회적 신분 집단으로 집계하고, 그 수준에서 의사결정을 모델링한다.

- 이러한 집계는 단순한 기술적 편의가 아니다. 그것은 동시에 하나의 설계 선택이기도 하다. 거시관리 게임의 맥락에서 플레이어는 각 개인의 삶을 최적화하는 것이 아니라, 전체 집단이 번영하고, 정체하고, 전문화되거나, 쇠퇴하는 조건을 통치해야 한다.

- 사회적 신분 수준의 모델링은 완전한 개별 주체 시뮬레이션의 비용을 치르지 않으면서도 분배구조와 사회구조를 유지할 수 있게 해준다.

- 또한 승급, 강등, 교육, 출산, 직업 이동을 시간이 지나며 각 신분의 구성과 역량이 변화하는 과정으로 추적할 수 있기 때문에, 내생적 사회변화를 표현하기도 더 쉽다.

### Historical Objective: A World in Transition

- GES는 대략적으로 중세 전성기부터 계몽주의 시대에 이르는 장기적 전환에 의해 규정되는 세계관을 위해 설계되었다.

- 이러한 배경에서는 정적인 경제모형으로는 충분하지 않다. 시스템은 문해력 상승, 직업 장벽의 변화, 교역망의 확장, 그리고 소비·생산 패턴의 변화와 같은 점진적인 구조변화를 표현할 수 있어야 한다.

- 따라서 내생적 사회경제적 선택은 부가적인 층위가 아니다. 그것은 게임 세계가 역사적 발전과 플레이어 개입을 반영하는 핵심 메커니즘 중 하나이다.

- 플레이어는 단기적인 경제변동뿐 아니라, 누적된 투자, 제도적 구조, 시장 상호작용으로부터 발생하는 느린 문명적 변화를 관찰할 수 있어야 한다.

### Player Agency: Why Endogenous SES Choice Matters

- GES의 핵심 설계 목표 중 하나는 눈에 보이는 사회적 반응을 통해 플레이어의 행위감을 강화하는 것이다.

- 사회적 신분이 행동적으로 고정되어 있다면, 경제성장은 단지 산출량 수치의 변화에 불과해진다. 반대로 교육, 출산, 직업 이동성, 소비 패턴이 경제여건에 따라 내생적으로 반응한다면, 플레이어는 자신의 결정이 사회 자체를 재구성했다는 것을 볼 수 있다.

- 이는 거시관리 게임에서 특히 중요하다. 플레이어의 역할은 각 가구를 직접 지휘하는 것이 아니라, 가구와 신분집단이 스스로 행동을 바꾸도록 만드는 조건을 조성하는 데 있다.

- 이런 의미에서 내생적 사회경제적 선택은 경제 메커니즘일 뿐 아니라, 플레이어 자기효능감의 핵심 피드백 경로이기도 하다.

### Summary of the Design Philosophy

- GES는 단순한 하나의 원칙 위에 구축되어 있다. 시스템은 의미 있는 구조변화를 만들어낼 만큼 충분히 깊어야 하지만, 동시에 가독성, 성능, 재미를 유지할 만큼 충분히 추상적이어야 한다.

- 따라서 GES는 사회적 신분 수준의 집계, 규칙 기반의 내생적 선택, 그리고 준-왈라스식 시장 논리를 결합하여, 플레이어에게 과도한 미시관리를 강요하지 않으면서 살아 있는 거시경제를 시뮬레이션한다.

- 그 결과 경제관리가 전략적으로 느껴지고, 사회변화는 노력의 결과로 느껴지며, 장기적 발전은 몰입감 있으면서도 플레이어의 행동에 반응하는 시스템이 되는 것을 목표로 한다.

## Procedure

- GES는 $t$로 지수화되는 이산시간 체계에서 작동한다.

- 각 기간 $t$ 내에서 시스템은 고정된 절차의 순서에 따라 실행된다. 주요한 경제조정은 모두 해당 기간 안에서 계산된다.

- 각 절차는 동일한 세 부분 구조로 문서화된다.

    1) 철학(Philosophy)

    2) 입력(Input)

    3) 출력(Output)

- 철학은 왜 해당 절차가 필요한지, 그리고 그것이 어떤 현실적 혹은 이론적 메커니즘을 구현하는지를 설명한다.

- 입력은 해당 절차에 필요한 변수와 정보를 명시한다.

- 출력은 해당 절차가 산출하는 변수, 결정, 혹은 상태변화가 무엇인지를 명시한다.

### Expectation Formation

#### Philosophy

- GES는 동태적 시스템이므로 가격과 수량 역시 고정되어 있지 않고 시간에 따라 조정되어야 한다.

- 따라서 경제주체는 이전에 관측된 시장조건에 기반한 기대를 형성하지 않고서는 생산과 공급 결정을 내릴 수 없다.

- 이런 이유로 기대형성은 각 기간의 첫 단계가 된다.

- 이 절차에서 모든 경제주체는 자신이 속한 프로빈스 내부의 상황에 대해서는 완전한 정보를 가진다고 가정한다.

- 반면 다른 프로빈스와 리전 시장에 대한 정보는 불완전하며, 이를 획득하기 위해서는 금전적 비용과 시간 비용이 모두 필요하다.

- 이 절차는 경제행동이 지역지식, 제한된 정보, 점진적으로 확장되는 시장 인식에 반응하도록 만든다는 점에서 몰입감에 중요하다.

- 동시에 이 규칙은 지나치게 복잡해서는 안 된다. 기대형성이 불투명하거나 불규칙한 논리에 의해 이루어지면 시스템은 이해하기 어려워진다. 반대로 기대형성 체계가 지나치게 계산 집약적이면, 게임플레이 개선 없이 성능만 악화시킨다.

- 플레이어는 기대형성에 직접 개입하지 않기 때문에, 이 규칙은 단순하고, 읽기 쉬우며, 직관적으로 예측 가능해야 한다.

- 이런 이유로 기대형성은 GES에서 가장 중요한 절차 중 하나이다. 이는 시뮬레이션의 내적 일관성과 플레이어의 경제 시스템에 대한 신뢰 모두에 강한 영향을 미친다.

#### Input

- 수요 스케줄 ($DS_{t-1,p,r}$)

    - $DS_{t-1,p,r}$는 기간 $t-1$ 동안 리전 $r$ 내 프로빈스 $p$에서 이전에 실현된 총수요를 의미한다.

    - 이는 효용극대화 문제로부터 도출된 수요를 바탕으로 하며, 이전 기간의 소비 단계 이후 기록된다.

    - 현재 기간의 수요는 절차상 나중에 실현되는 변수들에 의존하므로, 기대형성 단계에서는 동시점 수요가 아니라 시차가 있는 수요 정보를 사용해야 한다.

- 순가용소득 ($NAI_{t-1,p}^{e}$)

    - $NAI_{t-1,p}^{e}$는 프로빈스 $p$에서 사회적 신분 $e$가 세금과 생산 관련 비용을 반영한 이후 최종 배분에 사용할 수 있는 총소득을 의미한다.

    - 이는 소비와 사회경제적 선택에 사용할 수 있는 실질적 지출여력을 나타낸다.

    - 현재 기간에서는 기대형성 단계 시점에 동시점 순가용소득이 아직 실현되지 않았으므로, 경제주체는 이전에 관측된 소득 조건에 의존하여 기대를 형성한다.

    - 이는 다음과 같이 정의된다.

\[
\begin{aligned}
\text{Net Available Income}_{t,p}^{e}
&= (\tau^{e}_{p})' N^{e} \\
\tau^{e}_{p}
&\equiv
\begin{pmatrix}
\text{Labor Tax}^{e} \\
\text{Commercial Tax}^{e} \\
\text{Capital Tax}^{e} \\
\text{Housing Tax}_{p}
\end{pmatrix} \\
N^{e}
&\equiv
\sum_{i \in e} n_i - \tilde{c}_i \\
n_i
&=
\begin{pmatrix}
\text{Labor Income} \\
\text{Commercial Income} \\
\text{Capital Dividend} \\
\text{Rent Income}
\end{pmatrix} \\
\tilde{c}_i
&=
\begin{pmatrix}
\text{Labor Cost} \\
\text{Commercial Cost} \\
\text{Capital Investment} \\
\text{Land Investment}
\end{pmatrix}
\end{aligned}
\]

- 시차가 있는 시장가격 ($P_{t-1,p,r}$)

    - 경제주체는 자신이 속한 프로빈스 내에서 이전에 실현된 지역가격을 관측한다.

    - 리전 가격 정보는 상인 활동이나 정보획득을 통해 발견된 경우가 아니면 부분적으로만 이용 가능하다.

- 시장 접근성 정보

    - 경제주체는 어떤 시장에 재화를 공급할지를 예상할 때, 현재 자신이 알고 있는 시장 집합을 사용한다.

    - 이러한 정보는 상인의 존재, 과거의 정보획득, 그리고 교역 연결성에 따라 달라진다.

#### Output

- 각 관련 시장에 대한 기대수요

- 재화별·시장별 기대수익성

- 사회적 신분별 계획 생산결정

- 프로빈스 시장 혹은 리전 시장과 같은 계획 공급 대상

- 생산 및 공급 단계로 전달되는 갱신된 기대 변수

### Investment

#### Philosophy

- 투자는 현재 기간의 생산능력을 준비하기 때문에 기간의 시작 부분에 위치한다.

- GES에서 투자는 주로 생산 지향적 활동을 의미하며, 여기에는 건물 건설, 자본축적, 재료 조달이 포함된다.

- 이 단계는 이후 생산이 이루어질 생산 조건을 결정한다.

#### Input

- 기존 물적자본 스톡

- 사회적 신분별 가용 금융자원

- 건설 및 생산과 관련된 기존 유형재 재고

- 이전 기간 혹은 현재 기간 초기에 형성된 기대수익성

#### Output

- 갱신된 생산능력

- 갱신된 물적자본 스톡

- 투자에 사용되어 감소한 금융자원 혹은 재료자원

### Production

#### Philosophy

- 생산은 사회적 신분 수준의 자산과 투입요소를 경제적 산출물로 전환한다.

- GES는 개인 수준이 아니라 사회적 신분 수준에서 작동하므로, 생산은 각 사회적 신분에 대해 집계된 활동으로 결정된다.

#### Input

- 물적자본

- 인적자본

- 금융자산

- 유형 투입재 재고

- 사회적 신분별 생산 접근성

#### Output

- 생산된 재화 수량

- 시장 배분 이전 단계의 갱신된 재고

- 중간 생산비용

### Supply

#### Philosophy

- 공급은 생산된 재화와 가용 재고를 접근 가능한 시장들에 배분한다.

- 이 단계는 생산물을 실제 시장에 제공 가능한 형태로 전환하며, 상인의 공급능력, 시장정보, 교역마찰을 함께 반영한다.

#### Input

- 생산된 산출물

- 기존 재고

- 상인의 공급능력

- 기대가격과 기대수익성

- 시장 접근성 정보

- 운송비용과 운송시간

#### Output

- 프로빈스 시장으로 공급된 재화

- 접근 가능한 경우 리전 시장으로 공급된 재화

- 판매되지 않고 남은 재고

### Consumption

#### Philosophy

- 소비는 각 사회적 신분이 자신의 가용 자원을 생존소비, 기타 재화, 그리고 보다 넓은 사회경제적 수요에 어떻게 배분하는지를 결정한다.

- GES는 Stone-Geary 논리를 따르며, 특히 필수적인 유형재에 대한 생존소비가 먼저 충족된다.

#### Input

- 순가용소득

- 실현된 시장가격

- 시장에서 उपलब्ध한 재화

- 사회적 신분 수준의 선호 파라미터

- 필요한 경우 기존 가구 혹은 사회적 신분 차원의 유형재 재고

#### Output

- 실현된 유형재 소비

- 실현된 무형재 소비

- 해당되는 경우 충족되지 않은 수요

- 사회경제적 선택으로 이어지는 파생 수요

### Socio-economic Choice

#### Philosophy

- 사회경제적 선택은 사회적 신분의 수요 일부를 더 느리게 움직이는 구조적 결정으로 전환한다.

- 이러한 선택에는 교육, 출산, 직업 변경, 승급, 강등이 포함된다.

#### Input

- 생존소비 이후 남은 자원

- 실현된 교육, 출산, 직업 이동 수요

- 인적자본 수준

- 제도적·인구학적 제약

#### Output

- 인적자본의 갱신

- 인구의 갱신

- 승급 및 강등 결과

- 사회적 신분 구성의 변화

### State Update and Carry-over

#### Philosophy

- 마지막 단계는 다음 기간까지 지속되는 모든 상태변수를 갱신한다.

- 이 단계는 GES가 경로의존적이기 때문에 필요하다. 재고, 자본, 인적자본, 정보, 그리고 사회적 신분 구성은 모두 미래 결과에 영향을 미친다.

#### Input

- 실현된 생산, 공급, 소비, 사회경제적 선택 결과

- 남은 재고

- 자본 및 인구 관련 갱신

#### Output

- 기간 $t+1$의 초기 상태

- 다음 기간으로 이월되는 갱신된 재고

- 갱신된 사회적 신분 수준의 자산과 특성

- 갱신된 시장정보와 접근성

## What Remains Exogeneous

# Unit of Analysis

## Time period

## Geographic unit

## Social estate as the representative decision unit

# State Variables

## Estate-level state variables

## Province-level state variables

## Market-level state variables

# Resources

## Resource Taxonomy

### Tangible goods

### Non-tangible goods

### Consumable, luxurious, and durable classifications

## Economic Properties of Resources

### Storability

### Depreciation and decay

### Tradability

### Input-output role in production and consumption

## Resource Accounting

### Stock variables

### Flow variables

### Inventory update rules

# Social Estate

## Definition of Each Estate

### The Destitute

### The Commoners

### The Artisans

### The Merchants

### The Clergy

### The Soldiers

### The Virtuosos

### The Nomads

## Common Structure Across Estates

### Shared preference structure

### Shared budget logic

### Shared state-transition logic

## Estate Heterogeneity

### Productive access

### Asset composition

### Mobility eligibility

### Exposure to institutional constraints

# Market Structure and Price Formation

## Province Market

### Local market clearing logic

### Supply capacity constraint

### Inventory buffering

## Regional Market Integration

### Merchant information acquisition

### Choice between province market and region market

### Shipping time and shipping cost

### Conditions for inter-province trade

## Price Formation

### Expected price

### Realized price

### Menu cost and price adjustment rule

### Price persistence and friction

# Expectation Formation

## Information Set

### Lagged prices

### Lagged demand

### Market accessibility information

## Forecasting Rule

### Production forecast

### Supply destination forecast

### Expected profitability

## Frictions and Forecast Error

### Imperfect information

### Limited merchant discovery

### Inventory as shock absorber

# Consumer Choice

## Budget Constraint

### Financial assets

### Tangible stock holdings

### Market prices

## Stone-Geary Consumption Problem

### Subsistence bundle

### Residual discretionary demand

### Estate-level aggregate demand

## Non-Tangible and SES Demand

### Education demand

### Fertility demand

### Occupation mobility demand

### Service and art demand

## Consumption Realization

### Demand under inventory constraints

### Demand under price adjustment

### Unmet demand and carry-over effects

# Producer Choice

## Production Unit and Technology

### Estate-level production

### Inputs: financial, human, physical, and tangible stock

### Baseline production function

## Production Allocation

### What to produce

### How much to produce

### Input acquisition

## Supply Decision

### Provincial supply

### Regional supply

### Capacity limits and merchant mediation

# Socio-economic Choice

## Education

### Demand formation

### Human capital update

### Threshold and qualification effects

## Fertility

### Demand formation

### Population update

### Estate-specific fertility response

## Occupation Choice and Mobility

### Promotion

### Demotion

### Occupation switching

### Endogenous qualification dynamics

# Investment

## Definition of Investment in GES

### Building construction

### Capital accumulation

### Material procurement

## Investment Decision Rule

### Expected return

### Financing condition

### Constraint by estate and province

## Capital Update

### Physical capital accumulation

### Depreciation

### Interaction with future production

# Transition Rules and Dynamic Update

## End-of-Period Update

### Asset update

### Inventory update

### Human capital update

### Population update

### Estate composition update

## Persistence and Path Dependence

### Stored goods

### Qualification accumulation

### Information accumulation
