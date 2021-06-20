### v-model을 풀어서 구현하는 방식의 장점

- 우선 Vue 2 에선 한글입력에 대한 완전한 반응이 안된다. (IME 입력기는 제대로 지원을 안해준다)

- 이 프로젝트에 있는 TodoInput.vue 컴포넌트는 input을 props 와 emit 을 이용해서 동작한다.

- 만약 props의 값을 'value', emit 이벤트 이름을 'input'으로 했다면 컴포넌트의 v-model 속성으로 똑같이 사용할 수 있다. (꿀팁)