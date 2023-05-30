# 공부일지

<br/>
<details>
<summary>클린코드</summary>
<div markdown="1">
 
* 표면적 수준에서 개선
 
</div>
</details>

<details>
<summary>Next.js</summary>
<div markdown="1">

* SSR 서버 사이드 렌더링
  * 서버에서 페이지를 렌더링하여 생성한 페이지를 클라이언트에 전송 => 
  <br> 브라우저는 페이지에서 요청한 스크립트를 다운로드하고 DOM 위에 하이드레이션함
* SSG 정적 사이트 생성
  * 빌드 과정에서 정적 페이지를 미리 렌더링해서 HTML 마크업 형태로 제공함
  * 개발 환경에서는 매요청마다 getStaticProps가 실행됨
  * revalidate : 이미 빌드가 완료된 사이트에서 주기적으로 정적인 페이지를 업데이트함 (해당 페이지만 업데이트하기 때문에 전체 페이지를 빌드할 필요가 없어짐)
* ISR 증분 정적 재생성
  * 어느 정도의 주기로 정적 페이지를 다시 렌더링함
* 이미지 최적화
  * 모듈 loader : 'akamai' , vercel로 배포하는 경우 loader 속성 필요 없음

</div>
</details>
<details>
<summary>Code</summary>
<div markdown="1">

* 단일 책임 원칙 (SRP)
  * 변경 지점을 하나로 모아서 변경에 쉽게 대처할 수 있는 구조

</div>
</details>

<details>
<summary>Next.js</summary>
<div markdown="1">

* SSR 서버 사이드 렌더링
  * 서버에서 페이지를 렌더링하여 생성한 페이지를 클라이언트에 전송 => 
  <br> 브라우저는 페이지에서 요청한 스크립트를 다운로드하고 DOM 위에 하이드레이션함
* SSG 정적 사이트 생성
  * 빌드 과정에서 정적 페이지를 미리 렌더링해서 HTML 마크업 형태로 제공함
* ISR 증분 정적 재생성
  * 어느 정도의 주기로 정적 페이지를 다시 렌더링함
* 이미지 최적화
  * 모듈 loader : 'akamai' , vercel로 배포하는 경우 loader 속성 필요 없음

</div>
</details>

<details>
<summary>Spring</summary>
<div markdown="1">

* Transactional
  * @Transactional(propagation = Propagation.REQUIRES_NEW) : 새로운 트랜잭션을 생성하고 기존 트랜잭션이 있으면 일시 중단, 기능 완료되면 원래 트랜잭션 다시 시작
* 프록시
  * 클라이언트가 서버에 직접 요청 하는게 아니라 대리자를 통해 간접적으로 서버에 요청하는것
  * 접근 제어, 캐싱, 부가 기능 추가, 프록시 체인
* 템플릿 메서드 패턴
  * 변하는 부분(핵심 기능)과 변하지 않는 부분(추가 기능)을 분리하는 방법
* 전략 패턴
  * 변하지 않는 부분을 Context, 변하지 않는 부분을 Strategy라는 인터페이스를 만들고 위임으로 
* 템플릿 콜백 패턴
* 프록시 패턴
  * 접근 제어가 목적
* 데코레이터 패턴
* ThreadLocal
  * 해당 쓰레드만 접근할 수 있는 저장소
  * 해당 쓰레드가  쓰레드 로컬을 모두 사용하면 remove를 호출해서 저장된 값을 제거해야한다
* AOP
  * 어드바이스 : 부가 기능
    * @Before : 조인 포인트 실행 전. 작업 흐름을 변경할 수 없다
    * @AfterReturning : 메서드 실행이 정상적으로 반환될 때 실행
    * @AfterThrowing : 메서드 실행이 예외를 던져서 종료될 때 실행
    * @After : 메서드 실행이 종료되면 실행. finally
    * @Around : 메서드 실행의 주변에서 실행. 메서드 실행 전후에 실행. 가장 강력한 어드바이스. ProceedingJoinPoint 사용
  * 조인 포인트 : 어드바이스가 적용될 수 있는 위치
  * 포인트컷 : 조인 포인트 중에서 어드바이스가 적용될 위치를 선별하는 기능
  * 타겟 : 어드바이스를 받는 객체, 포인트컷으로 결정
  * 에스팩트 : 어드바이스 + 포인트컷을 모듈화 한것
  * 위빙 : 포인트컷으로 결정한 타겟의 조인 포인트에 어드바이스를 적용하는 것
  * 동일한 Aspect에서의 실행 순서 : @Around => @Before => @After => @AfterReturning => @AfterThrowing
</div>
</details>
