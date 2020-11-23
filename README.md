# lireddit

Ben Award의 Fullstack React GraphQL TypeScript Tutorial 따라하기

https://www.youtube.com/watch?v=I6ypD7qv3Z8



## 1. Node/TypeScript Setup

#### 환경 세팅

##### 에디터

- VS-Code 

##### 플러그인

- Bracket Pair Colorizer
- Docker
- GraphQL for VSCode
- Vim 



#### 프로그램 요구사항

- nodejs : v14.5.0 이상
- npm : 6.14.5 이상
- yarn : 1.21.1 이상



#### 프로젝트 생성 및 라이브러리 추가

- npm init -y : 모든 초기조건을 자동세팅한 프로젝트 생성
- yarn add -D @types/node typescript :  <u>타입스크립트 노드</u> 와 <u>타입스크립트</u>를 추가한다.  (-D 키워드는 devDependency 에 모듈을 추가한다. )
  - @types/node 는 node.js에 타입을 추가해주는 패키지다.
- yarn add -D ts-node 

- tsconfing.json : ben awad 가 설정한 tsconfig 파일을 생성해주는 패키지이다. 

```shell
npx tsconfing.json
```

이렇게 하면 tsconfig.json 파일이 생성된다. (생성 후 수정할 수 있다.)



#### package.json

- script 의 start에 "ts-node src/index.ts" 를 추가해준다.

```javascript
"start": "ts-node src/index.ts"
```

이 상태에서 yarn start 를 수행하면, 해당코드를 어떤 변환없이 바로 수행해버린다.

index.ts에서 console.log("hello")라고 했다면 그 명령어를 그대로 수행한다.



- script 의 watch를 아래와 같이 기술하고

```javascript
"watch" : "tsc -w"
```

watch 를 수행하면 tsconfig.json 의 outDir에 설정해놓은 것과 같이 dist폴더에 저장된다. 

그리고 핫리로드도 지원하므로, 

