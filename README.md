# DailyLogs

![](비모.gif)

*천리길도 한걸음부터, 初志貫徹, done is better than perfect*

그날그날 공부한 내용을 추려서 올립니다. TIL은 프라이빗 레포로 관리합니다. 충분히 이해한 내용, 나누고 싶은 내용은 [velog](https://velog.io/@tae0y)에 올리고 있습니다.

#### :runner: on-going

- 알고리즘 [solved.ac](https://solved.ac/profile/pty115) 19 / 100 **"코테마스터!"** [구현의왕](https://www.acmicpc.net/problemset?sort=ac_desc&solvedac_option=xz%2Cxn&tier=11%2C12%2C13%2C14%2C15&algo=102&algo_if=and)
- SQL 문제풀이 [HackerRank](https://www.hackerrank.com/) 13 / 100 **"포트폴리오 프로젝트에서 쓸 쿼리작성!"** 
- Java8, 11 (~2월末) [모던자바인액션](https://github.com/Modern-Java-in-Action/Online-Study/wiki) 14 / 21 챕터
- Kotlin/Android (~2월初)  [Udacity|코틀린으로 앱개발](https://classroom.udacity.com/courses/ud9012)  4 / 10 강의

#### :fist_oncoming: hold

- 프로그래머스 과제평가 연습문제 풀이
- 포트폴리오를 위한 토이프로젝트
- Android Jetpack

####  :man_dancing: well-done

- CS지식 구술평가 대비(네트워크/운영체제)
- SpringBoot/JPA [인프런|실전JPA활용1](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-JPA-%ED%99%9C%EC%9A%A9-1/dashboard) 7 / 7 섹션

## Contents

#### 22/2/9 뷰/스프링 프로젝트 게시판 만들기 헤딩

체크하지 않은 체크박스는 브라우저가 input을 submit하지 않는데, 그것을 몰라 자꾸만 nullpointerexception이 생겼다. 해결방법 하나는 hidden input을 만들어서 선택하지 않아도 값이 전달되도록 하는 것 하나, 둘째는 서버측에서 null을 제대로된 값으로 매핑해주는 것이다. 더 고민해보고 적용해야겠다. 확실히 웹에 대한 지식이 부족함을 느낀 하루. 길이 멀구나.

#### 22/2/8 김영한님 JPA활용1 강의가 막을 내렸다. 어제 못다푼 알골문제를 해결했다.

**김영한 JPA활용1** : 더 고민해볼 주제들이 생겼다. 시간을 두고 알아보자. 완강! 잘했다! 준영속 객체를 `merge`로 병합하는 대신, repository에서 새로 영속성 객체를 가져와 변경감지를 통해 수정하는 것이 안전하다. `merge`로 병합하면 값을 설정하지 않은 멤버가 null로 바뀔 위험이 있다. 객체 변경을 `@Setter`로 모두 열어버리면 유지보수가 어려우니 `createObject()`같은 생성 메서드를 사용하는 것이 좋다. 다시말해 팩토리 패턴을 사용하라는 것.

- 더 알아볼 것들
  - intelliJ 단축키 : 최근 사용한 파일목록, 선택한 영역을 템플릿으로 만들기, 테스트 생성, 테스트/원래코드간 전환, 메서드 정리, 에디터에서 커서 다중선택, 선택한 위치의 문자 대문자로 만들기 등 유용한 기능이 정말 많다.
  - JPA 동적쿼리 : JPA CRITERIA, Query DSL는 어떻게 사용하는가?
  - DTO란 무엇인가?

**코틀린/안드로이드** : ViewModel과 LiveData를 사용해서 데이터를 비동기로 처리할 수 있다.

- JAVA [14503번: 로봇 청소기 (acmicpc.net) ](https://www.acmicpc.net/problem/14503) 조건을 잘못 이해했다. 최고의 디버깅 방법은 세수하고 한숨 푹자고 일어나서 멀쩡한 정신으로 다시 보는 것..

#### 22/2/7 알골 문제풀이. 구현 문제는 규칙을 이해하는 게 절반이다.

- JAVA [14503번: 로봇 청소기 (acmicpc.net)](https://www.acmicpc.net/problem/14503) 헤딩

#### 22/2/6 모던자바, 뷰/스프링, SQL, 알골 문제풀이를 진행했다.

**모던자바인액션** : 자바는 인터페이스에 디폴트 메서드를 추가하면서 다중상속을 지원하게 되었다. 다이아몬드 문제를 피하기 위해서는 호출 우선순위 규칙을 정해두었다. 구현된 메서드 > 디폴트 메서드, 하위 인터페이스 > 상위 인터페이스. 그래도 안되면 `인터페이스.super.메서드명`으로 명시적 호출 또는 오버라이드. 그리고 모듈 시스템을 추가하여 코드 공개 수준을 컴파일 시점에 정밀하게 조정할 수 있게 되었다.

모던자바가 끝나면 이펙티브자바를 읽어보고, 자바17의 새로운 기능들도 더 배워보고 싶다. 코딩테스트를 준비하며 이전에 자바 정렬 메서드 사용법 정리한 글을 읽어보았는데, 스트림과 람다를 사용해 정렬하는 내용이 그제서야 이해가 되었다. 그리고 뷰/스프링 스터디에서 자바스크립트 람다식을 보았을 때도 코드를 잘 이해할 수 있었다. 몰랐던 것들이 점점 아는 것으로 바뀌어간다.

**뷰/스프링 스터디** :  maven2 이후로는 compile/provided/runtime 등 시점에 따라 의존성 주입을 제어할 수 있다. npm ci 명령어를 사용하면 package-lock.json을 우선하여 패키지를 설치하며, package.json과 충돌할 경우 오류를 내고 중단된다.

- SQL [Placements | HackerRank](https://www.hackerrank.com/challenges/placements/problem?isFullScreen=true)

  - 오라클문법 다중조인

    ```sql
    select x.컬럼이름A, 
           y.컬럼이름B,
           z.컬럼이름C, ...
    from 테이블이름X x, 테이블이름Y y, 테이블이름Z z, ...
    where x.컬럼이름M=y.컬럼이름N
      and y.컬럼이름O=z.컬럼이름Q;
    ```

  - ANSI문법 다중조인

    ```sql
    select x.컬럼이름A, 
           y.컬럼이름B,
           z.컬럼이름C, ...
    from 테이블이름X x join 테이블이름Y y
                        on x.컬럼이름M=y.컬럼이름N
                      join 테이블이름Z z
                        on y.컬럼이름O=z.컬럼이름Q;
    ```

- JAVA [15686번: 치킨 배달 (acmicpc.net)](https://www.acmicpc.net/problem/15686)

  - n C m (n은 13보다 작거나 같다) -> `bruteforce(pos+1, true, status); bruteforce(pos+1, false, status);`
  - 특정 원소를 제외하고 반복적으로 최솟값 구하기 : 정렬해서 여러 개를 구하는 거라면 PriorityQue로 하는 것이 좋다. qsort도 최악의 경우에는 O(n^2)이지만 힙정렬은 O(nlogn)에 끝나기 때문이다. 그러나 이번 문제는 최솟값 하나만 구하는 것이어서 Math.min으로 O(n) 안에 구했다.


#### 22/2/5 코딩테스트 결과는 지금으로서는 최선의 결과였다. 방향성은 옳으니 될때까지 계속한다. 뷰/스프링 스터디 참여, 스프링 인터넷 강의 수강하면서 배우는 게 많다.

**뷰/스프링 스터디** 프로젝트 환경설정 진행. intellij 커뮤니티 버전에서는 spring boot 프로젝트 실행이 안되는 문제가 발생함. spring.io에서 새로 프로젝트를 다운받아 pom.xml 등 설정파일을 diff해보자.

**오늘의 코딩테스트 리뷰** : SQL은 0 / 1솔, 알고리즘은 1.5 / 3솔이다. SQL은 문제에서 요구한 조건을 하나 빠뜨렸으나 테케로 확인하지 않고 제출해 틀렸다. 제출하고 나니까 "아맞다"하고 생각나더라. 그러나 해커랭크/리트코드로 SQL 문제풀이 계속해오니 코테 수준의 SQL은 잘 작성할 수 있었다. 방향성은 맞는것 같다. 앞으로도 감을 잃지 않게 꾸준히 풀어보자. 그리고 너무 SELECT 위주로 연습해왔으니,  CREATE/UPDATE/DELETE도 연습해보자. 알고리즘은 방향성을 잘못 잡았다. 알고리즘 대회를 나가는 것이 아니니 백준 골드는 과한 것 같다. 코테에서 주로 구현 문제를 많이 보았는데, 대비가 잘 안되어 있다. 백준에서 구현 문제를 위주로 풀어보자.

결론 : 1) 해커랭크/리트코드는 적어도 사흘에 한 문제 정도로 감을 유지 + 개인 프로젝트 DB만들어보면서 실전연습 2) 백준에서 구현/백트래킹/시뮬레이션 문제 위주로 더 풀이

**김영한 JPA활용1** : 강의 들으면서 더 필요한 내용을 정리, 자세한 내용 TIL

- JPA는 다양한 쿼리를 지원한다. 
  - JPQL은 엔티티 객체를 대상으로 검색한다. 테이블 조건검색 등 테이블 대상으로 해야 하는 것도 추상화된 객체형 SQL로 가능하게 해준다.
- 트랜잭션 : 스프링에선 어노테이션으로 간단히 설정할 수 있다. 이를테면 특정 예외발생시 롤백, 지정한 시간내 메서드 수행 완료 안되면 롤백, 읽기전용으로 수행 등.
- 의존성주입 : 객체 A를 실행하는 데 객체 B가 필요하다면, 언제 어느시점에 객체B를 건네주어야 할까? 스프링에선 어노테이션으로 간단히 설정할 수 있다.
  - 생성자 의존성주입 : 필수적인 레퍼런스를 꼭 가지도록 강제할 수 있고, 의존성 필드를 final로 설정할 수 있다. 순환 참조가 발생할 수 있다. A와 B가 서로 필요하다면, A생성자에서 B생성자를 다시 B생성자에서 A생성자를 호출하는 루프가 발생한다.
  - 필드 의존성주입 : 간단하지만, 의존관계가 눈에 잘 보이지 않아 과도하게 복잡해질 수 있다. final로 설정할 수 없다.
  - 세터 의존성주입 : 필요한 경우에 선택적으로 의존성주입을 할 수 있다. final로 설정할 수 없다.
    - '순환 참조'를 막기 위해 세터 의존성주입을 택하기 보다, 생성자 의존성주입을 택하되 순환 참조의 연결고리 자체를 끊어버리는 것이 옳다.
- 스프링 프로젝트는 MVC 패턴이다. Model 도메인, Repository CRUD 인터페이스, Controller 사용자요청처리 뷰처리, Service 받아온 데이터처리. 좌석버스, 버스탑승시스템, 버스고객센터, 좌석배정/차량운행 시스템
- 스프링 부트 `data-jpa` 사용하면 기본 설정이 h2 인메모리 데이터베이스이다. 그래서 개발/테스트할 때 휘발성으로 빠르게 접근해서 사용해보기 아주좋다.

고민. vue/spring강의 뭐듣지..

#### 22/2/4 백준 자바, 해커랭크 SQL 문제풀이 그리고 자바/SQL 헷갈렸던 내용 전체적으로 리뷰.

모르는 걸 틀리면 그런가보다 할텐데, 아는걸 틀리면 너무 억울할 것 같다. 그동안 JAVA/SQL 헷갈렸던 내용을 정리해서 리뷰했다. 늘 그렇듯, 최고가 아니라도 주어진 상황에서 최선의 결과를 얻자!

[MYSQL 코딩테스트 대비 (velog.io)](https://velog.io/@tae0y/MYSQL-코딩테스트-대비)

[JAVA 코딩테스트 대비 (velog.io)](https://velog.io/@tae0y/JAVA-코딩테스트-대비)

- JAVA

  - [11868번: 님 게임 2 (acmicpc.net)](https://www.acmicpc.net/problem/11868) : 돌게임부터 깨고 다시오자

- MYSQL

  - [Contest Leaderboard | HackerRank](https://www.hackerrank.com/challenges/contest-leaderboard/problem?isFullScreen=true)

  - [SQL Project Planning | HackerRank](https://www.hackerrank.com/challenges/sql-projects/problem?isFullScreen=true) : 다음코드는 a와 b의 모든 조합을 출력한다.

    ```mysql
    select col1, col2
    from (select col1 from table) a,
         (select col2 from table) b
    ```

#### 22/2/3 백준 자바, 해커랭크 SQL 문제풀이 그리고 :coffee::coffee:

- JAVA

  - [18222번: 투에-모스 문자열 (acmicpc.net)](https://www.acmicpc.net/problem/18222)

    - Math.pow는 double을 반환한다. Math.pow(2, 64)는 오버플로가 발생한다.
    - 문자열 '인덱스'와 '순서'를 헷갈리면 안된다. 첫번째 문자의 인덱스는 0이다.

  - [1197번: 최소 스패닝 트리 (acmicpc.net)](https://www.acmicpc.net/problem/1197)

    - union `if(root of a != root of b) a.root = b;` 
    - find `while(parent[a]==a) a=parent[parent[a]]; `

  - [11062번: 카드 게임 (acmicpc.net)](https://www.acmicpc.net/problem/11062) 

    ```java
    dp[i][j] = max(card[i]+dp[i+1][j], card[j]+dp[i][j-1]);
    dp[i][j] = min(dp[i+1][j], dp[i][j-1]);
    ```

- MYSQL
  - [Challenges | HackerRank](https://www.hackerrank.com/challenges/challenges/problem?isFullScreen=true) 반복되는 쿼리를 with으로 임시테이블로 만들어 사용

#### 22/2/2 백준 자바, 해커랭크 SQL 문제풀이했다. 그리고 자기소개서.. 자기소개서.. 자기소개서..

- JAVA
  - [18222번: 투에-모스 문자열 (acmicpc.net)](https://www.acmicpc.net/problem/18222) 헤딩중

- MYSQL
  - [Revising the Select Query II | HackerRank](https://www.hackerrank.com/challenges/revising-the-select-query-2/problem)
  - [Select All | HackerRank](https://www.hackerrank.com/challenges/select-all-sql/problem)
  - [Top Competitors | HackerRank](https://www.hackerrank.com/challenges/full-score/problem)
  - [Weather Observation Station 18 | HackerRank](https://www.hackerrank.com/challenges/weather-observation-station-18/problem)
  - [Weather Observation Station 19 | HackerRank](https://www.hackerrank.com/challenges/weather-observation-station-19/problem)
  - [Weather Observation Station 20 | HackerRank](https://www.hackerrank.com/challenges/weather-observation-station-20/problem)

#### 22/1/31 HackerRank SQL문제풀이했다.

`case 칼럼명 when 값`으로 쓸 수도 있고, `case 조건식`도 된다. `case/when`으로 칼럼값을 기준으로 세로로 쪼개고 `min/group by`로 합칠 수 있다. 마법같은 SQL!

- MYSQL
  - [Weather Observation Station 5 | HackerRank](https://www.hackerrank.com/challenges/weather-observation-station-5/problem)
  - [Revising the Select Query I | HackerRank](https://www.hackerrank.com/challenges/revising-the-select-query/problem)
  - [The PADS | HackerRank](https://www.hackerrank.com/challenges/the-pads/problem)
  - [Occupations | HackerRank](https://www.hackerrank.com/challenges/occupations/problem)
  - [Binary Tree Nodes | HackerRank](https://www.hackerrank.com/challenges/binary-search-tree-1/problem)
  - [The Report | HackerRank](https://www.hackerrank.com/challenges/the-report/problem)

#### 22/1/28 JPA 도메인 객체를 생성하고 연관관계 메서드를 만들어봄.

연관관계 매핑이란, 객체지향 프로그래밍과 관계형 데이터베이스 사이의 패러다임 불일치를 해소하기 위한 것이다. 연관관계의 주인이라 함은, 서로를 참조하는 두 객체 중 테이블 레코드를 저장, 수정, 삭제할 권할을 가진 객체를 말한다. 단, 테이블 레코드는 제어 권한을 가진 쪽에서만 수정하되, 객체 사이의 데이터는 동기화해주어야 한다.

연관된 객체를 불필요하게 불러오는 일이 없도록 실무에서는 '지연로딩'을 사용해야 한다.

JPA 영속성 컨텍스트란 애플리케이션과 데이터베이스 사이에서 객체를 보관하는 가상의 데이터베이스이다. '영속' 상태라 함은 엔티티 매니저로 객체를 영속성 컨텍스트에 저장한 것이고, '비영속'이란 객체가 생성되고 아직 영속석 컨텍스트에 저장하지 않은 경우이다.

#### 22/1/27 산타파이브 팀 세미나, 뷰/스프링 스터디에 참석. JPA 강의는 한 바퀴 듣고나면 꼭 기본편을 들어야겠다고 생각.

'내 트리를 꾸며줘' 서비스를 개발한 '산타파이브' 팀 세미나에 참석. '내 트리를 꾸며줘'는 동시접속 1000명 규모를 예상한 사이드 프로젝트였는데, 예상밖으로 큰 인기를 얻었다. 그 과정에서 산타파이브 팀이 예기치 않은 오류와 기능개발에 어떻게 대처했는지, 개발팀 및 기획/디자인 담당들의 눈물없이 들을 수 없는 분투기를 소개했다. 무려 서비스 출시 하루만에 호스팅 서비스를 대폭 교체했다는 내용, 말그대로 달리는 썰매 위에서 썰매날을 교체하는 일을 해온 개발자들이 존경스러웠다. 기획/디자인 담당자들이 밝힌 기획의도도 인상 깊었는데, 특히 이용자들과 가까워지기 위해 서비스 이름이 아니라 팀 이름으로 홍보/CS를 진행했다는 내용이 그랬다. 마지막으로 힘든 과정을 거치면서도 산타파이브 팀이 서로 다독이며 좋은 관계를 유지했다는 점도 놀라웠다. 

현직자들과 진행하는 vue/spring-boot 스터디 오리엔테이션에 참석. 언젠가 '산타파이브' 팀과 같은 동료를 만나고 함께 '내 트리를 꾸며줘'와 같은 서비스를 개발하길 기대해보게 됨.

#### 22/1/26 소켓/HTTP통신 실습을 위한 로컬서버 세팅하다가 검색 미로에 빠져버린 날. 그래도 여러가지를 배웠다. 스프링 강의로 다시 돌아옴.

thymeleaf는 스프링 부트가 자동설정을 지원하는 템플릿 엔진이다. JAR 패키징을 지원하고 자바 리소스, 속성파일, 라이브러리 등 모두 포함한다. 원하는 구조로 구성 가능하고 JRE만으로도 실행 가능하다. 반면 WAR로 패키징하는 JSP의 경우 웹 관련된 파일만 패키징하며, 정해진 구조로 구성해야 하고 Tomcat 같은 웹서버/웹컨테이너가 별도로 필요하다.

핫스왑이란 변경내용을 서버 재기동없이 적용하는 것이다.

자바빈즈는 재사용 가능한 소프트웨어 컴포넌트를 표방하는, 코딩컨벤션 중 하나이다. 직렬화가 가능해야 하고, getter/setter를 설정하는 등 규칙이 있다.

아파치2 mod_cband 모듈을 사용해서 사용자별/가상호스트별/목적지별 트래픽/대역폭을 제한할 수 있다. fail2ban은 ssh 로그파일을 스캔해 무작위대입 방식 공격을 막을 수 있는데, 주의할 점은 ssh 로그인시 총 5번의 재시도 기회를 주고 5번을 모두 틀려야 1회로 카운트한다는 것이다. free -h로 가용 메모리를 확인하고, 페이지당 평균 메모리 요구량을 확인하여 동시접속자수를 제한하면 된다. iptables로 허용된 ip에서만 접근할 수 있도록 제한을 걸 수도 있다.

MySQL이 Oracle로 넘어가면서, MySQL과 호환되면서 라이센스가 더 자유로운 MariaDB가 만들어졌다. ProstgressSQL은 멀티프로세스, MariaDB는 멀티스레딩 방식이다. 대규모 데이터, 복잡한 쿼리를 사용할 때는 ProstgressSQL을 사용하는 편이다. Redis는 시스템 메모리를 사용하는 키/값 데이터 스토어로, 수정이 잦은 데이터를 처리하거나 DBMS의 캐시로 사용한다.

#### 22/1/25 소켓/HTTP통신 실습을 위한 로컬서버 세팅, 알고리즘 문제풀이

- 백엔드 연습

  - [한번에 끝내는 U buntu 웹서버세팅 (우분투 서버세팅) – Lael's World](https://blog.lael.be/post/73)

- 알골 문제풀이

  - [SW Expert Academy 13218. 조별과제](https://swexpertacademy.com/main/code/problem/problemDetail.do)

  - [SW Expert Academy 13038. 교환학생](https://swexpertacademy.com/main/code/problem/problemDetail.do) 그리디문제인데 해법이 한번에 안떠오른다.


#### 22/1/23 자바8 Optional, 날짜/시간처리 라이브러리 복습, 그리고 자기소개서.

p.381, p.387 잘 이해가 안 간다.

저는 엄격한 아버지와 자애로운 어머니께 ........

#### 22/1/21 자바8의 날짜/시간처리 라이브러리를 복습했다.

[The Problem with Time & Timezones - Computerphile - YouTube](https://www.youtube.com/watch?v=-5wpm-gesOY)
시간대를 다루는건 정말 어려운 일이다.
- 율리우스력에서 그레고리력으로 바꿀 때, 오차를 조정하기 위해 열흘을 건너뛰었다.
  - 나라마다 그레고리력을 받아들인 시기가 다르다.
- 같은 장소에서 다른 시간대를 쓴다.
  - 이스라엘의 유대인과 팔레스타인끼리
  - 미국 내 인디언보호구역
- 일부 국가에서 여름에 한시간 당겨 생활하는 서머타임을 적용한다.
  - 같은 국가라도 서머타임 적용여부가 지역에 따라 달라진다.
  - 남반구와 북반구와 계절이 반대이므로, 남반구는 서머타임을 11월에 적용한다.
- 일부 국가는 소속 시간대를 변경한 경우가 있다.
- 달력의 오차를 조정하기 위해 '윤초'를 사용한다.
  - 윤초가 삽입된 날의 마지막을 59 / 59 / 00으로 하면 1초만큼의 시간 딜레이가 생긴다.
  - 윤초가 삽입된 날의 마지막을 59 / 60 / 00으로 하면 모든 시간처리 라이브러리를 재정의해야 한다.
  - 윤초를 24 * 60 * 60으로 나누어서 윤초가 삽입된 날은 1초마다 a밀리초를 더해주면, 시간동기화/시간처리 문제는 해결되나 1초가 부정확해진다.

#### 22/1/20 자바8의 DSL 기능을 복습하고, Optional/LocalTime 라이브러리 사용법을 공부했다.

NullSafe한 언어를 만드는 방법은 `?.`와 같이 네비게이션 연산자를 사용하는 것과, `Optional<T>`로 선택형값을 사용하는 것이 있다. 전자는 그루비에서, 후자는 하스켈/스칼라에서 사용한다. 코틀린은 둘 다 쓴다. `?.`를 엘비스 연산자라고 부른다.

메서드 시그니처에서 점 세개는 'Variable Arguments' 또는 'varargs'라고 하는데, 0개 이상의 인수를 받는다는 뜻이다. 메서드 매개인수의 가장 마지막에만 사용할 수 있다.

```
public static void main(String... args[]){
    // method body
}
```

#### 22/1/18 자바8의 새로운 기능을 활용한 리팩토링을 복습했다.

동작을 인수로 전달하는 곳에 람다/메서드참조를 사용한다. 람다/메서드참조를 감싼 메서드를 테스트하면 된다. 디버깅할 때는 람다/메서드참조 이름이 뜨지 않으므로 곤란한 일이 생길 것이다. 그리고 전략/템플릿/옵저버/의무체인/팩토리 패턴에 대해 간략하게 실습해보았다.

#### 22/1/16 자바8의 새로운 기능을 활용한 리팩토링, 테스팅, 디버깅, 그리고 DSL에 대하여 예습했다.

#### 22/1/10 꾸준한건 좋지만, 절대적인 학습량을 늘릴 필요가 있다.

- SQL/알골/일일면접
  - W3schools SQL Tutorial 완주

#### 22/1/8 알고리즘 문제풀이는 아직 한참 부족하구나. SQL은 문법을 한번 돌려야겠다.

- SQL/알골 : SQL은 전체문법을 훑어볼 필요가 있겠고, 알고리즘은 계속 풀어보면서 문제패턴을 통채로 외우면서 감을 익히는 수밖에 없겠다.
  - [(2) Reformat Department Table - LeetCode](https://leetcode.com/problems/reformat-department-table/submissions/) : GROUP BY, SUM을 이용해서 ID/월 테이블로 변환
  - [9663번: N-Queen (acmicpc.net)](https://www.acmicpc.net/problem/9663)
    - 접근방식 : 체스판을 이차원배열로 만들고, 퀸을 하나씩 놓을 때마다 퀸이 지나는 경로를 체크함. 다음 퀸을 놓을 때는 빈 체스판을 확인하고, 모든 퀸을 놓을 때까지 재귀반복. => 메모리초과
    - 해답 : 체스판에 N개의 퀸을 경로가 서로 겹치지 않게 놓는 문제는, N개의 행에서 퀸 놓을 자리를 찾는 문제와 같다. 경로가 서로 겹치는지는 1) 같은 열에 놓여있는지 2) 행간거리와 열간거리가 같은지 확인하면 된다. 일일히 체크판을 업데이트하지 않아도됨.

#### 22/1/7 백트래킹 등 시간제한을 걸어놓고 알고리즘 문제풀이를 더 해봐야겠다.

- SQL/알골
  - [(2) Swap Salary - LeetCode](https://leetcode.com/problems/swap-salary/submissions/)
  - [211230코테](####21/12/30 면접대비 MYSQL 리뷰, 코딩테스트 응시했으나 한 문제도 못 풀었다.) 5번문제 풀이, 메서드로 전달받은 인수를 복사해 로컬변수를 만들어놓고, 매개인수를 계속 건드려서 종료조건이 제대로 검사되지 못함.

#### 22/1/6 HTTP는 비연결성, 비상태 통신이므로 세션/쿠키를 이용해 인증정보를 유지한다. 시뮬레이션 문제는 루프방지 조건을 찾는게 중요하다.

- SQL/알골
  - [(2) Exchange Seats - LeetCode](https://leetcode.com/problems/exchange-seats/submissions/) : OVER/IF/WHEN
  - [211230코테](####21/12/30 면접대비 MYSQL 리뷰, 코딩테스트 응시했으나 한 문제도 못 풀었다.) 4번문제 풀이, 루프방지조건을 찾는 일이 어려웠다. 정작 찾고나니 허무할만큼 간단했지만.
- 일일면접 : 세션은 무엇이고, 서버가 여러 대일 때 세션을 어떻게 처리하나요?
  - HTTP 통신은 서버/클라이언트가 연결성과 상태를 유지하지 않는다. 로그인과 같이 인증상태를 유지해야하는 경우, 서버에 인증정보를 저장하고 클라이언트에는 해당 인증정보를 조회할 수 있는 키값을 저장합니다. 이때 서버측 데이터를 세션이라 하고, 클라이언트측 데이터를 쿠키라고 합니다. 
  - 다중 서버인 경우 로드밸런서가 쿠키로 연결된 서버를 조회하여 처음 인증을 맺은 서버로만 연결해줄 수 있습니다.  또는 인증정보를 모든 서버에 동기화해서 네트워크 성능 등 상황을 고려하여 서버를 연결해줄 수 있습니다. 
  - [HTTP 는 Stateless 한데 로그인은 어떻게 구현할 수 있을까? (세션/쿠키를 이용한 인증) (tistory.com)](https://hyuntaeknote.tistory.com/3?category=867120)

#### 22/1/5 안드로이드 액티비티/프래그먼트 수명주기를 복습, 액티비티 외부에서 수명주기를 관찰하고 작업을 수행할 수 있다.

액티비티 콜백 메서드는 생성 시점부터 제거될 때까지 다음 순서대로 호출된다: onCreate, onStart, onResume, onPause, onStop, onDestroy. 프래그먼트는 액티비티와 비슷한 수명주기를 가지나, 사용자 시야에서 벗어나면 곧바로 제거된다는 차이점이 있다. Lifecycle 라이브러리를 사용해 액티비티 외부에서 수명주기를 관찰하고 작업을 수행할 수 있다.

- SQL/알골
  - [(1) Not Boring Movies - LeetCode](https://leetcode.com/problems/not-boring-movies/submissions/)
- 일일면접 : 팩토리 메서드 패턴은 무엇이고 언제 사용할 수 있나요?
  - 객체 생성을 서브클래스/메서드로 위임하는 것으로, 상황에 맞춰 객체를 다르게 생성해야 할 때 사용할 수 있다. 추상 팩토리 패턴은, 팩토리 메서드를 별도 인터페이스에서 정의해두고 그 인터페이스를 구현한 클래스를 사용하는 것이다. 예시 : `List<String> list = ListFactory.of(array); `, `List<String> list2 = ListFactory.of(jsonString);` (참고: [디자인패턴:팩토리 패턴(Factory Pattern) – friday's blog (fun25.co.kr)](http://friday.fun25.co.kr/blog/?p=280))

#### 22/1/4 알골/SQL을 풀다보니, 마냥 풀기보다 잘 짜여진 코드를 더 많이 보고싶다.

안드로이드 액티비태 생애주기, LogCat

- SQL/알골
  - [(1) Human Traffic of Stadium - LeetCode](https://leetcode.com/problems/human-traffic-of-stadium/submissions/)
- [211230코테](####21/12/30 면접대비 MYSQL 리뷰, 코딩테스트 응시했으나 한 문제도 못 풀었다.) 3번문제 풀이, 피라미드를 배열에 담아 탐색, 코드는 167줄

#### 22/1/3 HttpURLConnection, Java-Json을 사용해서 공공데이터포털 API사용 실습.

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

#### 22/1/2 자바8 병렬처리/컬렉션API 복습하고, 문자열 다루는 알골 문제를 스트림으로 다시 풂.

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

### 2021

개발자로 진로를 굳힘. 전역을 함. 라이브러리/프레임워크 사용경험이 필요하다. 코딩부트캠프, 서비스회사, 스타트업 위주로 취준.

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