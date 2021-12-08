# State와 Props
상태 관리에 대해서 알아보겠습니다.

기존의 jquery와 다르게 vue는 document에서 직접적인 접근을 하여 DOM을 제어하지 않습니다. 그대신 state라는 상태를 이용하여 DOM을 관리합니다.

## State

Box.vue라는 Box component 가 있다고 예를 들어봅시다. 박스는 40이라는 높이를 가지고 있고, 80이라는 높이를 가지고 있습니다. 이 값들은 어떠한 행동에 따라 변경 될 여지가 있는 값이라고 할 때, 우리는 어딘가 이 값들을 가지고 있어야하고 이 값을 바탕으로 Box를 그려줘야 합니다. **정리를 해보면 넓이 40, 높이 80의 어떤 데이터를 Box.vue는 가지고 있어야 된다는 것 입니다.**

component의 state는 data 라는 함수를 이용하여 구성할 수 있습니다.
```js
// Box.vue 

<script>
export default {
  data() {  // Box 의 state
    return {
      width: 40, // 넓이
      height: 80 // 높이
    };
  }
};
</script>
```
data 안의 모든 값은 Proxy로 변경에 대한 처리가 observable하게 이루어 집니다. 또한 vue에 관련한 무엇인가를 적용하기 위해서는 v-bind 라는 것을 이용합니다. html태그에 인라인으로 스타일을 적용할 때는 :style 이라고 적용해도됩니다. 

리액트에서와 마찬가지로 뷰에도 props를 받는게 있습니다. 뷰에서는 props의 type을 적어줌으로써 props에 대한 안점함을 보장합니다.
해당 props가 내려오지 않았을 경우를 방지하기 위해 default값 또한 줄 수 있습니다.

```js
// Box.vue 

<script>
export default {
  props: {
    color: { type: String, default: "" }
  },
  data() {
    return {
      width: 40,
      height: 80
    };
  }
};
</script>
```

state와 props를 적용하기위해서는 아래와 같이 할 수 있습니다.
```js
<div v-bind:class="[state, props]"></div>
<div :class="[state, props]"></div>

<template>
  <div 
    v-bind:class="['box', color]" 
    v-bind:style="{ width: width + 'px', height: height + 'px' }">
  </div>
</template>
```
