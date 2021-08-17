---
layout: post
current: post
cover:  assets/built/images/author-logo.png
navigation: True
title: 블록체인 (1)
date: 2021-08-17 15:20:00
tags: [blockchain]
class: post-template
subclass: 'post tag-algorithm'
author: pathfinder357
---
{% include blockchain-table-of-contents.html %}

### 비트코인 네트워크의 개요
***

#### 비트코인의 탄생

중앙집권적인 정부나 기업이 개인의 프라이버시를 보장해 주지 못하므로 암호 기술을 이용해 스스로 프라이버시를 보호하기 위해 탄생

사토시 나가모토라는 익명의 저자가 쓴 한편의 논문에서 시작 됫으며 이논문은 탈중앙화된 화폐시스템을 제안

이 논문의 주요 제안 내용은 이와 같다

* 중앙통제시스템이 없는 탈중앙화된 p2p 네트워크다.
* 이전에 해결하지 못한 *이중 지급 문제*를 해결했다.
* 거래원장은 모든 참여자에게 공개된다.
* 참여자들은 거래 원장을 조회할수 있고, 규칙에 맞게 작성됐는지 검증할수 있다.
* 블록체인 데이터를 신뢰할수있는 합의시스템(PoW: proof of work)이 있다.

이중지금문제란 어떤 계좌의 잔액이 100원만 남았을때 A에게 100원을 송금하고 B에게도 100원을 송금하는것

중앙통제시스템에서 관리한다면 A에게 100원을 송금하자마자 해당 계좌의 잔액은 비었으므로 B에게 송금이 불가하지만
중앙통제시스템이 없는 p2p 분산 네트워크는 관리 주체가 없기 때문에 이 문제 해결이 어려움

하지만 이논문을 바탕으로 여러개발자들이 비트코인 논문 제안 내용을 연구하여 비트코인 네트워크를 구현


#### 암호화폐의 주요 이슈

p2p 분산 시스템은 근본적으로 데이터의 일관성, 네트워크의 가용성, 분할내성을 동시에 만족할수 없다.

이러한 문제로 인해 기존에 제안된 암호화폐는 묵살 되었고 실생활에 통용될수 없었고 이를 해결하기 위해서는
다음과 같은 문제점들이 해결되어야한다.

* 내가 받은 암호화폐가 진본인지 위조인지 확인가능한가?
* 내가 받은 암호화폐가 이중 지급 된것이 아닌지 확인가능한가?
* 내가 보유한 암호화폐의 소유권을 다른 사용자가 인정가능한가?

위 문제에 대한 기본적 해결책은 중앙통제 시스템이 검증하고 보관하는것이지만, 중앙화폐시스템은 시스템에 대한 공격을 받으면 산하에 있는 정보가 누출된다는 취약점이 있다.

사토시 나카모토는 기존 암호화폐시스템들을 발전시켜 완전히 탈중앙화된 개념을 사용하면서도 위 문제를 해결했다.

**** 비트코인은 기존 암호화페 아이디어 종합체

* Ecash schema: p2p 네트워크에서 자신이 암호화폐의 소유자임을 '증명' 하고, 다른 사람들이 '검증' 하기 위해 전자 서명을 사용
* State machine replication: 각 노드간 데이터 일관성을 보장하기 위한 시스템이다. State는 블록체인의 상태이며 시간에 따라 변한다 *(S1 -> S2 -> S3 ->..)*. 시간에 따른 상태 변화는 모든 노드가 동일하게 관리해야 한다.
* Consensus mechanics: 개별 거래 원장에서 부터 블록체인의 상태까지 모든 과정에 대해 각노드들이 동의할수있는 합의 규칙이다. 이규칙에 의해 전체 상태가 일관되게 유지된다.
* HashCash computational puzzle: 합의 규칙에 따라 수학적 퍼즐이 제시되고, 채굴자들은 경쟁적으로 이문제를 푼다. 경쟁에서 이긴 채굴자가 블록을 생성할 권한을 받는다. 이 과정을 통해 신규 암호화화폐가 발행되고, 상태 변화의 일관성이 유지된다.
* peer-to-peer: 서버- 클라이언트 구조가 아닌 p2p 구조로 탈중앙화를 이뤘다.



