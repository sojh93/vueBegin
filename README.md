# 1. 시작하기
[vue 시작하기](https://v3.ko.vuejs.org/guide/migration/introduction.html)
[vue란 무엇인가요?](https://v3.ko.vuejs.org/guide/introduction.html#vue-js%E1%84%80%E1%85%A1-%E1%84%86%E1%85%AE%E1%84%8B%E1%85%A5%E1%86%BA%E1%84%8B%E1%85%B5%E1%86%AB%E1%84%80%E1%85%A1%E1%84%8B%E1%85%AD)
-> 프로그레시브 프레임워크. 핵심 라이브러리는 뷰 레이어에만 초점을 맞추어 다른 라이브러리나 기존 프로젝트와의 통합 쉬움.

## 선언적 렌더링
-> 간단한 템플릿 구문을 사용해서 DOM에서 데이터를 선언적으로 렌더링 할 수 있다.
```
<div id="counter">
  Counter: {{ counter }}
</div>
----------------------------------
const Counter = {
  data() {
    return {
      counter: 0
    }
  }
}

Vue.createApp(Counter).mount('#counter')

----------------------------------

```
## 텍스트 보간 외 엘리먼트 속성 부여 가능.
```
<div id="bind-attribute">
  <span v-bind:title="message">
    여기에 마우스를 올려두고 잠시 기다리면 제목이 동적으로 바뀝니다!
  </span>
</div>

const AttributeBinding = {
  data() {
    return {
      message: '이 페이지를 다음 시간에 열었습니다. ' + new Date().toLocaleString()
    }
  }
}

Vue.createApp(AttributeBinding).mount('#bind-attribute')

```
## 사용자 입력 핸들링
```
<div id="event-handling">
  <p>{{message}}</p>
  <button v-on:click="reverseMessage">Reverse Message</button>
</div>

const EventHandling = {
  data() {
    return {
      message: 'Hello Vue.js!'
      }
    },
    methods: {
      reverseMessage() {
        this.message = this.message
          .split('')
          .reverse()
          .join('')
      }
    }
  }
  Vue.createApp(EventHandling).mount('#event-handling')
  ```
  
## 양식 입력과 앱 상태를 양방향으로 바인딩하는 ```v-model```디렉티브
  
  ``` <div id="two-way-binding">
    <p>{{message}}</p>
    <input v-model="message"/>
  </div>
  
  const TwoWayBinding = {
    data() {
      return {
        message: 'Hello Vue!'
        }
      }
    }
    Vue.createApp(TwoWayBinding).mount('#two-way-binding')
  ```
## 조건문과 반복문
  ```
  <div id="conditional-rendering">
    <span v-if="seen">이제 나를 볼 수 있어용</span>
  </div>
  
  const ConditionalRendering = {
    data() {
      return {
        seen: true
      }
    }
  }
  Vue.createApp(ConditionalRendering).mount('#conditional-rendering')
  ```
  
## ```v-for``` 디렉티브
  -> 배열에서 데이터를 가져와 아이템 목록을 표시하는 데 사용.
  
  ```
  <div id="list-rendering">
    <ol>
      <li v-for="todo in todos">
        {{todo.text}}
      </li>
    </ol>
  </div>
  
  const ListRendering = {
    data() {
      return {
       todos: [
        { text: 'Learn JavaScript'},
        { text: 'Learn Vue'},
        { text: 'Build something awesome'}
      ]
    }
  }
}

Vue.createApp(ListRendering).mount('#list-rendering')
```
## 컴포넌트로 조립하기
```
// 뷰 어플리케이션 생성
const app = Vue.createApp(...)

// todo-item 이란 이름의 새로운 컴포넌트 선언
app.component('todo-item', {
  template: `<li>할일이 있어요</li>`
})

// 애플리케이션을 마운트.
app.mount(...)

<ol>
  <!-- todo-item 컴포넌트의 인스턴스를 만든다. -->
  <todo-item></todo-item>
</ol>

app.component('todo-item', {
  props: ['todo],
  template: `<li>{{todo.text}}</li>`
})
```
```v-bind```를 사용하여 할일을 개별 todo-item 컴포넌트에 전달.

```
<div id="todo-list-app">
  <ol>
    <!--
      이제 할일 todo-item 에 할일을 전달한다.
      콘텐츠는 동적으로 표현된다. -->
    <todo-item
      v-for="item in groceryList"
      v-bind:todo="item"
      v-bind:key="item.id"
      ></todo-item>
    </ol>
  </div>
  
  const TodoList = {
    data() {
      return {
        groceryList: [
          {id: 0, text: '야채' },
          {id: 1, text: '치즈' },
          {id: 2, text: '사람이 먹을 수 있는 거라면 뭐든지'}
        ]
      }
    }
  }
  
  const app = Vue.createApp(TodoList)
  
  app.component('todo-item', {
    props: ['todo'],
    template: `<li>{{todo.text}}</li>`
  })
  
  app.mount('#todo-list-app')
  ```
  
  컴포넌트는 다음과 같이 조합할 수 있다.
  
  ```
  <div id="app">
    <app-nav></app-nav>
    <app-view>
      <app-sidebar></app-sidebar>
      <app-content></app-content>
    </app-view>
  </div>
  ```
## 조건문과 반복문
  ```
  <div id="conditional-rendering">
    <span v-if="seen">이제 나를 볼 수 있어요</span>
  </div>
  
  const ConditionalRendering = {
    data() {
      return {
        seen: true
        }
      }
    }
    Vue.createApp(ConditionalRendering).mount('#conditional-rendering')
  ```
  텍스트, 속성뿐만 아니라 DOM의 구조에도 데이터를 바인딩 할 수 있다. mount, update, unmount 때 자동으로 전환효과를 적용해준다.(vue 자체적으로)
  
  ```
  const ConditionalRenderingApp = {
    data() {
      return {
        seen: true
      }
    }
  }
  Vue.createApp(ConditionalRenderingApp).rendering')
  
  <div id="list-rendering">
    <ol>
      <li v-for="todo in todos">
        {{ todo.text}}
      </li>
    </ol>
  </div>
  
  const ListRendering = {
    data() {
      return {
        todos: [
          { text: 'Learn JavaScript'},
          { text: 'Learn Vue'},
          { text: 'Build something awesome'}
        ]
      }
    }
  }
  
  Vue.createApp(ListRendering).mount('#list-rendering')
  ```
# 2. 애플리케이션 & 컴포넌트 인스턴스
  
## 애플리케이션 인스턴스 생성하기
  -> 모든 Vue 애플리케이션은 ```createApp``` 함수를 사용하여 새로운 **애플리케이션 인스턴스**를 생성하여 시작한다.
  
  ```
  const app = Vue.createApp({/* options */})
  app.component('SearchInput', SearchInputComponent)
  app.directive('focus', FocusDirective)
  app.use(LocalePlugin)
  ```
  
 *애플리케이션 인스턴스로 노출된 대부분의 메소드들은 동일한 인스턴스를 반환하여 연결(chaining)을 허용한다.('.'으로 연결한다는 뜻인 듯)*
  ```
  Vue.createApp({})
    .component('SearchInput', SearchInputComponent)
    .directive('focus', FocusDirective)
    .use(LocalePlugin)
  ```
  
## 최상위(Root) 컴포넌트
  
  'createApp'에 전달된 옵션은 **루트 컴포넌트**를 구성하는데 사용된다.<br/>
  이 컴포넌트는 애플리케이션을 mount할 때, 렌더링의 시작점으로 사용된다.<br/>
  애플리케이션을 DOM요소에 마운트한다.<br/>
  ex) Vue 애플리케이션을 **<div id="app"></div>**에 마운트하려면 #app을 전달해야 한다.</br></br>
 
 mount는 애플리케이션이 아닌 루트 컴포넌트 인스턴스를 반환한다.</br>
 
 ```
 const RootComponent = { /* options */ }
 const app = Vue.createApp(RootComponent)
 const vm = app.mount('#app')
 ```
 *vm은 (ViewModel의 줄임말로 사용된다. Vue가 MVVM패턴과 밀접하게 관련있어서 이렇게 쓰는 듯)*</br>
 
## 라이프 사이클 훅
-> 각 컴포넌트는 생성될 때 일련의 초기화 단계를 거친다.</br>
ex) 데이터 관찰, 템플릿 컴파일, 인스턴스를 DOM에 마운트, 데이터 변경 시 DOM을 업데이트 해야한다.</br>
이 과정에서 라이프사이클 훅 함수도 실행하여 사용자가 특정 단계에서 자신의 코드를 추가할 수 있는 기회를 제공한다.</br>

