# DailyLogs

![](비모.gif)

*done is better than perfect, 初志貫徹*

그날그날 공부한 내용을 추려서 올립니다. TIL은 프라이빗 레포로 관리합니다. 충분히 이해한 내용, 나누고 싶은 내용은 [네이버 블로그](https://blog.naver.com/PostList.naver?blogId=pty115&from=postList&categoryNo=71)에 올리고 있습니다.

#### :runner: on-going

- 알고리즘/SQL 문제풀이
- Java8, 11 (~2월)

#### :fist_oncoming: hold

- Kotlin/Android (~1월)
- Java/SpringBoot (~1월)
- 프로그래머스 과제평가 연습문제 풀이
- 포트폴리오를 위한 토이프로젝트

####  :man_dancing: well-done

- CS지식 구술평가 대비(네트워크/운영체제)

## Contents

#### 21/1/4 알골/SQL을 풀다보니, 마냥 풀기보다 잘 짜여진 코드를 더 많이 보고싶다.

안드로이드 액티비태 생애주기, LogCat

- SQL/알골

  - [(1) Human Traffic of Stadium - LeetCode](https://leetcode.com/problems/human-traffic-of-stadium/submissions/)

  - ```mysql
    SELECT ID, VISIT_DATE, PEOPLE
    FROM STADIUM S
    WHERE (PEOPLE >= 100)
        AND (((SELECT ID FROM STADIUM WHERE ID=S.ID-1 AND PEOPLE >= 100) IS NOT NULL 
        AND (SELECT ID FROM STADIUM WHERE ID=S.ID-2 AND PEOPLE >= 100) IS NOT NULL) 
        OR ((SELECT ID FROM STADIUM WHERE ID=S.ID+1 AND PEOPLE >= 100) IS NOT NULL 
        AND (SELECT ID FROM STADIUM WHERE ID=S.ID+2 AND PEOPLE >= 100) IS NOT NULL)
        OR ((SELECT ID FROM STADIUM WHERE ID=S.ID-1 AND PEOPLE >= 100) IS NOT NULL 
        AND (SELECT ID FROM STADIUM WHERE ID=S.ID+1 AND PEOPLE >= 100) IS NOT NULL))
    ORDER BY VISIT_DATE
    ```

  - ```mysql
    select id, visit_date, people 
    from (
    select id, visit_date, people,
           CASE WHEN min(people) OVER(ORDER BY id ROWS BETWEEN CURRENT ROW AND 2 FOLLOWING) >= 100 THEN 'YES'
    			WHEN min(people) OVER(ORDER BY id ROWS BETWEEN 1 PRECEDING AND 1 FOLLOWING) >= 100 THEN 'YES'
    			WHEN min(people) OVER(ORDER BY id ROWS BETWEEN 2 PRECEDING AND CURRENT ROW) >= 100 THEN 'YES'
                ELSE 'NO'
           END as condition_check
    from tmp        
        ) t 
    where condition_check = 'YES'
    ORDER BY 2
    ```

  - [211230코테](####21/12/30 면접대비 MYSQL 리뷰, 코딩테스트 응시했으나 한 문제도 못 풀었다.) 3번문제 풀이, 피라미드를 배열에 담아 탐색, 코드는 167줄

#### 21/1/3 HttpURLConnection, Java-Json을 사용해서 공공데이터포털 API사용 실습.

- HTTP 상태코드. 
  - 1xx(조건부 응답) 요청을 받았으며 프로세스를 계속한다. 
  - 2xx(성공) 요청을 성공적으로 받았으며 인식했고 수용하였다. 
    - 200 성공
  - 3xx(리다이렉션 완료) 요청완료를 위해 추가 작업 조치가 필요하다. 
  - 4xx(요청오류) 요청의 문법이 잘못되었거나 요청을 처리할 수 없다. 
    - 400 잘못된요청, 401 인증안됨, 403 권한없음, 404 찾을수 없음
  - 5xx(서버오류) 서버가 명백히 유효한 요청에 대해 충족을 실패했다.
    - 500 내부서버오류, 502 Bad Gateway, 503 서비스 사용불가, 504 게이트웨이 시간초과

- SQL/알골
  - [(1) Big Countries - LeetCode](https://leetcode.com/problems/big-countries/)
  - [(1) Classes More Than 5 Students - LeetCode](https://leetcode.com/problems/classes-more-than-5-students/)
  - [211230코테](####21/12/30 면접대비 MYSQL 리뷰, 코딩테스트 응시했으나 한 문제도 못 풀었다.) 3번문제 풀이시도/실패

#### 21/1/2 자바8 병렬처리/컬렉션API 복습하고, 문자열 다루는 알골 문제를 스트림으로 다시 풂.

병렬처리가 무조건 순차처리보다 빠른 것은 아니니 상황을 잘 고려해서 적용해야 한다. 컬렉션 객체를 다루는 여러 메서드가 추가되었고, 맵에도 스트림화하지 않더라도 사용할 수 있는 유용한 메서드가 추가되었다.

- SQL/알골
  - [(1) Rising Temperature - LeetCode](https://leetcode.com/problems/rising-temperature/)
  - [211230코테](####21/12/30 면접대비 MYSQL 리뷰, 코딩테스트 응시했으나 한 문제도 못 풀었다.) 코드를 일부개선
  - [코딩테스트 연습 - 오픈채팅방 | 프로그래머스 (programmers.co.kr)](https://programmers.co.kr/learn/courses/30/lessons/42888) 문자열 처리를 스트림으로 다시풀었다. 단순 반복문으로 풀었을때는 실행시간이 0.29ms ~ 306.53ms이었지만, 스트림으로 문제를 풀면 3.90ms ~ 117.59ms 소요되었다. 스트림은 굉장히 많은 데이터를 다룬다거나, 데이터 하나당 처리시간이 긴 경우에 성능상 이득을 볼 수 있다는 것을 다시 확인할 수 있었다.

#### 22/1/1 :sunny: 자바8은 컬렉션 객체를 보다 쉽게 다룰 수 있는 여러 유용한 메서드를 추가했다.

of 메서드로 작은 컬렉션을 보다 엄밀한 의미의 '불변객체'로 선언할 수 있다. 리스트에 removeIf, replaceAll로 객체의 순회/변경을 추상화할 수 있다. 또한 맵도 forEach, sorted, getOrDefault, computeIfAbsent, remove, replaceAll 등으로 순회/변경 과정을 추상화할 수 있다.

- SQL/알골
  - [(1) Customers Who Never Order - LeetCode](https://leetcode.com/problems/customers-who-never-order/submissions/)
  - [211230코테](####21/12/30 면접대비 MYSQL 리뷰, 코딩테스트 응시했으나 한 문제도 못 풀었다.) 2번문제 리뷰 : 규칙체크 - 업데이트 - 종료조건검사 - 재귀호출

#### 21/12/31 병렬처리가 꼭 순차처리보다 빠른 것만은 아니다. SQL/알골 문제도 풀었다.

내부 반복을 이용해 명시적으로 다른 스레드를 사용하지 않고도 스트림을 병렬로 처리할 수 있다. 간단하게 스트림으로 병렬 처리할 수 있지만 항상 병렬 처리가 빠른 것은 아니다. 필요할 때는 순차 처리와 성능을 직접 측정해서 비교해봐야 한다. 병렬 스트림으로 데이터 집합을 처리할 때 처리해야할 데이터가 아주 많거나 각 요소를 처리하는 데 오래 걸릴 때 성능을 높일 수 있다. 가능하면 기본형 특화 스트림 등 올바른 자료구조를 선택이 어떤 연산을 병렬로 처리하는 것보다 성능적으로 더 큰 영향을 미칠 수 있다. 아울러 병렬 처리할 때에도 적합한 자료구조를 택해야 성능상 이점을 온전히 누릴 수 있다. 포크/조인 프레임워크는 병렬화할 수 있는 태스크를 작은 태스크로 분할하여 각각의 스레드로 실행하며 서브태스크 결과를 합쳐서 최종 결과를 생산한다. Spliterator는 탐색하려는 데이터를 포함하는 스트림을 어떻게 병렬화할 것인지 정의한다.

- SQL/알골

  - [(1) Employees Earning More Than Their Managers - LeetCode](https://leetcode.com/problems/employees-earning-more-than-their-managers/)

  - [(1) Duplicate Emails - LeetCode](https://leetcode.com/problems/duplicate-emails/)

  - [211230코테](####21/12/30 면접대비 MYSQL 리뷰, 코딩테스트 응시했으나 한 문제도 못 풀었다.) 1번문제 리뷰 : 부등호 구간을 잘못 적어서 틀렸던 거임

#### 21/12/30 면접대비 MYSQL 리뷰, 코딩테스트 응시했으나 한 문제도 못 풀었다.

시뮬레이션/조합문제. 지문이 길고 제약사항이 많았다. 문제 자체는 어렵지 않았으나 풀기가 벅찼다. 그럼에도 불구하고, 계속 연습해보는 수밖에 없다.

#### 21/12/29 면접대비 운영체제, 네트워크 개념 리뷰

- 운영체제
  - 프로세스는 각자 코드/데이터/힙/스택, 스레드는 각자 스택
  - 멀티스레딩은 문맥전환이 저렴하나 동기화 문제있음 
  - 라운드로빈 스케줄링은 기아문제 없지만 문맥전환 오버헤드 가능
  - LRU 알고리즘은 가장 오래 사용되지 않은 페이지를 교체
  - 외부단편화는 여유공간 흩어진것, 내부단편화는 더 크게 박싱된것
  - 고정분할-페이징, 다중분할-세그멘테이션

- 네트워크

  - TCP는 신뢰성을 보장하는 연결형, UDP는 부하가 적은 비연결형

  - GET은 URL/헤더로, POST는 바디에 데이터를 포함

  - OSI 7계층은 물/데/네/전/세/표/응

  - 세션은 서버측에서, 쿠키는 웹브라우저에서 유지하는 데이터

#### 21/12/28 Java-Json, HttpConnection 라이브러리 사용연습

#### 21/12/26 :snowman: 

#### 21/12/25 :christmas_tree:

#### 21/12/24 스프링 부트 JPA REST 헬로월드 프로젝트 실행까지

JPA 인터페이스를 어떻게 선언해야 하고, REST API는 어떻게 구성해야 하는지 잘 모르겠다. 인프런 강의를 듣기로.

#### 21/12/23 REST 과제 테스트 환경설정만 하루종일 했다. 윈도우 명령어는 생소하다.

2019 카카오 블라인드 2차 문제풀이에 도전. 그러나 환경설정에서 하루종일 삽질을 거듭하다 포기했다. 문제가 출제된 이후 golang의 패키지 관리 부분에서 큰 변화가 있었고, 그에 따라 적절한 패키지를 불러오지 못하는 상황이었다. 여러 블로그를 참고하여 `go env -w GO111MODULE="off"` 명령어로 사장된 기능을 잠시 꺼두고 `go mod init` 으로 새 패키지 관리 명령어를 사용했으나, 결국은 윈도우/WSL 모두 환경설정에 실패했다. golang config 파일에서 패키지 버전을 조정해주면 되겠지만, golang은 코드를 수정하지도 못할 정도로 전혀 알지 못한다.

결론, PLANB로 스프링부트 등을 활용해 로컬 웹앱을 구동하고 요청/응답만 연습하기로 했다.

- 리눅스 / 윈도우 명령어
  - mv / 파일을 이동하기 : move [destination_file] [destination_folder]
  - mkdir / 폴더를 만들기 : mkdir [folder_name]
  - rm / 파일을 삭제하기 : del [file_name]
  - rmdir / 폴더를 삭제하기 : rmdir [folder_name]

#### 21/12/22 SQL문제풀이, URL/URI란, 운영체제 개념복습

- ANSI SQL은 DBMS 종류에 제약을 받지 않는다.
  - [친절한 SQL 튜닝 - YES24](http://www.yes24.com/Product/Goods/61254539)(오라클DB)
  - [Real MySQL - YES24](http://www.yes24.com/Product/Goods/6960931)

- [URI,URL,URN](https://github.com/CodingInterviewStudy/CrackingTheCodingInterview/wiki/7주차-2) : 이전에는 `naver.com/main.html`과 같이 웹사이트 리소스를 위치로(URL/URI) 불러오는 방식이었으나, 최근에는 Restful을 추구하며 `naver.com/main`으로 구분자를 통해(URI) 불러온다.
  - ![img](https://camo.githubusercontent.com/99a24e41700a0c2deeaf357291cfd916d518399454f72dca6e0b43ba35b149dc/68747470733a2f2f747661312e73696e61696d672e636e2f6c617267652f3030386933736b4e6779316776716d3938767471376a3630626a30366d30737630322e6a7067)

- 페이지교체 알고리즘
  - LRU 가장 오랫동안 참조되지 않은 페이지를 교체
  - LFU 참조횟수가 가장 적은 페이지를 교체, 왜냐하면 초기에 집중적으로 참조한 페이지는 더 필요하지 않을 수 있으므로
  - MFS 참조횟수가 가장 많은 페이지를 교체, 왜냐하면 참조횟수가 적으면 최근에 불러와 사용중인 페이지일 수 있으므로

#### 21/12/21 페이지교체 알고리즘, 단편화, 캐시 지역성에 대해 복습했다.

깊이 들어가면 끝이 없다. 개념 복습으로 마무리하고, 개발에 어떻게 활용할지 고민하면서 더 파고 들어가야 하겠다.

#### 21/12/20 프로세스, 멀티 프로세스, 프로세스 스케줄링에 대해 복습했다.

#### 21/12/19 자바 스트림 filter, collect 등 메서드 사용법을 복습했다.

#### 21/12/18 SQL SELECT문 관련내용을 정리했다.

SET 변수, WITH RECURSIVE, GROUP BY, 문법/실행순서, DATE_FORMAT, 컬럼/테이블 별칭, 테이블 조인 연산, WHERE, IF ELSE, LIMIT, SUBSTR

#### 21/12/17 자바 스트림에서 다양한 리듀스 연산을 수행할 수 있다. 프로그래머스 SQL 고득점 Kit를 완주했다!

- 자바 스트림 누적자 리듀싱 연산

  - 이미 정의된 리듀싱 : counting 등

  - 범용 리듀싱 : reducing

  - 그룹핑 : groupingBy

  - 누적자 : collect

- 프로그래머스 SQL Kit 완주!

#### 21/12/16 자바 컬렉션 객체에 스트림을 사용해 DB 쿼리처럼 다양한 작업을 할 수 있다.

스트림 메서드는 중간연산, 최종연산으로 나뉜다. 최종연산은 스트림 객체를 반환하지 않고, 중간연산은 스트림 객체를 반환한다. 중간연산은 최종연산을 만나야만  작업을 시작한다(루프퓨전, 쇼트서킷 등 포함.) 

#### 21/12/15 객체지향 SOLID : '추상성'을 최대한 유지하기 위해 '다형성'을 활용한다.

- Single Responsibility Principle 단일책임의 원칙 : 하나의 클래스는 하나의 책임을 가져야 하며, 변경이 있을 때 파급효과가 적도록 해야 한다.
- Open/closed Principle 개방-폐쇄의 원칙 : 확장에는 열려있되 변경에는 닫혀있어야 한다. 이를테면 객체의 멤버변수를 클래스 대신 인터페이스로 선언하면, 상황에 맞춰 해당 인터페이스를 구현한 클래스를 사용할 수 있다.
- Liskov Substitution Principle 리스코프 치환의 원칙 : 상위 타입의 객체를 하위 타입의 객체로 치환해도 상위 타입을 사용하는 프로그램은 정상 동작해야 한다. 
- Interface Segregation Principle 인터페이스 분리의 원칙 : 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다.
- Dependency Inversion Principle 의존관계 역전 원칙 : 프로그래머는 추상화에 의존해야지 구체화에 의존하면 안된다. 구현 클래스에 의존하지 말고 인터페이스에 의존해야 한다. 

#### 21/12/12 자바 스트림은 연산을 연속/병렬 처리하는 API이다.

컬렉션은 모든 데이터를 메모리에 올려 한 번에 처리한다. 스트림은 처리할 데이터만 메모리에 올려 처리한다. 컬렉션, 배열, 표준 입출력 등을 스트림화할 수 있는데, 스트림화는 비싼 연산이다. 

#### 21/12/11 자바 람다는 익명클래스를 단순화한 것이다. 

- `(인수목록) -> 표현식`
- `(인수목록) -> {코드블록;}`

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