## 시맨틱 태그를 잘 쓰고, Role과 Accessible Name을 잘 설정하자.

### 출처 

[모두를 위한 접근성 이야기](https://tech.kakaopay.com/post/accessibility-stories-for-everyone/)

### 계기

조금 더 자세한 웹 접근성 경험 공유를 받고자 읽어보았습니다!

### 배운 내용

#### [접근성 준수의 필요성]

1. 생각해볼만한 질문: 우리 서비스 사용자 중 장애를 가진 사용자는 몇 명일까?
2. 편의 시설은 장애가 없는 사람에게도 도움이 된다.
    - 휠체어 -> 경사로 -> 유모차, 자전거도 쓸 수 있는 경사로
    - 손에 힘을 줄 수 없는 사람들 -> 레버 손잡이 -> 위생이 중요할 때 손을 안쓰고 열 수 있는 문
    - 빛 번짐, 저시력자 -> 다크 모드 -> 눈에 피로가 덜 하게 화면을 보고 싶을 때
    - 스크린 리더 -> Image alt 속성 -> 네트워크, 컨텐츠 차단 등 이미지 표시가 어려울 때
3. 초고령 사회로 진입하며 디지털 소회 계층이 점점 늘어나고 있으므로, 접근성은 모두의 문제로 봐야 한다.
4. 장애인 모바일 사용자를 잠재고객으로 볼 수 있다. 국내는 약 185만명 정도로, 시각장애 25만, 청각장애 40만, 지체장애 120만명 정도이다.
5. 접근성 확보 노력은 사회 공헌적 노력이며, 기업 이미지 향상에 도움이 될 수 있다.
6. "이렇게까지 해야 하나요?" - 접근성은 기술 뿐만 아니라 PM, 디자이너, 개발자 간의 협업 없이 실형하기 어렵다.
    - 접근성을 달성하기 위해서 상당한 개발, 검증 작업이 필요
    - 디자인에 제약이 발생 - 글자 크기, 명조, 폰트, 아이콘 디자인, 문구 등

#### [접근성 준수 방법]

1. 가장 쉽게 접근성을 준수할 수 있는 방법은 웹 표준, 웹 표준의 핵심은 시맨틱 웹
2. 접근성은 브라우징 도구 스크린 리더가 웹을 더 쉽게 이해할 수 있게 하는 것이다.
    - 기계가 웹을 이해할 수 있어야 그 기계를 사용하는 사람도 브라우징을 더 쉽게 할 수 있다.
    - 검색 엔진 역시 기계이기 때문에 시맨틱 마크업이 SEO에 도움이 된다.
3. 시맨틱 태그 별 역할 예시
    - `<header>` - 페이지/글 제목
    - `<footer>` - 컨텐츠 작성자, 저작권 정보, 관련 문서 소개
    - `<main>` - 문서의 핵심 주제를 포함하는 컨텐츠
    - `<article>` - 독립적인 컨텐츠
4. Tag 별로 할당 가능한 Role과 불가능한 Role이 존재한다.
    - `<button>`은 role="checkbox", "radio", "tab" 등을 할당할 수 있다.
    - `<input type="text">` 는 role="textbox"를 가지고 있고, "button" 할당 시 Enter를 눌러도 액션 미발생
5. 꾸밈 요소여도 이미지 설명을 전달할 필요가 있다고 생각이 들면 컨텐츠에 대한 설명을 추가
    - (ex) `기뻐하는 죠르디`
6. 스크린 리더는 `Accessible Name + Role` 형식으로 읽으므로, `Accessible Name`가 적절히 설정되게 만드는 것이 중요하다.
    - `Accessible Name = author || contents`
    - author = `aria-label, aria-labelledby, title, alt, <desc>`
    - contents = textContent
    - (ex) `<button>`은 `author`가 없으면 `contents`를 쓰는데, 이를 `Children Presentational`이라고 한다.
7. `<table>` 접근성 개선 팁
    - 별도의 설정이 없다면 줄글처럼 읽는다.
    - `th`에 `scope=col|row`값을 지정해 각 td에 연관되는 th를 지정해주어야 한다.
    - 각 `td`를 읽을 때 해당하는 `th`를 함께 읽어준다. (즉, 테이블을 줄글로 자동으로 변환한다.)
8. 개발 보조 도구 활용
    - 크롬 개발자 도구 Accessbility 탭
    - WAVE Evaluation Tool, eslint-plugin-jsx-a11y
    - https://wave.webaim.org/
    - https://www.npmjs.com/package/eslint-plugin-jsx-a11y

### 학습 한계

- 태그 별 사용 가능한/불가능한 Role 목록
- 시맨틱 태그의 실질적인 사용법 (중첩 사용 등)

### 활용 방안

시맨틱 태그를 적극적으로 활용하고, 보조 도구들을 활용해 검증하면서 Accessible Name, Role을 더 명확하게 설정해보기