```
Vue.createApp({
  data() {
    return { count: 1}
  },
  created() {
    // `this` points to the vm instance
    console.log('count is: ' + this.count) // => "count is: 1"
  }
})
```
인스턴스 라이프사이클에는 mounted, updated, unmounted 훅도 있음. 모든 라이프사이클 훅에는 Vue 인스턴스를 가리키는 this 컨텍스트와 함께 호출된다.

### TIP
! options 속성이나 콜백에서 ~~created: () => console.log(this.a) 또는 (vm.$watch('a', newValue => this.myMethod())~~ 과 같은 화살표 함수를 사용하지 말 것.</br>
  화살표 함수는 this가 없기 때문에, this는 다른 변수로 취급되거나 호출한 변수를 발견할 때까지 부모 스코프에서 해당 변수를 찾을 것임.</br>
  이 때문에 ```Uncaught TypeError: Cannot read property of undefined``` 또는 ```Uncaught TypeError: this.myMethod is not a function```와 같은 오류가 발생한다.
  
  
  
  
  
  
  
  
 
  

1. CDN
2. Codepen
3. CodeSandbox
4. Vite(npm init vite-app hello-vue3)
5. Vue CLI(npm install -g @vue/cli)

# 2. 개요

## 주목할만한 새로운 기능들
1. [Composition API](https://v3.ko.vuejs.org/ko-kr/guide/composition-api-introduction.html)
2. [Teleport](https://v3.ko.vuejs.org/ko-KR/guide/teleport.html)
3. [Fragments](https://v3.ko.vuejs.org/ko-KR/guide/migration/fragments.html)
4. [Emits 컴포넌트 옵션](https://v3.ko.vuejs.org/ko-KR/guide/component-custom-events.html)
5. [커스텀 렌더들을 생성하기 위한 @vue/runtime-core의 createRenderer API](https://github.com/vuejs/core/tree/main/packages/runtime-core)
6. <script setup> - SFC Composition API의 더 쉬운 표현(404error)
7. <style vars> - SFC State-driven CSS 변수
8. <style scoped> - 전역 규칙으로 사용하거나 특정 slot의 규칙으로 사용가능.

## 주의해야 할 변경사항들

### 전역 API
-> 전역 Vue API가 애플리케이션 인스턴스를 사용하도록 변경됨.<br/>
-> 글로벌 및 내부 API가 트리쉐이킹(죽은 코드 제거)이 가능하도록 재구성됨.

### 템플릿 디렉티브
    1. v-model의 컴포넌트 사용법 재정의.
    2. 노드들의 key 사용방법이 변경됨.
    3. 같은 요소에 v-if와 v-for가 사용될 때 우선순위가 변경됨.
    4. v-bind = "object"는 순서에 민감하게 됨.
    5. v-for 내부의 ref는 더이상 refs 참조 배열을 자동생성하지 않음.
  
### 컴포넌트들
    1. 함수형 컴포넌트는 오직 일반 함수를 사용해서만 만들 수 있다.
    2. 싱글파일 컴포넌트(SFC)의 <template>과 함수형 컴포넌트 옵션의 functional 속성은 더이상 사용 x.
    3. 비동기 컴포넌트 생성을 위해 defineAsyncComponent 메서드 필요.
  
### 렌더 함수
    1. 렌더함수 API 변경됨.
    2. $scopedSlots 속성이 제거되고 모든 슬롯이 $slots를 통해 함수로 노출됨.
  
### 커스텀 요소들
    1. 커스텀 요소 허용이 Template 컴파일 시 수행된다.
    2. 사용자 지정 속성 is의 사용은 예약어인 <component>태그로 제한된다.
    
### 기타 소소한 변경사항들
    1. destroyed 라이프사이클 옵션 명칭이 unmounted로 변경된다.
    2. beforeDestroy 생명주기 옵션의 명칭이 beforeUnmount로 변경된다.
    3. Props default 팩토리 함수는 더이상 this에 접근할 수 없다.
    4. 컴포넌트 라이프사이클에 맞게 사용자 지정 디렉티브 API가 변경됨.
    5. data 옵션은 항상 함수로 선언되어야 함.
    6. mixins의 data 옵션은 얕게 병합된다.
    7. 속성 강제 방법이 변경됨.
    8. 몇몇 Transition 클래스의 명칭 변경됨.
    9. 배열에서 watch 콜백은 배열이 교체될 때만 발생. 배열의 변경사항에 대해 watch 콜백 실행하려면, 반드시 deep 옵션을 설정해줘야 한다.
    10. 특수 디렉티브(v-if / else-if / else, v-for 또는 v-slot)이 없는 <template>태그는 <br>
        일반 요소로 처리되며 내부 콘텐츠를 렌더링하는 대신 native <template> 요소가 된다.
    11. Vue 2.x에서 애플리케이션 루트 컨테이너의 outerHTML은 루트 컴포넌트 템플릿으로 대체된다.<br>
        Vue 3.x에서는 애플리케이션 컨테이너의 innerHTML을 대신 사용한다.
    
### 제거된 APIs
    1. v-on 수정자로서의 키코드 지원.
    2. $on, $off 그리고 $once 인스턴스 메소드.
    3. 필터
    4. 인라인 템플릿 속성
    5. $destroy 인스턴스 메소드. 더 이상 개별 Vue 구성 요소의 수명주기를 수동으로 관리할 필요가 없다.


## 지원 라이브러리들
-> 모든 공식 도구들과 라이브러리는 Vue 3을 지원하나 대부분 베타 상태. npm에서 ```next``` dist 태그로 배포된다. 2020년 말까지 ```latest``` dist 태그를 사용하도록 모든 프로젝트를 안정화하고 전환할 예정.<br>
    
### Vue CLI
-> v4.5.0 부터 ```vue-cli``` 는 새 프로젝트를 만들 때 Vue 3을 사전 설정하는 기본 옵션을 제공한다.<br>
   ```vue-cli```를 업그레이드 하고 ```vue create```를 실행하여 Vue 3 프로젝트를 만들 수 있다.
    
### Vue Router
-> Vue Router 4.0은 Vue 3을 지원.
    
### Vuex
-> Vuex 4.0은 3.x 와 거의 동일한 API로 Vue 3을 지원한다. 플러그인 설치방법 유의!
    
### 확장 Devtools
-> 새로운 UI와 리팩토리된 Dev Tools 개발 중. 아직 베타버전.
    
### IDE 지원
-> Vetur 사용 추천.
    
### 다른 프로젝트들
-> 
Project | npm | Repo
--|--|--
@vue/babel-plugin-jsx | npm v1.1.1 | [[GitHub]]
eslint-plugin-vue | []![beta] | [[GitHub]]
@vue/test-utils	| []![beta]	| [[GitHub]]
vue-class-component	| []![beta]	| [[GitHub]]
vue-loader | []![beta] | [[GitHub]]
rollup-plugin-vue | []![beta] | [[GitHub]]

# 3. 상세

## v-for Array Refs
## 비동기 컴포넌트
## 속성 강제 규칙(Attribute Coercion Behavior)
## class와 style이 포함된 $attrs
## $children
## 커스텀 디렉티브
## 커스텀 엘리먼트 Interop(Custom Elements Interop)
## Data Option
## emits 옵션
## 이벤트 API
## Filters
## Fragments
## 함수형 컴포넌트
## 글로벌 API
## 전역 API 트리쉐이킹
## 인라인 템플릿 속성
## key 속성
## 키 코드 수식어(KeyCode Modifiers)
## $listeners 제거됨
## Mount API changes
## propsData
## Props Default 함수의 this 접근
## 렌더함수 API
## 슬롯 통합
## Suspense
## Transition 클래스 변경
## 트랜지션 그룹 루트 엘리먼트
## v-on.native 수정자가 제거되었습니다.
## v-model
## v-if와 v-for의 우선순위
## v-bind 병합동작
## VNode Lifecycle Events
## 배열 Watch
