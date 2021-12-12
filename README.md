# DailyLogs

![](비모.gif)

그날그날 공부한 내용을 한 줄로 요약해 업로드합니다. TIL은 프라이빗 레포로 관리 중이고, 충분히 이해하고 나누고 싶은 것을 골라 [네이버 블로그](https://blog.naver.com/PostList.naver?blogId=pty115&from=postList&categoryNo=71)에 올리고 있습니다.

#### on-going

- Java8, 11
- Kotlin/Android
- Interview(CS/algorithm)

## Contents

#### 21/12/12 자바 스트림은 연산을 연속/병렬 처리하는 API이다.

컬렉션은 모든 데이터를 메모리에 올려 한 번에 처리한다. 스트림은 처리할 데이터만 메모리에 올려 처리한다. 컬렉션, 배열, 표준 입출력 등을 스트림화할 수 있는데, 스트림화는 비싼 연산이다. 

#### 21/12/11 자바 람다는 익명클래스를 단순화한 것이다.

#### 21/12/08 시스템 테스팅 면접문제도 면접관과 의사소통이 중요하다.

1)사용자와 사용목적을 확인 2)면접관과 의사소통하며 사용하는 경우의수 추려내기 3)한계조건을 확인 4)스트레스 조건과 장애조건을 확인 5)테스트 종류가 블랙박스/화이트박스 무엇인지, 사람의 개입이 필요한 테스트인지 확인

#### 21/12/07 시스템 디자인 설계 면접문제는 면접관과 의사소통이 중요하다.

문제를 정확히 정의하고, 작은 규모의 시스템에서 더 큰 규모로 점증적으로 확대해 나가자. 가정을 할 때는 명확히 언급하면 혹시 문제를 잘못 이해했을 때 면접관이 바로잡아줄 수 있다. 

#### 21/12/05 동작을 파라미터화해 객체지향 패러다임을 유지할 수 있다.

이를테면 컬렉션에서 어떤 데이터를 추출해야 하는데, 요구사항이 상황에 따라 시시때때로 변한다고 가정해보자. 보다 간결한 코드를 위해 프리디케이트, 익명클래스, 람다, 제네릭 등을 활용해 데이터 처리 함수를 바깥에서 구현, 매개인자로 넘겨 처리할 수 있다.

#### 21/12/03 백준에서 크루스칼 알고리즘 문제를 풀다.

- [1197번: 최소 스패닝 트리 (acmicpc.net)](https://www.acmicpc.net/problem/1197)
- [2406번: 안정적인 네트워크 (acmicpc.net)](https://www.acmicpc.net/problem/2406) 메모리초과로 고심하다 `Scanner` 대신 `BufferedReader`를 사용해 해결

#### 21/12/02 소프티어 모의 알고리즘 대회에 참가, 크루스칼 알고리즘을 짜지 못하다.

1)간선(정점A, 정점B, 가중치) 리스트로 구성한다. 2)오름차순으로 정렬한다. 3)union-find함수를 이용해 disjoing-set을 수행한다. 

#### 21/12/01 최소공통조상트리는 깊이우선탐색을 활용한다.

1)트리를 구성한다. 2)노드는 부모/자식/깊이 정보를 가지고 있다. 3)임의의 노드를 선택해 루트노드를 찾는다. 4)루트노드로부터 깊이우선탐색을 실시하고 깊이 정보를 갱신한다. 5)주어진 두 개 노드의 깊이를 맞춘다. 6)두 노드가 같아지면 결과값을 출력하고 종료한다. 

#### 21/11/30 자바8은 함수형 패러다임을 일부 수용했다.

자바8 이후로는 보다 간결하게 코드를 작성하고, 보다 쉽게 멀티코어 프로세서를 활용할 수 있다. 이를테면 컬렉션 객체에서 데이터를 추출/정렬할 때, 메서드 체이닝과 람다 표현식으로 보다 자연어에 가깝게 서술할 수 있다. 또한 대용량 데이터의 경우 StreamAPI를 활용해 병렬작업을 추상화해 수행할 수 있다.