---
{"dg-publish":true,"dg-path":"terms/rest","permalink":"/terms/rest/","dgPassFrontmatter":true,"noteIcon":"","created":"2024-01-01T15:28:41.025+09:00","updated":"2026-02-02T09:13:04.811+09:00"}
---


# REST(Representational State Transfer)
- REST는 그 자체로는 HTTP API에 대한 설계 원칙을 의미한다. 따라서 REST API를 이해하기 위해서는 먼저 [[02-resources/01-dev/20-publish/01-digital-garden/terms/API\|API]]와 HTTP를 어느 정도 이해하고 있어야 한다.
- REST 원칙에 부합하는 정도를 단계별로 나는 [[02-resources/01-dev/01-concepts/Richardson Maturity Model\|Richardson Maturity Model]]이라는 것이 있다. 성숙도라고 보통 표현한다. 여기서 가장 높은 단계를 표현하는 것이 바로 [[02-resources/01-dev/01-concepts/HATEOAS\|HATEOAS(Hypermedia as the Engine of Application State)]]다.

## 참고
- [Richardson Maturity Model - martinfowler.com](https://martinfowler.com/articles/richardsonMaturityModel.html)



	What
RESTful API 라는 말을 많이 들어보았을 것이다.

R

Why
왜 API는 RESTful 해야 하는가?

How

who where when

## 이전 글
### 선수지식
- api가 뭔지 알고 있다. -> 다른 질문으로 바꿔보기
  - 본인이 쓰고 있는 언어의 API 종류를 말해보자.
  - SDK와 API

  
    - http의 구조에 대해 알고 있다.

        - 구문 형식에 대해 말할 수 있다.
        - http method의 종류에 대해 알고 있다
        - status코드에 대해 알고 있다.
        - url과 uri를 구분할 수 있다.

- api에 대해 알아보자
    - sdk와의 차이점은?
    * sdk는 특정 목적을 가진 api의 집합 정도로 이해할 수 있다.
    * 인터페이스란 무엇인가.
    * 차량의 계기판, 비행기 시뮬레이터 같은 것, 버튼 하나로 운행하지만 그 내부 동작은 알지 못한다. 알 필요도 없다. 어찌 명명하자면 오퍼레이션 인터페이스 정도로 생각할 수도 있다.
    * 인터페이스의 또 다른 것 유아이. 화면을 보고 유아이라고 한다. 유저 인터페이스. 사용자는 사용할 뿐. 유액스 등을 고려하자고 한다. 인터페이스에 기대하는 기본적인 동작이 있는 것.
    * 프로그래밍 인터페이스 도 마찬가지. 프로그래밍을 위해 필요한 인터페이스를 에이피아이 라고 하는 것이다.
    * 백엔드 개발자가 에이피아이 서버를 개발한다는 이야기가 많음 프론트에서는 인터페이스를 가지고 정보를 조작하는 유저 인터페이스를 개발한다. 

    * 무엇과 무엇의 간결한 연결 을 지원한다.

* 나아가서
    * 그렇다면 개발자를 업으로 삼는 사람들은 api에 대해 뭘 더 알아야 할까. 이런 기본적인 기대 값이 무엇인가를 알아야 할 것. 서버 애플리케이션에 있어서 그것이 rest임 2022년도 기준. Rest는 다른 글이에서 알아보자.

  

  

http에 대해 알아보자
 Api가 비즈니스 트랜잭션의 단위로 나누어지는 경향이 있다.

  

### 개요

http기반 api의 설계 원칙이다.
이유 

인터페이스가 각기 다른 생김새를 하고 있으면 비효율이 발생한다. 엘레베이터 자동차 등 인터페이스를 거의ㅡ통일 시킨다. 만드는 사람의 입장에서도 인터페이스를 따르는 것을 기준으로 업무에 대한 의사결정을 할 수 있다. 퀄리티의 기준이 되기도 한다.

다만 소프트웨어가 항상 겪는 문제, 추상적이기 때문에 원칙에 대한 해석이 제각각이다. 만들어진 물체는 그렇지 않지만 논리적 개념은 통일이 쉽지 않다.

규칙에 대해
- Representational state transfer
- 마치 MVC처럼 원칙의 집합이다.
    - 원칙의 리스트는 다음과 같음

- 이에 대한 판단의 척도 하나가
    - 리차드슨 성숙도 모델
        - [https://johngrib.github.io/wiki/richardson-maturity-model/](https://johngrib.github.io/wiki/richardson-maturity-model/)



참고
- [Day1, 2-2.  그런 REST API로 괜찮은가 - YouTube](https://www.youtube.com/watch?v=RP_f5dMoHFc&ab_channel=NAVERD2)