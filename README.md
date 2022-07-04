# DailyLogs

![](비모.gif)

*初志貫徹, done is better than perfect, 걱정을해서 걱정이 없다면 걱정이 없겠네*

그날그날 공부한 내용을 추려서 올립니다. TIL은 프라이빗 레포로 관리하고, 같이 나누고 싶은 내용은 [velog](https://velog.io/@tae0y)에 올립니다.

#### :runner: on-going

- ios/swift, 12월까지
- 이펙티브자바 일독하기(13/90), 7월까지 

#### :fist_oncoming: hold

- Java8, 11 (~4.6.) [모던자바인액션](https://github.com/Modern-Java-in-Action/Online-Study/wiki) 21 / 21 챕터
  - 2주 더 투자해서 복습, 깃허브에 예제/내용요약 올리기
  - 자바11 이후의 변화
- SpringSecurity [인프런|백기선,스프링시큐리티](https://www.inflearn.com/course/%EB%B0%B1%EA%B8%B0%EC%84%A0-%EC%8A%A4%ED%94%84%EB%A7%81-%EC%8B%9C%ED%81%90%EB%A6%AC%ED%8B%B0) 40 / 48 강의
- 알고리즘 [solved.ac](https://solved.ac/profile/pty115) 19 / 100,  [백준|구현의왕 문제세트](https://www.acmicpc.net/problemset?sort=ac_desc&solvedac_option=xz%2Cxn&tier=11%2C12%2C13%2C14%2C15&algo=102&algo_if=and)
- SQL 문제풀이 13 / 100, [HackerRank|SQL 문제세트](https://www.hackerrank.com/)
- 프로그래머스 과제평가 연습문제 풀이
- Android Jetpack : Compose(선언형 UI 라이브러리) 등
- Kotlin/Android (~2월初)  [Udacity|코틀린으로 앱개발](https://classroom.udacity.com/courses/ud9012)  4 / 10 강의
- 토이프로젝트: kotlin/android (REST통신, 로컬DB CRUD, 커스텀뷰)
- 헤드퍼스트 디자인패턴 3 / 14 챕터
- 포트폴리오 사이드프로젝트: 보안시각화, 링크관리, 시간표관리

####  :man_dancing: well-done
- CS지식 구술평가 대비(네트워크/운영체제)
- SpringBoot/JPA [인프런|김영한,실전JPA활용1](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8-JPA-%ED%99%9C%EC%9A%A9-1/dashboard) 7 / 7 섹션
- 토이프로젝트: vue/spring-boot/mariadb - JWT토큰 사용한 로그인(SpringSecurity) 및 게시판(vue-routes)
- 토이프로젝트: ios/swift/storyboard - 랜덤메뉴생성(REST, 뷰 동적생성)



## Contents

### 2022

### 22/7/4 ios 랜덤메뉴앱 헤딩+1, autolayout 적용 성공

그리고 한 가지 더!! 랜덤메뉴앱에 autolayout을 적용했다. leading / trailing constraint 개념을 알고나니 무척 간단히 끝났다. 불필요한 width / left constraint를 지우고, leading / trailing을 superview에 맞춰 0으로 설정해주었다. [소들님 블로그](https://babbab2.tistory.com/155?category=932180)를 참고했다. autolayout 카테고리를 순서대로 읽다보니 정말 쉽게 이해가 됐다. 애플 공식문서보다 낫다.

#### 22/6/27 equals, hashcode
equals를 재정의하면 hashcode도 재정의! 논리적으로 같은 객체는 hash도 같아야한다.

#### 22/6/26 ios 랜덤메뉴앱 헤딩4, 이번에는 여기까지
깃헙에서 xib로 구현한 카드뷰를 찾아 적용했다. 버튼도 추가해줬는데, ios에서는 터치 이벤트에 파라미터를 더 넘길수가 없다. 버튼에 태그를 걸어 어떤 버튼인지 확인하고 다음 로직을 수행했다. info.plist에 미리 정의한 앱으로 URL을 통해 다른앱을 실행할 수 있는데, 안드로이드와 같이 묵시적 인텐트를 찾지 못해 아쉽다. 다음 과제는 constraint/anchor를 사용해 동적으로 뷰를 추가하는 방법, gestureRecognizer로 터치 이벤트 다루는 방법을 제대로 익히는 것이다.
- scrollview
  - stackview(vertical)
    - (repeated) stackview(vertical)
      - cardview
      - button

#### 22/6/20 ios 랜덤메뉴앱 헤딩3

스크롤이 안돼서 한참을 헤맸다. scrollview 아래에 stackview를 추가해줬으나 constraint 설정이 잘못되어 스크롤이 되지 않았다.
- 스크롤뷰 사용방법
  - 스크롤뷰: alt키 누르면서 margin 없이 상위 뷰에 constraint를 추가
  - 컨테이너뷰(스택뷰): alt키 안누르고 constraint를 추가, 세로 스크롤인 경우 equalWidth to ScrollView
  - 컨테이너 내부의 뷰(라벨뷰): 각각 모든 뷰가 다른 뷰 bottom을 바라보게 설정해서 컨테이너가 높이를 계산할 수 있게 해준다

#### 22/6/19 ios 랜덤메뉴앱 헤딩2

REST 요청작업을 클로저로 구현해 넘겼다. 해당 클로저에서 값을 밖으로 빼내려면 @escaping으로 명시한 클로저를 사용해줘야 한다. 이어서 백그라운드 스레드에서 UI를 수정하지 못하기 때문에 main에서 비동기로 처리해야 한다. 두 가지 개념이 아직 명확하지 않은데, 클로저/스레드 부분에 대해 좀더 파봐야겠다. 가장 급한 부분은 autosizing이다.

#### 22/6/18 ios 랜덤메뉴앱 헤딩

- codable 프로토콜을 채택해 JSON 디코드용 모델을 만들어줬다.
- URLSession, URLRequest, dataTask, @escapint closure를 사용해 비동기로 http 통신을 수행하고 결과값을 클로저 밖으로 빼냈다.
- segment control로 검색조건을 입력받았다.
- location manager로 현재위치를 확인했다.
- 이제 taskview와 scrollview를 사용해 결과값을 화면에 뿌려주면 된다.

#### 22/6/17 메모리관리(finalizer, cleaner, 참조해제 등)

finalizer, cleaner는 제대로된 동작을 보장하지 않는다. try-with-resource 구문을 사용하자.

#### 22/6/16 의존객체주입

의존객체를 필드에 미리 정의하기보다, 생성자나 메서드로 주입받을 수 있게하자.

#### 22/6/15 싱글턴 보장하는 방법

enum으로 정의하면 자바에서 한번만 생성되게끔 보장해준다.

#### 22/6/14 팩터리 메서드, 빌더

생성자 대신 팩터리 메서드를 써보자. 대신 상속이 안된다. 기본 생성자가 private이기 때문. 그리고 필드가 많으면 빌더를 고려해보자.

#### 22/6/13 swift 메모리에 남지 않는 문자열

swift는 rc 방식으로 컴파일할 때 메모리 해제 시점을 알 수 있다. 그래서 deinit에서 문자열과 같은 크기의 더미데이터로 덮어쓰는 로직을 추가하면, 안전하게 힙영역에 쓰레기값이 남지 않게 할 수 있다.

#### 22/6/2 swift mapkit

#### 22/5/15 swift webkit

#### 22/5/12 swift 프로퍼티/프로토콜 등, 프로그래밍 언어를 처음 배울 때만큼 새롭고 신기하다

저장프로퍼티는 값을 저장만 한다. 연산프로퍼티는 getter/setter에서 수행할 연산을 정의해줄 수 있다. 타입프로퍼티는 자바의 클래스 스태틱 멤버와 같고, 서브클래스에서 재정의 할 수 있는지도 옵션으로 줄 수 있다. 저장프로퍼티 및 부모클래스의 연산프로퍼티를 오버라이드하는 경우 프로퍼티 옵저버를 사용할 수 있다.

상속은 클래스에서 단일 상속만 가능하다. 확장은 기존 클래스, 구조체, 열거형 타입에 새로운 코드를 먹이는 것이다.

프로토콜은 자바의 인터페이스와 비슷한데, 기본값을 설정할 수 없으며 optional 제한자로 선택적으로 구현할 수 있다.

스위프트에도 자바에서 인터페이스를 사용해 동작을 전달하는 것처럼, 프로토콜을 사용해 동작을 전달할 수 있다.

스위프트에서 `===` 연산자는 두 상수나 변수가 같은 인스턴스를 '참조'하고 있는지 비교하는 연산자이다.

#### 22/5/9 swift는 클래스랑 구조체가 다르고, ARC로 자원을 관리한다

클래스는 레퍼런스 참조라 자바 클래스랑 거의 비슷하고, 구조체는 값 인스턴스라 취급이 다르다. 이를테면 클래스 인스턴스 변수는 그 자신은 바꿀 수 없어도 멤버는 바꿀 수 있다. 그러나 구조체 인스턴스 변수는 그 자신은 물론 멤버 일체도 바꿀 수 없다.

런타임에 가비지 컬렉션을 돌리지 않고, 컴파일 타임에 Reference Count를 확인해서 자원을 해제한다.

#### 22/5/7 swift에는 `;`가 없는 대신에, `@` `#` `?` `!`가 있다

스위프트에는 `;`이 없다. 쓴다고 오류가 나지는 않는데, 굳이 안써도 된다. 그런데 `@` `#` `?` `!`는 있다. `@`는 컴파일러 지시문을 뜻하고, `#`는 스위프트 2 이하에서 파라미터 라벨이 파라미터 이름과 동일할 때 쓰는 기호이고, `?` `!`는 null safety를 위한 옵셔널 형식 관련 기호이다.

익명함수는 `(parameter) -> (returnType) in expression/statement`와 같이 표현한다. 파라미터, 반환타입, in구문 등 상황에 따라 생략할 수 있다.

스위프트에는 인터페이스 대신 프로토콜이 있고, 클래스와 구조체가 따로 있다더라.

#### 22/4

개발교육을 마치고 실무에 투입되었으나 성과가 더디다. 요구사항을 정확히 반영하지 못해 롤백하거나, 로컬에서 제대로 테스트하지 못하고 개발서버에 올렸다가 롤백하는 경우가 왕왕 있다. 

요구사항, 테스트를 구체화하고 싶은데, 뾰족한 방법이 없어 엑셀로 조지고있다. 언제나 조져지는건 나이지만. 뭔가 방법이 없을까!

#### 22/4/7 개발은 디테일하게

개발표준과 코딩규칙을 지키면서 개발하자. 
그런데 개발표준이랑 코딩규칙을 어디서보는거징.

#### 22/4/5 개발은 점진적으로

테스트 가능한 최소 기능을 먼저 개발하자.

- Spring MVC의 요청 처리흐름
  - **Filter 처리**
  - 사용자 요청을 DispatcherServlet이 받음
  - 해당 URI를 Handlermapping에서 검색
    - RequestMapping으로 구현한 API를 찾는데, RequestMappingHandlerAdapter가 모두 가지고 있음
    - 원하는 Mapping을 찾은 경우, **Intercepter를 처리**
    - **Argument Resolver 처리**
    - Message Converter 처리
  - Controller Method 호출

#### 22/4/3 조직도 재귀쿼리

테이블이 ITEM_ID, PARENT_ID 쌍으로 구성되어 있을 때, CTE를 사용한 재귀쿼리로 조직도를 출력한다.

#### 22/3/31 개발은 BUG와 DEBUG 사이의 CODING이다.

Spring에 Mybatis를 물려 조회 기능을 구현했다. 그런데 자꾸만 `Mapped Statements collection does not contain value for` 오류가 났다. 신입이 버그 잡는 데 쩔쩔매고 있으니 내 위로 세 사람이 퇴근도 못하고 같이 머리를 맞대고 고민했다. 너무 감사하면서도 죄송스러웠다..

예상되는  원인은 다음과 같았다. <u>xml 파일을 찾지 못했거나</u>, <u>쿼리 매핑 네임스페이스나 id를 잘못 지정</u>했거나, <u>파라미터/리턴타입 VO 멤버 형식/이름규칙이 맞지 않거나</u>, 해당 <u>VO가 스캔 범위에 포함되지 않았</u>거나.

역순으로 찾아나갔다. config 파일에서 VO가 스캔 범위에 포함되어 있는지 확인하고, VO 멤버 형식과 이름을 확인하고, dao와 xml에서 매핑 네임스페이스와 id를 확인했다. 첫 번째로, VO가 BaseVO를 상속하지 않아 필요한 멤버가 없었다. 두 번째로, mybatisd의 multiSelect 메서드를 사용하는데 매핑 네임스페이스 마지막에 온점을 찍지 않아 제대로 참조할 수가 없었다. 세 번째로, 컨트롤러에서 결과값을 받는 VO 형식을 잘못 지정해주고 있었다. 총체적 난국이었다. 마지막으로 application.properties에서 xml이 잘 매핑되어 있는지 확인했다. 여기서 오류 원인을 찾을 수 있었다. *.xml로 매핑되어 있었는데 나는 파일을 *.XML로 만들었던 것이다. 파일 이름을 바꾸고, 클린/빌드하니 오류가 해결되었다.

버그 하나 넘어가니 또 만나는 새로운 버그. 이제는 프론트에서 오류가 터져나왔다. 그럼에도 불구하고, 문제를 해결해나가는 과정이 즐겁고 기쁘다. 늘 하고 싶었던 일이니까. 다만 빠르게 실력이 커나가기만을 바랄뿐이다.

#### 22/3/30 저장 프로시저2

트랜잭션 커밋/롤백, TRY/CATCH, WHILE 사용법을 익혔다. 며칠안에는 트랜잭션 격리수준(?)에 대해 정리해두자.

#### 22/3/29 저장 프로시저

동적으로 쿼리를 작성하는 대신에 저장 프로시저를 매번 ALTER해서 사용한다면, 저장 프로시저를 사용하는 의미가 있는 걸까? 매번 실행계획도 새로 컴파일될텐데 말이다. 

ANSI_NULLS, QUOTED_IDENTIFIER, BEGIN/END, CONVERT, WITH에 대해 정리했다. Read Committed, Read Uncommitted 등 격리수준에 대한 부분을 더 살펴봐야한다.

#### 22/3/28 다중 아우터 조인

다른 테이블을 참조하는 칼럼이 여러 개 있을 때, 다중 아우터 조인으로 해당 테이블 값을 한 번에 가져올 수가 있다.

#### 22/3/24 스프링 어노테이션 정리

스프링 네 가지 필수 어노테이션 repository, service, controller, autowired. 이 중에 repository와 service가 실상은 아무 기능이 없다는 점에 놀랐다.

#### 22/3/23 맥에서 윈도우 연습서버 띄우기 헤딩, 결론: 불가

m1에서는 아직까지는 공식적으로 vmware, virtualBox를 사용할 수 없다. 다만 vmware는 m1 프리뷰 버전이 22년 10월까지 무료로 지원된다. 그러나 해당 프리뷰 버전은 ms server를 지원하지 않는다.

결론적으로 윈도우 연습서버를 띄우려면 클라우드 호스팅서버를 사용하거나(월 7천원 ~ 7만원까지 다양하다), 정년퇴임을 앞둔 윈도우 노트북을 예토전생시키는 수밖에 없다.

#### 22/3/22 맥에서 윈도우 연습서버 띄우기 헤딩

도커 데스크탑에서 ms sql 서버를 띄운 linux 컨테이너를 구동해보기. 여기서부터 고통의 굴레가 시작됐다. m1에서 해당 이미지를 지원하지 않아 도커와 이미지를 모두 지웠으나, 이후 도커를 재설치 했을 때 아예 도커도 구동되지 않는 문제가 있었다. StackOverflow에서 도커 완전삭제 명령어를 검색하여 해결. 

#### 22/3/12 알고리즘 문제풀이

나머지 연산은 더하기, 빼기, 곱하기에 대하여 분배법칙이 성립한다. 나눗셈 연산의 경우에는 분배법칙이 성립하지 않기 때문에, 곱셈의 역원을 활용해야 한다.

- 나머지연산의 분배법칙
  - `(A + B) % C == (A%C + B%C) % C`
  - `(A - B) % C == (A%C - B%C) % C`
  - `(A × B) % C == (A%C × B%C) % C`
  - `(A / B) % C == (A × B^-1) % C == (A%C × B^-1%C) % C`

#### 22/3/9 신입사원 사전과제 제출 

알록달록 PPT 오랜만이다.

#### 22/3/3 뷰/스프링 로그인/게시판 기능통합 헤딩3

뷰2에서 뷰3로 마이그레이션 중이다. 라우터를 더 높은 버전으로 인스톨했지만, 사용할 때 차이점은 없었다. 쿠키 관련 라이브러리를 바꾸었고 코드 가독성이 더 좋아진 것 같다. `vue-cookies`에서 `vue-cookie-next`로 바꾸었고, 보안 설정할 때 인수를 JSON 형식으로 보낼 수 있어서 인수목록 순서를 외울 필요가 없어졌다. 부트스트랩은 뷰3 버전이 만들어지는 중이라 일부 기능이 지원되지 않는다. 간단한 컴포넌트 사용에는 무리가 없을것 같다. 

안드로이드 스터디에 참여했다. 첫 시간에는 '코드작성의 편리함'과 '기능상 효율성'을 구분지어 생각하자는 내용으로 스터디 리더가 주제 발표를 했다. 이를테면 액티비티 `onCreate`에서 `onClickListener`를 분리하려는 상황을 가정했다. 코드작성의 편리함을 생각한다면 코드의 반복과 빠른 변경주기를 고려해 코드를 분리한다고 말할 것이고, 반면 기능상 효율성을 생각한다면 함수가 로딩되며 할당되는 자원을 절약하고, 해당 함수를 호출하고 생성하는 시점을 정밀하게 제어한다는 관점에서 설명할 것이다. 이 둘의 차이를 분명히 알고 개발해나가자는 내용이었다. 꽤 인상깊었고 몇 가지 관련 과제를 받았다.

이펙티브자바, 클린코드, 두 가지를 몇 달 안에 공부해봐야겠다. 우선은 오래 미뤄왔던 디자인패턴 개념을 배우는 것도 급하다.

#### 22/3/1-2 뷰/스프링 로그인/게시판 기능통합 헤딩1-2

더디게 더디게 성장하고 있다. 그래도 의존성주입/제어의역전 개념을 이해한 상태로 Vue/spring-boot로 CRUD REST API를 만들었다. spring-boot에서 컨트롤러/서비스/SQL매퍼를 구현했고, Vue에서는 router/axios로 서버측에 접근해 토큰은 쿠키에 저장했다. DAO/DTO/VO로 컨트롤러/서비스에서 객체를 매핑해줬다. n:n관계 테이블은 매핑 테이블을 하나 둬서 1:n으로 풀어줬다. 이제 남은 과제는 라우터에서 이동할 때 인증 필요한 페이지인지 확인하고 토큰으로 인증수행하기, 그리고 기능별로 프론트 페이지 작성하기.

#### 22/2/27 모던자바 스터디 끝! :book:

모던자바인액션 20, 21장을 읽었다. 모던자바 스터디는 오늘부로 끝이 났다. 람다가 무엇인지, 그리고 어디에 사용할 수 있는지 알 수 있었던 것이 가장 큰 수확이다. 다만 모던자바인액션은 거의 람다 만능주의라고 불러도 될 정도로 모든 코드를 람다를 사용해 추상화했는데, 코드가 배로 많아지고 또 복잡해져서 실무에서 람다를 사용하는 것이 어떤 이점이 있는지는 직접 부딪쳐 보면서 배우는 수밖에 없을 것 같다.

그동안 배운 내용을 정리해서 깃헙에 올려보자. 그리고 어떤 공부가 더 필요할지 고민해봐야겠다. 디자인패턴이나 프로젝트 아키텍처, 이펙티브자바, 또는 DDD/TDD/BDD 등 관심이 간다.

#### 22/2/26 모던자바 함수형 패러다임 개념공부, 로그인 기능 코드리뷰

모던자바인액션 17, 18장을 읽고, 19장 내용을 정리해서 발표 스크립트를 작성했다. 사 년 전 자바8이 처음 발표되었을 때, 람다를 소개하는 글을 몇 번 읽은 적이 있었다. 도무지 이해가 가지 않고, 무엇보다도 어디에 쓰는지 알 수 없었다. 이 책을 읽으면서 어렴풋이 개념이 잡혔다. 람다는 `()->{}`와 같이 함수를 간략히 표현한 것이다. 함수형 패러다임을 적용하면, 부수효과가 없고 참조투명한 함수를 만들 수 있어서, 테스트하기 쉽고 운영중 예기치 않은 오류를 피할 수 있다.

스터디 모임에서 이번주 동안 만든 로그인 기능을 리뷰했다. JWT 토큰에 사용자 아이디와 권한 정보를 함께 넣어서 발급한 부분을 지적받았다. 사용자 아이디만 있다면, 토큰이 유효한지 확인하고 데이터베이스에서 해당 사용자의 권한을 확인해 적용하면 된다는 지적이었다. 클레임을 어떻게 암호화할지 고민했는데 그편이 보안상 더 안전할 것 같다.

커스텀필터를 적용한뒤 CORS 예외 규칙이 적용되지 않는 문제는 여전히 해결하지 못했다. 어제 구현한대로 REST컨트롤러에서 login을 처리해주는 방식으로 로직을 바꾸었다.

#### 22/2/25 뷰/스프링 게시판 로그인 헤딩4

커스텀 필터를 추가하니 WebMvcConfigurer와 WebSecurityConfigurerAdapter에서 설정한 CORS 규칙이 적용되지 않았다. 폼 로그인에서 HTTP POST 요청을 보내니 CORS 때문에 요청이 거부되었다고 오류가 나온다. 커스텀 필터를 걷어내고 REST 컨트롤러에서 ID/PW를 받아 토큰을 발행하는 것으로 수정했다. 

응답헤더에 Authorization에 담겨 반환하는데, JS에서 응답헤더를 읽을 수 없으므로 응답바디에 추가해서 보냈다. 

- 남은과제들: 토큰 내부정보 암호화, CSRF토큰, HttpOnly, Referrer체크, 토큰을 이용해서 게시글 수정/삭제 권한부여

#### 22/2/24 뷰/스프링 게시판 로그인 헤딩3

드디어 SpringSecurity에서 UsernamePasswordAuthenticationToken으로 JWT토큰을 발급하고 응답헤더에 넣어 전달하는 데까지 완성했다. 예제를 보고 따라한 수준이므로, 라이프사이클을 더 공부해야한다.

토큰방식 인증은 분산환경에 보다 유연하게 사용할 수 있다. 그러나 세션 아이디 보다 문자열 길이가 길고, 토큰 내부에 사용자 정보를 담고 있어 탈취시 정보가 노출될 수 있고, 한 번 발급된 토큰은 서버에서 취소할 수 없어 미리 유효기간을 정해야하는 등 문제점이 있다.

DAO는 실제 데이터베이스에 접근하는 객체이다. 도메인 로직에서 데이터베이스에 CRUD하는 비즈니스 로직을 숨기기 위해 사용한다. DTO는 컨트롤러/뷰/비즈니스/서비스 등 계층간 데이터 교환을 위한 객체이다. VO는 DTO와 동일한 개념이지만 읽기전용이다.

- 내일은 : JWT토큰 내부정보 암호화, 사용자 인증정보에 따라 게시글 수정/삭제 권한부여 [X]

#### 22/2/23 뷰/스프링 게시판 로그인 헤딩2

#### 22/2/22 뷰/스프링 게시판 로그인 헤딩

#### 22/2/21 면접준비2

#### 22/2/20 면접준비

#### 22/2/19 코테와 휴식:coffee:

#### 22/2/18 뷰/스프링 게시판 만들기 헤딩4

controller, service, mapper, mybatis sql을 사용해서 사용자 및 게시판 등록/조회/삭제/수정은 이제 가능하다. 그런데 mybatis로 join 연산하는 방법은 잘 모르겠고, 특히 사용자 인증/권한 관리 부분은 정말 잘 모르겠다. 코드만 보기보다 SpringSecurity 클래스를 공부해봐야겠다.

문서 없이 레거시 코드를 고친다는게 얼마나 어려운 일인지.. 알게된 하루..

#### 22/2/17 뷰/스프링 게시판 만들기 헤딩3

vue-bootstrap의 skeleton을 사용해서 로딩화면을 조금더 멋지게 만들었다. 회원가입 기능을 추가했는데, 사용자가 입력하지 않지만 서버측에서 초기화해줘야 하는 값들을 제대로 처리하지 못하고 있다. 현재는 임의 문자열을 넣어두었다.

java에서 finally 구문에 return을 넣으면 예외처리 구문이 무시될 수 있다.

mysql/mariadb에서 last_insert_id()는 클라이언트별로 가장 최근에 성공적으로 삽입된 행의 AUTO_INCREMENT 값을 반환한다. 그래서 스레드 안전하며, 충돌이 발생할 우려가 없다. 다만, AUTO_INCREMENT 없는 테이블이거나, 행 추가가 실패하면 0을 반환한다. 여러 행을 추가하는 경우 첫 행의 AUTO_INCREMENT 값이 반환된다. 마지막으로 트랜잭션을 롤백해도 AUTO_INCREMENT는 유지됨에 유의.

#### 22/2/16 뷰/스프링 게시판 만들기 헤딩2

axios로 외부 API에 http요청을 보낸다. 중첩된 router를 사용해서 헤더/메뉴/메뉴별화면을 만들었다. created에서 api를 호출하면 화면이 깜빡일 동안 데이터가 나오지 않았는데, mounted 시점에 호출하면 화면이 깜빡이지 않았다. 그런데 created/mounted의 라이프사이클별 기능을 생각해본다면 순전히 우연인 것 같다. 로딩화면을 좀더 세련되게 바꾸고 싶어 찾아보니 bootstrap의 skeleton을 사용하면 되더라. 

cors 문제를 해결하기 위해 vue 설정파일에서 proxy를 설정해줄 수 있다. babel 설정파일에서는 모듈 alias를 설정해줄 수 있다.

람다를 사용해 컴포넌트를 지연로딩할 수 있다. () => import ('컴포넌트경로')

중첩 라우터에서 부모 컴포넌트에도 router-view를 추가하는 것을 몰라 한참 헤맸다. 

#### 22/2/15 뷰/스프링 게시판 만들기 헤딩

vue router와 컴포넌트를 사용해서 SPA를 만들 수 있다. router-link는 화면에 a 태그로 변환되어 표시되고, router-view는 갱신된 URL에 해당하는 화면을 보여준다. 여러 컴포넌트를 한 페이지에 불러올 수 있고, 여러 컴포넌트를 중첩해서 표시할 수도 있다. 

axios는 promise 기반으로 비동기 http 통신을 지원한다. resolve/then/catch 메서드로 작업완료시/성공후/에러발생시 처리할 작업을 지정해줄 수 있다. 공공데이터포털은 CORS 때문에 웹에서 바로 접근해 데이터를 가져오지 못한다([내가 찾은 CORS Error의 올바른 해결법](https://coding-groot.tistory.com/91)) 프록시 서버를 두고 대신해서 가져오도록 하면 된다.

조합형 글자는 v-model에서 엔터, 스페이스바를 눌러야 데이터가 동기화된다. 그래서 마지막 글자가 잘릴 수 있다. v-on에서 input 이벤트를 감지해 데이터를 바인딩해주면 해결할 수 있다.

vue 프로젝트에서 app.vue는 최상위 컴포넌트이고, main.js는 가장 먼저 실행되는 js파일이다. main.js에서 app 컴포넌트가 생성된다.

#### 22/2/14 CompletableFuture 사용법을 훑어보고, REST API 사용방법을 연습해보았다.

**모던자바** CompletableFuture는 Future의 구현클래스로서, 두 개 이상의 Future를 블로킹 없이 연결하여 수행할 수 있다. andThen, thenBoth 등 메서드를 사용한다. 리액티브 프로그래밍은 어렵구나, 복잡하게 보지말고 CompletableFuture의 사용법을 배운다고 생각하자.

오늘의 알골 : 2022 카카오블라인드 2차과제 헤딩 / FAIL, 그러나 HttpURLConnection에서 헤더/바디에 데이터 추가하는 방법, JSONArray 객체 순회하는 방법을 알 수 있었다. 정답이 웹에 나와있는 엘리베이터 문제를 복기해보고 다시 도전해보자. 

지금처럼 공부해왔더라면 더 많이 성장할 수 있었을텐데 아쉬움이 늘 남는다. 그러나, 그럼에도 불구하고, 그렇기 때문에, 오늘은 오늘의 공부를 하는 수밖에 없다.

#### 22/2/13 리액티브 프로그래밍이란

**모던자바** 반응형 웹이란, 태블릿/폰/PC 등 사용자 환경에 따라 화면을 재구성하는 것이다. 반면 리액티브 프로그래밍이란, 런타임 환경이 변화에 대응하도록 전체 아키텍처가 설계된 프로그램이다. 리액티브 시스템을 세 가지 속성을 지켜야 하는데, 첫째로 큰 작업을 처리하느라 간단한 질의의 응답을 지연하지 않고 실시간으로 입력에 반응해야 한다. 둘째로 한 컴포넌트 실패로 전체 시스템이 실패하지 않아야 한다. 셋째로 시스템이 작업 부하에 맞게 작업을 효율적으로 처리해야 한다.

오늘의 궁금증 : CompletableFuture의 complete는 용도가 뭘까? future.get은 결과를 무한정 기다린다. completable.complete으로 결과가 나오면 completable.get을 호출하여 안 기다려도 된다. 맞나?

#### 22/2/12 뷰는 간단하게 배우고 멋진 화면을 만들 수가 있구나

**뷰/스프링 프로젝트 Q&A게시판 만들기 리뷰**: mybatis에서 insert한 값을 매핑해서 받아올 수 있다. 등록한 게시글 일련번호를 새로운 쿼리로 조회하거나 게시판 max(글번호)와 같이 구현할 필요가 없다. checkbox를 체크하지 않으면 null인 것은 맞지만, vue 데이터 바인딩에서 디폴트 값을 정해줄 수 있기에 새로 분기를 세우고 초기화해줄 필요가 없다. 코드리뷰 왕사랑!

**뷰/웹 기본개념**: DOM이 수정될 때마다 브라우저는 전체 DOM을 새로 렌더링한다. 성능저하 방지를 위해 실제 DOM 접근은 지양해야 한다. 가상 DOM은 변경된 부분만 새로 렌더링한다. 다만, 일부 엘리먼트의 경우 접근하는 것만으로 전체 DOM이 새로 렌더링 되는 경우가 있으니 유의바람.

JS는 변수/함수 호이스팅을 지원한다. 선언시 메모리 공간을 먼저 할당해주고, 초기화할 때 값을 채워넣는다. 그래서 함수를 정의하기 전에 호출할 수 있고, 변수를 초기화하기 전에 접근할 수 있다. 다만 var는 undefined로 미리 초기화되어 있으나 const/let은 메모리공간만 할당되므로 초기화전 접근하면 에러가 난다.

스프링의 제어의 역전이란, 전에는 개발자가 객체 의존관계 등을 모두 제어해줬는데 이제는 서블릿 등 컨테이너에서 대신 해준다는 뜻이다. 의존관계를 설정하는 방법은 의존성 검색과 주입 두 가지 방법이 있다. 의존성 검색은 빈에서 필요한 객체를 찾아 매핑하는 경우고, 의존성 주입은 설정파일 등에 필요한 객체를 미리 정의해두면 자동으로 주입해서 사용하는 것이다. 객체 생성시점에 주입하는 생성자 방식, 멤버세터 호출시 주입하는 세터 방식 두가지로 나뉜다.

컴포넌트는 vue 인스턴스에 지정해 전역 컴포넌트로 만들어 호출하는 방식, vue 파일에 지역 컴포넌트로 만들어 호출하는 방식이 있다. 부모에서 자식으로는 props를 내려 데이터를 보내고, 자식은 부모에게 emit으로 이벤트를 올려 데이터를 보낸다. 같은 레벨 컴포넌트는 공통부모로 데이터를 보내 다시 받는 과정이 필요하다. 이벤트 버스를 사용해 지정된 컴포넌트끼리 데이터를 주고받을 수 있다. 이때 의존관계와 상태를 추적하기 위해 vuex라는 유용한 라이브러리도 사용한다.

**모던자바** 도저히 머리에 안들어온다. Future, 스레드풀, 메시업, 마이크로 서비스 등 새로운 내용이 많다. 이 부분을 배우면 이른바 '리액티브 프로그래밍'에 한 걸음 다가갈 수 있겠다. 모던자바인액션은 함수형/리액티브 프로그래밍 입문서로 최고다.

오늘은 SQL, 내일은 알골

[Advanced Join - Symentric Pairs (HakerRank)](https://www.hackerrank.com/challenges/symmetric-pairs/problem?isFullScreen=true) 헤딩

#### 22/2/11 뷰/스프링 프로젝트 게시판 만들기 헤딩3

뷰 튜토리얼을 봄.

```
export/import
vue-router
data/methods/lifeCycle hook/computed/watch
template/div
v-model
v-value
v-on
v-if
v-show
v-for
```

#### 22/2/10 뷰/스프링 프로젝트 게시판 만들기 헤딩2

게시글 등록후, 등록한 게시글을 조회하는 로직이 마음에 들지 않는다.

- **오늘의 bugfix**
  - 게시글 등록완료를 알리는 팝업이 유지되지 않음
    - 1차 팝업 후 곧바로 다음 메서드가 실행되는 것으로 착각해서 로직 순서를 바꿈.
    - 2차 알고보니 게시글 등록후 서버측 예외가 발생해서 팝업이 뜨기전 종료된 것이었음. 로직 순서를 원래대로 원복함.
  - 게시글 수정 화면에서 비밀글 체크가 해제됨
    - 1차 DB에 저장된 Y/N값을 프론트로 넘겨줄 때부터 TRUE/FALSE로 바꾸어 전달.
    - 2차 프론트와 서버측에서 다른 곳에서 해당 멤버를 Y/N값으로 여기고 처리하고 있어서 모두 바꿀 수는 없어 원복함.
  - 페이징 기능
    - 인수를 전달하지 않아 오류 발생. 고침.
  - 게시글 등록후 등록한 게시글 화면이 아니라 글 목록으로 넘어감
    - 프론트에서는 게시글 번호를 서버측으로 넘기지 않음. 그런데 서버측에서 프론트에서 받아온 데이터로 게시글 번호를 조회해서 오류가 발생함.
    - 가장 좋은 방법은 게시글 등록후 해당 글의 일련번호를 받아 조회하는 것이지만, 로직이 그렇게 되어 있지 않아서 게시글을 등록한 사용자의 가장 최신글을 조회하는 것으로 바꿈.
    - 다른 개발자가 구현한 게시판은 게시판의 가장 최신글을 조회하는 것으로 되어 있음.

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
```sql
-- 오라클문법 다중조인
select x.컬럼이름A, 
       y.컬럼이름B,
       z.컬럼이름C, ...
from 테이블이름X x, 테이블이름Y y, 테이블이름Z z, ...
where x.컬럼이름M=y.컬럼이름N
  and y.컬럼이름O=z.컬럼이름Q;
```
```sql
-- ANSI문법 다중조인
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
  - [한번에 끝내는 U buntu 웹서버세팅 (우분투 서버세팅) – Lael World](https://blog.lael.be/post/73)
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

```java
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
