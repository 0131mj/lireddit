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

- npm init-y : 모든 초기조건을 자동세팅한 프로젝트 생성
- yarn add -D @types/node typescript :  <u>타입스크립트 노드</u> 와 <u>타입스크립트</u>를 추가한다.  (-D 키워드는 devDependency 에 모듈을 추가한다. )
  - @types/node 는 node.js에 타입을 추가해주는 패키지다.
- yarn add -D ts-node 



#### 환경설정

- script 의 start에 "ts-node src/index.ts" 를 추가해준다.

6:00 보는 중



명령어를 입력 후, node 를 고른다.

이렇게 하면 tsconfig.json 파일이 생성된다. 

```shell
npx tsconfing.json
```

