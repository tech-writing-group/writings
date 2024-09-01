---
slug: state-and-presentation
title: state and presentation
authors: yejun
unlisted: true
---

# 02. Presentation / State 동기화 문제: 프론트엔드와 백엔드의 경계 정하기

## Background / Problem

- Presentation Layer
  - 기본적으로 서비스와 사람이 소통하려면 Interface가 필요해진다.
  - 이때 사용하는 것이 Presentation Layer임
- State (Business Logic) Layer
  - 서비스는 입력 출력만 필요한 계산기가 아닌 이상에야 어떤 상태를 가지고 있기 마련임.
  - 현재 상태를 State라고 하며, 상태가 변화할 수 있는 관련 규칙을 Business Logic이라고 함
  - 보통 서비스는 제공하는 자원 (실제 물리적, 금전적 가치를 지녔거나, 정보로써의 가치, 서비스 이용권, 다른 사람의 정보 등)이 있다.
  - 이 자원과 규칙을 관리하는 것이 State Layer임
- State 관리 전략
  - 백업: 편의상 사용자의 정보를 원격에 백업처럼 저장하는 경우가 있음
  - 최신 상태와 규칙 유지
    - State와 Business Logic을 한 장소에서 최신의 올바른 상태로 유지하고 싶은 경우가 있음
    - 이 때, 보여주기 위한 부분과 실제로 정보를 저장하는 부분이 분리되곤 함
    - 예를 들어, 게시판의 글 목록은 다른 사람에게도 보여줘야 하므로, 이를 저장하는 부분 (원격 서버)와 보여주는 부분(클라이언트)가 분리됨

## Solutions

- Pure Client Side: 클라이언트에서 State 관리
- Thin Client / Pure SSR: 서버에서 State 관리
- Replicated State (CSR) / Original State in Server: Client Side에서 State 관리
- Hybrid (SSR + CSR): Hydration이라는 과정을 통해 Interactivity는 Client로 구현
