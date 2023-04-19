# 공부일지

<br/>
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

* 템플릿 메서드 패턴
  * 변하는 부분(핵심 기능)과 변하지 않는 부분(추가 기능)을 분리하는 방법
* 전략 패턴
* 템플릿 콜백 패턴
* 프록시 패턴
* 데코레이터 패턴
* ThreadLocal
  * 해당 쓰레드만 접근할 수 있는 저장소
  * 해당 쓰레드가  쓰레드 로컬을 모두 사용하면 remove를 호출해서 저장된 값을 제거해야한다
</div>
</details>
