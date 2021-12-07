# vue cli 알아보기

React의 cra처럼 vue에도 cli가 있습니다. vue-cli 가 기본적인 프로젝트를 세팅해주기 때문에 폴더 구조에 대한 고민, lint, build, 어떤 라이브러리로 구성을 해야하는지 webpack 설정은 어떻게 해야되는지에 대한 고민을 덜어줍니다.

## vue-cli 설치

```shell
npm install -g @vue/cli
yarn global add @vue/cli
```
설치 후 아래 명령어를 입력해서 정상 설치되었는지 확인하면 됩니다.
```
vue --version // 4.5.15
```

## VUE CLI로 프로젝트 생성해보기
```shell
vue create 여러분의프로젝트이름
```

일단 default 로 프로젝트를 생성해보겠습니다. 프로젝트 생성 후 해당 프로젝트 폴더로 이동해 dev 서버를 실행합니다.
```
cd hello-vue
npm run serve
```

