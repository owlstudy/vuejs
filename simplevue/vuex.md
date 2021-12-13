# Vuex

글로벌하게 state를 관리할 수 있도록 도와주는 상태관리 라이브러리입니다.

**왜 vuex가 필요한가요?**

1. 형제끼리의 state 교환이 불가능합니다.

일반적인 vue state의 흐름으로는 형제끼리의 데이터 교환이 불가능합니다.
그렇기 때문에 이런 상황에서는 두 컴포넌트를 감싸고 있는 부모 컴포넌트로 state를 올려서 사용하게 됩니다. 

2. props의 깊이가 깊어질 경우

props의 깊이가 깊어질수록 내려주는것이 복잡해집니다.

3. 액션에 따라 동시에 바뀌는 컴포넌트들

버튼을 클랙했을 때 여러 컴포넌트들에 동시에 영향을 주는 경우가 있다면 vuex의 도입을 고려해봄직 합니다.

## 실습

- state: 관리할 상태 값들
- getters: 밖으로 내보낼 값들(실제 컴포넌트에서 가져가 사용할 값들)
- mutations: 실제 state가 변화되는곳
- actions: mutations을 일으키는곳

```js
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export default new Vuex.store ({
  state: {
    counter: 0
  },
  getters: {
    counter: state => state.counter
  },
  mutations : {
    increment: state => state.counter +=1,
    decrement: staet => state.counter -= 1
  },
  actions : {
    addCounter : context => context.commit("increment"),
    subCounter: context => context.commit("decrement")
  }
})
```

```js
// main.js
import Vue from 'vue'
import App from './App.vue'
import store from './store'

Vue.config.productionTip = false;
new Vue ({
  store, 
  render: h => h(App)

}).$mount('#app')
```

vuex 의 action에 접근하기 위해서는 vuex에서 제공해주는 mapActions라는 함수를 이용해야합니다.

```vue
// components/Left.vue

<template>
  <div>
    <button @click="subCounter">-</button> // vuex 의 action 을 일으킵니다
    <button @click="addCounter">+</button>
  </div>
</template>

<script>
import { mapActions } from "vuex";

export default {
  methods: {
    ...mapActions(["addCounter", "subCounter"])
  }
};
</script>

<style>
</style>

```
getter에 접근하기 위해서는 vuex에서 제공해주는 mapGetters를 이용합니다.

```vue
// components/Right.vue 

<template>
  <div>value: {{ counter }}</div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  computed: {
    ...mapGetters(["counter"])
  }
};
</script>

<style>
</style>

```
