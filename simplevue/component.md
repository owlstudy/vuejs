# Component

component란 view를 구성하는 작은 조각들입니다.

## .vue 파일 구성 알아보기

vue 파일들은 .vue라는 확장자를 가지고 아래와 같은 기본적인 구성으로 이루어집니다.
```html
<template> // html 
</template>

<script>   // script
export default {};
</script>

<style>    // style
</style>
```

각 파일들은 자신만의 html, style, script를 가지기 때문에 component별로 독립된 환경을 가지고 개발을 할 수 있습니다.


### Style 변경과 scope

vue에서는 scope라는 옵션으로 component style scope를 적용할 수 있습니다.

```html
<style scoped>
h1 {
  color: #03a9f4;
}
</style>
```

### Component 다루기

컴포넌트 파일의 이름은 대문자로 시작합니다.

App.vue에서 모든 조각을 조립할 수 있습니다. 즉 다른 컴포넌트들의 부모 컴포넌트가 됩니다.

```js
<script>
import Header from "./components/Header";
import Menu from "./components/Menu";
import Content from "@/components/Content";

export default {
  name: "app",
  components: { // 가져온 component 들을 등록합니다.
    Header,
    Menu,
    Content
  }
};
</script>
```
자세히 보면 "@/components/Content" 와 같은 식으로 경로를 설정해 놓은 것을 볼 수 있습니다. @는 절대경로를 가리킵니다.

component를 사용하기 위해서는 script안쪽의 components에 등록을 해줘야 vue component로 인식 할 수 있습니다. 
component를 잘 쪼갤 수록 복잡한 tag, style관리 또한 없어집니다.