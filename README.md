# 항해 플러스 프론트엔드 4기 과제 1주차: Chapter4-1 성능 최적화 (1)
- [과제 체크포인트](#과제-체크포인트)
  - [기본과제](#기본과제)
  - [심화과제](#심화과제)
- [과제 셀프회고](#과제-셀프회고)
  - [기술적 성장](#기술적-성장)
  - [코드 품질](#코드-품질)
  - [학습 효과 분석](#학습-효과-분석)
  - [과제 피드백](#과제-피드백)
- [리뷰 받고 싶은 내용](#리뷰-받고-싶은-내용)

## 과제 체크포인트

### 기본과제

#### 1) 라우팅 구현:
- [ ✅ ] History API를 사용하여 SPA 라우터 구현
  - [ ✅ ] '/' (홈 페이지)
  - [ ✅ ] '/login' (로그인 페이지)
  - [ ✅ ] '/profile' (프로필 페이지)
- [ ✅ ] 각 라우트에 해당하는 컴포넌트 렌더링 함수 작성
- [ ✅ ] 네비게이션 이벤트 처리 (링크 클릭 시 페이지 전환)
- [ ✅ ] 주소가 변경되어도 새로고침이 발생하지 않아야 한다.

#### 2) 사용자 관리 기능:
- [ ✅ ] LocalStorage를 사용한 간단한 사용자 데이터 관리
  - [ ✅ ] 사용자 정보 저장 (이름, 간단한 소개)
  - [ ✅ ] 로그인 상태 관리 (로그인/로그아웃 토글)
- [ ✅ ] 로그인 폼 구현
  - [ ✅ ] 사용자 이름 입력 및 검증
  - [ ✅ ] 로그인 버튼 클릭 시 LocalStorage에 사용자 정보 저장
- [ ✅ ] 로그아웃 기능 구현
  - [ ✅ ] 로그아웃 버튼 클릭 시 LocalStorage에서 사용자 정보 제거

#### 3) 프로필 페이지 구현:
- [ ✅ ] 현재 로그인한 사용자의 정보 표시
  - [ ✅ ] 사용자 이름
  - [ ✅ ] 간단한 소개
- [ ✅ ] 프로필 수정 기능
  - [ ✅ ] 사용자 소개 텍스트 수정 가능
  - [ ✅ ] 수정된 정보 LocalStorage에 저장

#### 4) 컴포넌트 기반 구조 설계:
- [ ✅ ] 재사용 가능한 컴포넌트 작성
  - [ ✅ ] Header 컴포넌트
  - [ ✅ ] Footer 컴포넌트
- [ ✅ ] 페이지별 컴포넌트 작성
  - [ ✅ ] HomePage 컴포넌트
  - [ ✅ ] ProfilePage 컴포넌트
  - [ ✅ ] NotFoundPage 컴포넌트

#### 5) 상태 관리 초기 구현:
- [ ✅ ] 간단한 상태 관리 시스템 설계
  - [ ✅ ] 전역 상태 객체 생성 (예: 현재 로그인한 사용자 정보)
- [ ✅ ] 상태 변경 함수 구현
  - [ ✅ ] 상태 업데이트 시 관련 컴포넌트 리렌더링

#### 6) 이벤트 처리 및 DOM 조작:
- [ ✅ ] 사용자 입력 처리 (로그인 폼, 프로필 수정 등)
- [ ✅ ] 동적 컨텐츠 렌더링 (사용자 정보 표시, 페이지 전환 등)

#### 7) 라우팅 예외 처리:
- [ ✅ ] 잘못된 라우트 접근 시 404 페이지 표시

### 심화과제

#### 1) 해시 라우터 구현
- [ ❌ ] location.hash를 이용하여 SPA 라우터 구현
  - [ ] '/#/' (홈 페이지)
  - [ ] '/#/login' (로그인 페이지) 
  - [ ] '/#/profile' (프로필 페이지)
 
#### 2) 라우트 가드 구현
- [ ✅ ] 로그인 상태에 따른 접근 제어
- [ ✅ ] 비로그인 사용자의 특정 페이지 접근 시 로그인 페이지로 리다이렉션

#### 3) 이벤트 위임

- [ ✅ ] 이벤트 위임 방식으로 이벤트를 관리하고 있다.

## 과제 셀프회고

<!-- 과제에 대한 회고를 작성해주세요 -->

### 기술적 성장

> 🎉 새로 학습한 개념

#### 1) History API
History API란 windows.history 객체에 접근할 수 있도록 제공해주는 방법입니다.<br />
사용자의 기록 기록을 탐색하고, 기록 스택의 내용을 조작할 수 있게 해주어 SPA에서 라이언트 사이드 라우팅을 구현할 수 있게 해줍니다.

#### 2) 이벤트 버블링과 캡처링 / 이벤트 위임

##### 이벤트 흐름 3단계
1. 캡처링 단계 (이벤트가 하위 요소로 전파)
2. 타깃 단계 (이벤트가 실제 타깃 요소에 전달)
3. 버블링 단계 (이벤트가 상위 요소로 전파)

- 버블링
  - 한 요소에 이벤트 발생 -> 이 요소에 할당된 핸들러 동작 -> 부모 요소의 핸들러 동작
  - 이 동작을 가장 최상단의 조상 요소를 만날 때까지 반복 및 동작합니다.

- 버블링 중단하기
  - 이벤트 버블링은 타깃 이벤트에서 시작해서 document 객체를 만날 때까지 각 노드에서 모두 발생합니다. 몇몇 이벤트는 window 객체까지 거슬러 올라가서 모든 핸들러가 호출될 수도 있습니다.
  - 이 때 핸들러에게 이벤트를 완전히 처리하고 난 후 버블링을 중단하도록 명령할 수 있습니다.
  - `event.stopPropagation()`

- 캡처링
  - 한 요소를 클릭하면 이벤트가 최상위 조상에서 시작해 아래로 전파되는 것을 말합니다.
  - false - 버블링 단계에서 동작 (기본값)
  - true - 캡처링 단계에서 동작
  - `el.addEventListener(..., {cature: true})`
  - `el.addEventListener(..., true)`

- 이벤트 위임
  - 이벤트 위임은 비슷한 방식으로 여러 요소를 다뤄야할 때 사용됩니다.
  - 요소의 공통 조상에 이벤트 핸들러 단 하나만 할당해도 여러 요소를 한꺼번에 다룰 수 있습니다.

> 🛠️ 기존 지식의 재발견/심화

#### 객체 지향 프로그래밍

- 기본 클래스 정의: 모든 컴포넌트의 기반이 되는 Component 클래스를 정의한 코드 입니다.

```
export default class Component { // 초기 컴포넌트 
    $target;
    state;
    props;
    constructor($target, props = {}) {
        this.$target = $target;
        this.props = props;
        this.setup();
        this.render();
    };
    mounted() {}; // 컴포넌트가 마운트 되었을 때
    setup() {};
    template() {return "";}; // 전체적인 UI 구성
    render() { // UI 렌더링
        this.$target.innerHTML = this.template();
        this.setEvent();
        this.mounted();
    };
    setEvent() {}; // 이벤트 설정
    setState(newState) { // 상태 변경
        this.state = {...this.state, ...newState};
        this.render();
    };
}
```

- 실제 사용 예제: Component 클래스를 상속하여 만든 Header 컴포넌트 입니다.

```
import Component from "../core/Component";

export default class Header extends Component {
  constructor($target, props) {
    super($target, props);
  }

  template() {
    const navItems = localStorage.getItem("user")
      ? [
          { path: "/", name: "홈", id: "home" },
          { path: "/profile", name: "프로필", id: "profile" },
          { path: "/logout", name: "로그아웃", id: "logout" },
        ]
      : [
          { path: "/", name: "홈", id: "home" },
          { path: "/login", name: "로그인", id: "login" },
        ];
    return '
            <div class="bg-blue-600 text-white p-4 sticky top-0">
                <h1 class="text-2xl font-bold">항해플러스</h1>
            </div>
            <nav id="nav" data-component="navigator" class="bg-white shadow-md p-2 sticky top-14">
                <ul class="flex justify-around">
                    ${navItems
                      .map(
                        (nav) => `
                        <li>
                            <a href="${nav.path}" id=${nav.id} class="text-blue-600 font-bold">${nav.name}</a>
                        </li>
                    `,
                      )
                      .join("")}
                </ul>
            </nav>
        ;
  }

  setEvent() {
    document.querySelector("#nav").addEventListener("click", (e) => {
      if (e.target.tagName === "A") {
        e.preventDefault();
        const path = e.target.getAttribute("href");
        this.props.router.navigateTo(path);
      }
    });
  }
}
```

> ❤️‍🔥 구현 과정에서의 기술적 도전과 해결

기존에 주로 함수형으로 코드를 짰었는데, 이번 과제에서는 개인적인 도전의 의미로 전체 코드를 Class 문법으로 구현 해봤습니다.<br />
Component만 클래스 형식을 사용할까 했지만 코드의 일관성을 주기 위해 전체 다 클래스 문법으로 구현했습니다.<br />

원래 함수형으로 코드를 짜는게 익숙해서 그런지 기능을 구현하려고 할 때 처음에 함수형 밖에 떠오르지가 않아서 애를 좀 먹었습니다..<br />
또한, 컴포넌트에 미리 정의해둔 클래스들은 구글링 등 다른 분들의 코드들을 참고해서 작성해서 그런지 전부 사용하지 않고 한 두개 정도의 클래스만 한정되게 사용하여 아쉬운 점이 남아 있습니다.

### 코드 품질

> 🫠 리팩토링이 필요한 부분

#### Router

아무래도 심화 과제인 해시 라우트를 구현하지 못한게 가장 아쉽습니다..<br />
Router에 해쉬 라우트를 구현하니 홈("#/"), 로그인("#/")은 잘 이동하나 프로필("#/profile")만 이동이 안되는 이슈가 있었습니다..<br />
또한 나중에는 브라우저 라우트까지 작동을 안하여 결국엔 롤백 후 과제 제출을 하게 되었습니다.😭

나중에 다른 분들과 준일 코치님의 과제 해설을 보니,<br />
`main.js`와 `main-hash.js`로 라우트를 각각 분리 한 것을 보고<br />
기존 라우터에서 해시 라우트를 추가하는 것이 아닌 따로 구현을 해야하는구나 깨달았고,<br />
전체적으로 Router 컴포넌트 부분이 잘 정리가 안되어 있어 리팩토링이 필요하다고 생각합니다. 

### 학습 효과 분석

> 🙌 가장 큰 배움이 있었던 부분

#### 테스트 코드

평소에 디버깅을 `console.log`나 터미널로만 에러를 확인하는 방법으로 대응 했었는데,<br />
이번에 테스트 코드라는 개념을 처음 익히고 사용해봤습니다.<br />
테스트 코드는 버그를 사전에 발견해 에러를 최소화하고, 코드 품질을 높일 수 있으며 소프트웨어의 안정성을 높일 수 있습니다.

그 중에서 이번 과제를 통해 유닛 테스트와 e2e 테스트를 사용해 보았는데요.<br />
처음에는 테스트를 계속 통과하지 못하여 크게 당황했습니다..<br />
분명 로컬에서는 잘 작동하는데 테스트 통과는 안되니 정말 답답하고 어디서부터 손을 대야하는지 막막하고 지금이라도 처음부터 다시 짤까..? 라는 고민도 수없이 했습니다..

결국에는 상연 학습메이트님께 도움을 청했고, 상연학습메이트님께서 테스트 코드 디버깅 하는 방법과 Jest 확장 프로그램 사용 방법을 자세하게 알려주셔서 기본 과제를 통과할 수 있게 되었습니다.<br />
알려주신 방법으로 혼자 심화과제 디버깅을 해보았고 2, 3번은 무사히 통과하게 되었습니다.

> 💪 추가 학습이 필요한 영역

#### 디자인 패턴

- 팩토리 패턴: 비슷한 객체를 공장에서 찍어내듯 클래스로 캡슐화 처리하여 생성하는 패턴
- 생성자 패턴: 비슷한 속성과 행위를 한 생성자로 묶어 모듈화 하는 패턴
- 싱글톤 패턴: 특정 클래스의 인스턴스를 한 개만 유지하는 패턴
- 빌더 패턴: 객체 생성 과정을 분리하여 순차적이고 직관적으로 만들며 불변성을 유지할 수 있게 해주는 패턴

### 과제 피드백

이번 과제에서 리액트 등의 프레임워크의 감사함을 깨달았습니다.. 😅<br />
리액트에서 손쉽게 구현할 수 있는 기능들을 제가 직접 손수 함수 또는 클래스를 짜서 기능 구현을 해야하니 머리론 알겠는데 어떻게 시작해야하나 처음엔 막막해서 손도 못 대고 코치님께서 제공해주신 학습자료만 수십번 본 것 같습니다...!<br />
역시 돌고돌아 기본이 중요하더라구요..! 자바스크립트 기본적인 것들 실제로 많이 써보면서 이해도와 적응력을 높이는 게 중요하다고 생각합니다!

## 리뷰 받고 싶은 내용

### hash router 
hash router를 구현 하는데, 다른 페이지들은 이동이 잘 되는데 ("#/", "#/login")<br />
"#/profile" 에서만 오류가 나서 이것저것 고쳐보니 모든 라우터 이동이 안되서 결국 롤백 했습니다..! ㅜㅜ<br />
뭐가 문제일까욤..?

![화면 캡처 2024-12-21 142800](https://github.com/user-attachments/assets/16b8c91d-c90b-4066-a2d1-1946a57eada8)
 
```
import MainPage from "../pages/MainPage";
import ProfilePage from "../pages/ProfilePage";
import LoginPage from "../pages/LoginPage";
import ErrorPage from "../pages/ErrorPage";

class Router {
  constructor() {
    this.setRoute();
    this.isLoggedIn = !!localStorage.getItem("user");
    window.addEventListener("popstate", this.handlePopState.bind(this));
    window.addEventListener("hashchange", this.handleHashChange.bind(this));
  }

  setRoute() {
    this.isLoggedIn = !!localStorage.getItem("user");
    this.routes = [
      { path: "/", page: MainPage },
      { path: "/profile", page: ProfilePage },
      { path: "/login", page: LoginPage },
      { path: "#/", page: MainPage },
      { path: "#/profile", page: ProfilePage },
      { path: "#/login", page: LoginPage },
    ];
  }

  addRoute(path, handler) {
    this.routes[path] = handler;
  }

  navigateTo(path) {
    if (path.startsWith("#")) {
      location.hash = path; 
    } else {
      history.pushState(null, null, path);
      this.handleRoute(path)  
    }

  }

  handlePopState() {
    this.handleRoute(window.location.pathname);
  }

  handleHashChange() {
    this.handleRoute(location.hash);
  }

  handleRoute(path) {
    const route = this.routes.find((route) => route.path === path);
    const $root = document.querySelector("#root");

    if (path === "/profile" || path === "#/profile" && !localStorage.getItem("user")) {
      this.navigateTo("/login");
      return;
    } else if (path === "/login" ||path === "#/login" && localStorage.getItem("user")) {
      this.navigateTo("/");
      return;
    } else if (path === "/logout") {
      this.handleLogout();
      return;
    } else if (route && route.page) {
      new route.page($root);
    } else {
      new ErrorPage($root);
    }
  }

  handleLogout() {
    localStorage.removeItem("user");
    this.setRoute();
    this.navigateTo("/login");
  }

  getRoutes() {
    return this.routes;
  }
}

export default Router;
```
