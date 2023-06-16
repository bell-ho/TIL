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
* next/Link
  * 최초 실행시 해당 페이지 html을 불러옴 페이지에서 Link태그 이용시 더 이상 추가적인 html을 받아오지 않음 (자바스크립트 파일만 가져옴) ~a 태그를 이용할 땐 매번 html을 받아와야함~
    * 즉 최초 실행은 SSG로 실행되지만 페이지를 라우팅할 때는 CSR로 빠르게 이동함
  * next/link 는 특정 영역으로 들어와야 파일을 불러옴 => 불필요한 네트워크 요청을 지양함
* ISR 증분 정적 재생성
  * 어느 정도의 주기로 정적 페이지를 다시 렌더링함
* 이미지 최적화
  * 모듈 loader : 'akamai' , vercel로 배포하는 경우 loader 속성 필요 없음
* .next 폴더
  * 네트워크에 보이는 html과 자바스크립트 파일은 .next 폴더에 있음
  * cache, server, static 폴더
    * static / chunk / pages 안에는 getStaticProps-해시값의 이름의 자바스크립트 파일이 있음, 브라우저는 이것을 다운로드함
    * server / pages 안에는 html과 json이 있음
* next/image
  * 서버에서 자동으로 이미지 용량 최적화를 해줌 => webp 형식이기때문
  * quality props를 통해 얼마나 최적화 할지 정할 수 있음 기본은 75
  * placeholder="blur" 를 하면 blur 이미지가 자동으로 적용됨
  * next/image는 외부 이미지의 높이와 너비를 알 수 없음 그래서 빌드타임에 최적화 하지 못함 => 외부 링크를 사용할 때는 width와 height를 넣어야함
    * 가로 세로 크기를 모르는 외부링크를 사용시 fill 속성을 사용하고 부모 태그로 감싼뒤 position을 relative/absolute/fixed 등으로 설정하고 부모의 사이즈를 설정함
  * 사진이 납작해 보일 때는 objectFit 속성을 추가하면됨 contain 또는 cover
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
