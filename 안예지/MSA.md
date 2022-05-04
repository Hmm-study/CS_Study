# MSA (MicroService Architecture)

### Cloud Native Application

- Microservice
- CI/CD
  - 지속적인 통합 CI - 통합 서버, 소스 관리, 빌드 도구 (jenkins,Team CI)
  - 지속적인 배포 CD
- DevOps
- Cotainers

![img](https://user-images.githubusercontent.com/89010467/164701299-df592a26-262c-473c-a39b-0607a696820c.png)

### Monolithic (모놀리식 아키텍처)

> MAS를 알아가기전 모놀리식을 알고가자!
>
> 모놀리식 아키텍처란? 마이크로 서비스 아키텍처의 반대 되는 개념
>
> 하나의 서비스 또는 어플리케이션
>
> 요소간의 의존성이 강하다!

**장점**

- 애플리케이션이 하나의 아키텍처로 이루어져 있어 테스트가 용이
- 빠르게 간단한 서비스를 만들 수 있음
- 서비스 규모가 작으면 유리함

**단점**

- 하나의 작은 수정사항이 있어도 전체를 다시 빌드하고 다시 배포해야함
- 유지보수가 힘들고 프로젝트가 커질수록 구동 시간이 늘어남
- 일부의 오류가 전체에 영향을 미침
- 각 서비스별로 다양한 언어나 프레임워크를 갖는것에 한계가 있음

### SOA(Service Oriented Architecture)

> MSA와 같이 **서비스 지향 설계 방식**
>
> 서비스 단위로 개발을 하고 개발된 서비스들을 공유함으로써 재가용성을 늘리고 유연성 확보
>
> 서비스를 **재사용**에 중점을 둔다!

장점

- 재사용을 통한 비용 절감
- ESB(Enterprise Service Bus) 라는 서비스 채널 이용
- 서비스 단위로 모듈을 분리하여 결합도가 낮아짐
- 버스 형태에 연결만 가능하다면 확장성과 유연성이 증가

단점

- 모듈의 의존성이 줄지만 여전히 결합도는 증가
- 하나의 DB를 사용한다는 점에서 의존성이 존재

## MSA (MicroService Architecture)

> 소프트웨어 개발 기법 중 하나로, 어플리케이션 **서비스**별로 나눔!
>
> 하나의 큰 어플리케이션을 여러 개의 작은 서비스(기능별)별로 쪼개어 조합 구조

**장점**

- 빈번한 업데이트가 필요한 서비스가 있을 때
- 장애로 인해 전체 서비스가 중단 되는 것을 막을 수 있다.
- 기능에 따라 다른 언어를 선택할 수 있음
- 거대한 서비스도 빠르게 수정이 가능

단점

- 체계적으로 준비되어 있지 않으면 오히려 프로젝트 성능이 떨어짐
- DB 또한 개별적으로 운영되기 때문에 트랜잭션으로 묶기 힘듬(트랜잭션 관리 힘듬)
- 서비스간 통신에 대한 오버헤드 발생

📌 Monolithic > SOA > MSA  크기 순

### Spring cloud(스프링 클라우드)

마이크로서비스 구축에 필요한 라이브러리들을 모아 스프링 프로젝트를 제공!

MSA를 지원하기 위한 스프링 프레임워크

1. Spring cloud config
   - 여러 테스트로 환경 설정 후 다시 빌드 하고 배포하는 과정을 방지
   - 설정 파일을 외부로 분리할 수 있도록 함
   - [사용 방법](https://madplay.github.io/post/introduction-to-spring-cloud-config)
2. Spring Eureka
   - Cloud 시스템에서 서비스의 로드 밸런싱과 실패처리 등을 유연하게 가져가 위해 각 서비스들의 IP / Port / InstanceId를 가지고 있는 REST 기반의 미들웨어 서버
   - MSA에서는 IP와 Port가 일정하지 않아 client에 service의 정보를 수동적으로 입력하는 것은 한계가 있다.
   - API 게이트로 들어온 서비스 요청을 어디로 서비스로 보내줄건지 알려준다고 생각하자
3. Spring Netflix Zuul(또는 Gate way)
   - 게이트 웨이 역활
   - 인증 및 권한 부여
   - 로깅, 추적 상관관게
4. **Spring cloud stream**
5. **Spring cloud security**

