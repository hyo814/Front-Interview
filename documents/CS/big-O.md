# 💻 빅오(Big-O)표기법
<br />

## 👨🏻‍💻 빅오(Big-O)란?
- 빅오(O, Big-O)란 입력값이 무한대로 향할때 함수의 상한을 설명하는 수학적 표기 방법이다.
- 컴퓨터 과학에서 빅오는 입력값이 커질 때 알고리즘의 `실행 시간(시간 복잡도)`과 함께 `공간 요구사항(공간 복잡도)`이 어떻게 증가하는지를 분류하는 데 사용된다.
- 알고리즘의 효율성을 분석하는 데에도 매우 유용하게 활용 된다.
- 알고리즘은 흔히 '시간과 공간이 트레이드 오프(Space-Time Tradeoff)' 관계다. 이 말은 실행 시간이 빠른 알고리즘은 공간을 많이 사용하고, 공간을 적게 차지하는 알고리즘은 실행 시간이 느리다는 이야기이다.


<br />

## 👨🏻‍💻 시간 복잡도(Time Complexity)
- 시간 복잡도의 사전적 정의는 어떤 알고리즘을 수행하는 데 걸리는 시간을 설명하는 계산 복잡도(Computational Complexity)를 의미하며, 계산 복잡도를 표기하는 대표적인 방법이 바로 빅오다.
- 빅오로 시간 복잡도를 표현할 때는 최고차항만을 표기하며, 계수는 무시한다. 예를 들어 입력값 n에 대해 4n^2 + 3n + 4 만큼 계산하는 함수가 있다면 이 함수의 시간 복잡도는 최고차항인 4n^2만을 고려한다. 이중에서도 계수는 무시하며 n^2 만을 고려한다. 즉, 시간 복잡도는 O(n^2)이 된다.

<br />

## 👨🏻‍💻 공간 복잡도(Space Complexity)
- 공간 복잡도란, 프로그램을 실행시킨 후 완료하는데 필요로 하는 자원 공간의 양을 말한다.
- 총 공간 요구 = 고정 공간 요구 + 가변 공간 요구로 나타낼 수 있다.
- 고정 공간은 입력과 출력의 횟수나 크기와 관계없는 공간의 요구(코드 저장 공간, 단순 변수, 고정 크기의 구조 변수, 상수)를 말한다.
- 가변 공간은 해결하려는 문제의 특정 인스턴스에 의존하는 크기를 가진 구조화 변수들을 위해서 필요로 하는 공간, 함수가 순환 호출을 할 경우 요구되는 추가 공간, 즉 동적으로 필요한 공간을 말한다.

<br />

## 👨🏻‍💻 빅오 종류
### 🏃 O(1)
- 입력값이 아무리 커도 실행 시간을 일정하다.
- 최고의 알고리즘이라 할 수 있다.
- O(1)에 실행되는 알고리즘으로 해시 테이블의 조회 및 삽입이 해당한다.

<br />

### 🏃 O(log n)
- O(1)과 다르게 실행 시간이 입력값에 영향을 받는다.
- 로그는 매우 큰 입력값에도 크게 영향을 받지 않는 편이기 때문에 웬만한 n의 크기에 대해서도 매우 견고하다.
- 대표적으로 이진 검색이 이에 해당한다.

<br />

### 🏃 O(n)
- 입력값만큼 실행 시간에 영향을 받으며, 알고리즘을 수행하는 데 걸리는 시간은 입력값에 비례한다. 이러한 알고리즘을 선형 시간(Linear-Time)알고리즘이라고 한다.
- 정렬되지 않은 리스트에서 최댓값 또는 최솟값을 찾는 경우가 이에 해당하며 이 값을 찾기 위해서는 모든 입력값을 적어도 한 번 이상은 살펴봐야 한다.

<br />

### 🏃 O(n log n)
- 병합 정렬을 비롯한 대부분의 효율 좋은 정렬 알고리즘이 이에 해당한다.
- 적어도 모든 수에 대해 한 번 이상은 비교해야 하는 비교 기반 정렬 알고리즘은 아무리 좋은 알고리즘도 O(n log n)보다 빠를 수 없다.
- 물론 입력값이 최선인 경우, 비교를 건너 뛰어 O(n)이 될 수 있으며 팀소트(Timesort)가 이런 로직을 갖고 있다.

<br />

### 🏃 O(n^2)
- 버블 정렬 같은 비효율적인 정렬 알고리즘이 이에 해당한다.

<br />

### 🏃 O(2^n)
- 피보나치 수를 재귀로 계산하는 알고리즘이 이에 해당한다.
- n^2와 비슷해보이지만 2^n이 훨씬 더 크다.

<br />

### 🏃 O(n!)
- 각 도시를 방문하고 돌아오는 가장 짧은 경로를 찾는 외판원 문제(Travelling Salesman Problem)를 브루트 포스로 풀이할 때가 이에 해당한다.
- 가장 느린 알고리즘으로, 입력값이 조금만 커져도 웬만한 다항 시간 내에는 계산기 어렵다.

<br />