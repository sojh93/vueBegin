# 시작하기
[vue 시작하기](https://v3.ko.vuejs.org/guide/migration/introduction.html)

1. CDN
2. Codepen
3. CodeSandbox
4. Vite(npm init vite-app hello-vue3)
5. Vue CLI(npm install -g @vue/cli)

# 개요

## 주목할만한 새로운 기능들
1. [Composition API](https://v3.ko.vuejs.org/ko-kr/guide/composition-api-introduction.html)
2. [Teleport](https://v3.ko.vuejs.org/ko-KR/guide/teleport.html)
3. [Fragments](https://v3.ko.vuejs.org/ko-KR/guide/migration/fragments.html)
4. Emits 컴포넌트 옵션
5. 커스텀 렌더들을 생성하기 위한 @vue/runtime-core의 createRenderer API
6. <script setup> - SFC Composition API의 더 쉬운 표현
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
->
### 렌더 함수
### 커스텀 요소들
### 기타 소소한 변경사항들
### 제거된 APIs

## 지원 라이브러리들

### Vue CLI
### Vue Router
### Vuex
### 확장 Devtools
### IDE 지원
### 다른 프로젝트들

# 상세

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
