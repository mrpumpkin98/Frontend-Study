# 자료구조와 알고리즘\_기초

## ✅ 데이터 구조와 알고리즘 개요

### 데이터 구조란?

- 데이터 구조는 컴퓨터 프로그램에서 데이터를 구성, 저장, 조작하기 위한 특수한 형식
- 데이터 구조의 종류 : 배열, 연결 리스트, 스택, 큐, 트리, 그래프, 해시 테이블 등

### 알고리즘이란?

- 알고리즘은 문제를 해결하거나 작업을 수행하기 윟나 단계별 절차 또는 프로세스
- 알고리즘은 데이터 구조를 조작하고 해당 데이터에 대한 검색, 정렬, 분석 등 다양한 작업을 수행

### 복잡도 분석이란?

- 복잡도 분석은 컴퓨터 과학에서 알고리즘과 데이터 구조의 효율성과 확장성을 분석하는 데 사용되는 기법
- 입력 데이터의 크기에 따라 계산에 필요한 시간과 공간을 측정하는 것
- 이 정보는 특정 알고리즘이나 구조의 성능 특성을 파악하고 주어진 문제에 적합한 솔류션을 선택하는 데 사용

### Big O 표기법이란?

- 입력 크기가 무한대에 가까워질 때 함수의 제한 동작을 설명하는 데 사용되는 수학적 표기법
- 일반적으로 함수의 성장률에 대한 상한으로 표현
- 계산을 실행하는데 필요한 시간이나 공간의 양에 대한 최악의 시나리오를 나타낸다.

## ✅ 배열이란?

- 배열은 메모리에 연속적인 데이터 블록으로 저장된 데이터 항목의 모음

### 연결 리스트란?

- 연결 리스트는 일련의 노드로 구성된 데이터구조로, 각 노드에는 데이터 값과 시퀀스의 다음 노드에 대한 참조가 포함되어 있다.
- 일반적으로 `큐`나 `스택`과 같이 지속적인 삽입 또는 삭제 작업이 필요한 애플리케이션에서 사용

### 스택이란?

- 스택은 요소 모음을 저장하는 데이터 구조로, 스택의 맨 위에서 요소가 추가되고 제거된다.
- 스택은 스택에 마지막으로 추가된 요소가 가장 먼저 제거된느 후입선출 원칙을 따른다.

### 큐란?

- 큐는 요소 모음을 저장하는 데이터 구조로, 요소는 큐의 뒤쪽에 추가되고 큐의 앞쪽에서 제거된다.
- 큐는 선입선출 원칙을 따르며, 이는 큐에 처음 추가된 요소가 가장 먼저 제거된다는 것을 의미한다.

### 트리란?

- 트리는 에지 또는 분기로 연결된 노드로 구성된 계층적 데이터 구조다.
- 트리는 시각화 및 조작하기 쉬운 방식으로 요소 간의 관계를 표현하는 데 사용된다.
- 머신러닝

### 그래프란?

- 그래프는 정점(노드)과 정점 쌍을 연결하는 에지의 집합이다.

### 해시 테이블이란?

- 해시 테이블은 해시 함수를 사용하여 키를 배열의 인덱스에 매핑함으로써 데이터에 빠르게 엑세스할 수 있도록 하는 데이터 구조

> **💡 요약**
> 결론적으로 자바스크립트는 방대한 데이터 구조와 알고리즘을 제공한다. 이러한 데이터 구조와 알고리즘을 결합하면 개발자에게 복잡하고 동적인 애플리케이션을 구축할 수 있는 강력한 도구 세트를 제공해준다.

## ✅ 왜 데이터 구조와 알고리즘을 공부해야 할까?

### 데이터 구조와 알고리즘이란?

- **데이터 구조 :** 프로그래밍에서 데이터를 구성, 저장 및 검색하는 방식 (데이터 구성 방식)
- **알고리즘 :** 정렬이나 검색과 같은 특정 잡업을 수행하는 데 도움이 되는 단계 (데이터 조작 방법)

### 왜 데이터 구조와 알고리즘을 공부해야 할까?

- 문제 해결 능력 향상
- 효율성 및 속도 향상
- 라이브러리 및 프레임워크에 대한 이해도 향상
- 코드 품질 향상

### 자바 스크립트의 가장 일반적인 데이터 구조와 알고리즘

#### [ 데이터 구조 ]

- **배열 :** 가장 단순한 데이터 구조
- **연결 리스트 :** 배열과 유사하지만 요소가 순차적으로 배열되는 대신 각 요소에 참조/포인터가 포함
- **스택 :** 후입선출
- **큐 :** 선입선출
- **해시 테이블 :** 키와 값 쌍의 컬렉션을 저장하는 데 사용

#### [ 알고리즘 ]

- **정렬 :** 배열의 요소를 특정 순서로 재정렬하는 데 사용 (버블, 선택, 삽입, 퀵, 병합)
- **검색 :** 검색 알고리즘은 컬렉션에서 특정 요소를 찾는다. (선형 검색, 이진 검색)
- **재귀 :** 직접 또는 간접적으로 자체 내에서 호출되는 프로그래밍 기법 (수학 문제 풀이)
- **동적 프로그래밍 :** 복잡한 문제를 더 작은 하위 문제로 나누어 해결

## ✅ Big O 표기법과 시간 복잡도 분석의 이해

알고리즘의 시간 또는 공간 복잡도의 증가율을 설명하는 수학적 표기법

### Big O 표기법이란?

- **상수 시간 복잡도\_O(1) :** 입력 크기에 관계없이 알고리즈을 완료하는 데 동일한 시간이 걸림
- **로그 시간 복잡도\_O(log n) :** 알고리즘의 실행 시간이 입력 크기에 따라 대수적으로 증가하는 시간 복잡도
- **선형 시간 복잡도\_O(n) :** 실행 시간이 입력 크기에 따라 선형적으로 증가
- **준선형 시간 복잡도\_n log n :** 알고리즘의 실행 시간이 입력 크기에 따라 서의 선형적으로 증가
- **이차 시간 복잡도\_n^2 :** 알고리즘의 실행 시간이 입력 크기에 따라 기하급수적으로 증가

### 시간 복잡도는 어떻게 계산하나?

- 알고리즘의 시간 복잡도를 계산하려면 알고리즘이 수행하는 연산 횟수를 세어야 한다.

### 공간 복잡도

- 알고리즘은 시간 복잡도 외에도 특정 크기의 입력을 처리하는 데 사용하는 메모리 양인 공간 복잡도도 가질 수 있다.
- 공간 복잡도\_O(f(n))

## 참고

- 자료구조와 알고리즘 with 자바스크립트\_ 온개발팀저