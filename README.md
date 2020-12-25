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



### 프로젝트 생성

```shell
npm init -y
```

모든 초기조건을 자동세팅한 프로젝트 생성



### 라이브러리 추가

##### @types/node, typescript

```shell
yarn add -D @types/node typescript
```

-  <u>타입스크립트 노드</u> 와 <u>타입스크립트</u>를 추가한다.  (-D 키워드는 devDependency 에 모듈을 추가한다. )
  - @types/node 는 node.js에 타입을 추가해주는 패키지다.

##### ts-node

```shell
yarn add -D ts-node
```

##### tsconfing.json

```shell
npx tsconfing.json
```

- tsconfing.json :  미리 설정된 tsconfig 파일을 생성해주는 패키지로, 강의를 하는 ben awad 가 만든 파일이다.
- 위의 명령어를 실행하면 Pick the framework you're using 이라는 선택문구가 나오는데, 여기서 node 를 선택한다.
- 이렇게 하면 tsconfig.json 파일이 생성된다. (생성 후 수정할 수 있다.)



### package.json

타입스크립트를 실행하는 방식을 알아보고 적용해보자. 



##### ts-node

타입스크립트 파일은 바로 실행될 수가 없는데, ts-node는 메모리상에서 ts 파일을 읽어서 바로 실행해준다.

- script 의 start에 "ts-node src/index.ts" 를 추가하자. 

```javascript
"start": "ts-node src/index.ts"
```

- 이제 터미널에서 yarn start 를 입력하면, index.ts가 자바스크립트 파일로 변환되는 과정없이, 바로 해당 명령을 실행한다.
- 즉, index.ts에서 console.log("hello")라고 입력해뒀다면 그 명령어를 그대로 수행한다.

하지만, 속도가 느려서 튜토리얼에 사용할 건 아니다...

그럼? 그냥 보여줄려고 쓴거다. 실제로는 아래와 같이 컴파일과 실행을 2track 으로 진행한다.



##### tsc -w

```javascript
"watch" : "tsc -w"
```

- script 의 watch를 위와 같이 기술하고, 터미널에서 watch 를 수행하면 tsconfig.json 파일에서outDir에 설정해놓은대로,  dist폴더에 저장된다. 
- 그다음, 기존의 start는 start2로 바꾸고 새롭게 start를 추가한다. 

```javascript
 "start": "node dist/index.js",
 "start2": "ts-node src/index.ts"
```

- 그리고 새로운 터미널에서 start를 실행한다.

정리하면 이렇다. 

- 터미널1 : watch로 타입스크립트 파일 변경 왓치

- 터미널2 : dist/index.js 파일 실행

이렇게 2track으로 구성해두면, 파일이 변경될 때마다 컴파일을 미리 해두고, 실행만 하니까 더 빠르다. 

- ts-node : 1.68s
- node dist/index.js : 



##### nodemon

```shell
yarn add nodemon -D
```

```javascript
"dev": "nodemon dist/index.js",
"dev2": "nodemon --exec ts-node src/index.ts",
```

- nodemon 은 tsc -w 와 node dist/index.js 이 두개의 명령을 연결해주는 것이라고 볼 수 있다.
- 해당 파일의 변경을 감지하고 있다가 변화가 일어나면 파일을 다시 실행한다.
- --exec 은 해당 앱을 실행해주는 명령이다. 즉, src/index.ts에 변화가 생겼을 때, ts-node 를 exec 한다.



#### 결론

구성은 이렇게 된다. 

##### 터미널 1. 타입스크립트 재 컴파일

```shell
tsc -w 
```

- ts 파일을 js로 컴파일하는데, -w 옵션을 줘서 파일의 변화가 생길 때마다 리컴파일 하게 만든다. 
  (해당 옵션은 tsconfig.json의 설정을 따른다. )



##### 터미널 2. 변경된 코드 재 실행

```shell
nodemon dist/index.js
```

- 변경된 코드를 감지하고, 다시 실행한다. 



## 2. MicroORM Setup

#### 패키지 설치

- 터미널을 하나 열고 아래와 같이 패키지를 설치한다.

```shell
yarn add @mikro-orm/cli @mikro-orm/core @mikro-orm/migrations @mikro-orm/postgresql pg
```



22: 13 보는 중