# nest.js

nest.js란 node.js 로 데이터베이스를 구성할 수있게 해주는 프레임워크
<br>
typescript 와 express를 이용한다. (프레임워크의 프레임워크)

nest.js의 필요성
<br>
큰 규모의 프로젝트의 데이터베이스르 만들기 쉽다.

# Node 설치
https://nodejs.org/ko/
위의 사이트에서 nodejs 설치하면 npm까지 같이 설치 완료


NestJS cli 설치 (맥북에서 설치하는 경우 명령어  앞에 sudo권한 줘야함)
<br>
$ npm i -g @nestjs/cli
<br>
nestJS cli(command-line-interface) 설치하는 cmd

$ nest new [project-name]
<br>
npm, yarn, pnpm 중에 뭘로 설치하고 싶냐고 묻는다.
보통 npm으로 설치하는거 같음.

<br>

# 파일 구조 파악하기

eslintrc.js : 파일 속 문법 에러가 나면 알려준다.
<br>
prettierrc : 코드 포매터. 작은 따옴표, 큰 따옴표, indent 크기 등의 규칙을 정한다.
<br>
package.json : scripts 안의 명령어들을 잘 사용할 것
<Br>
src 폴더 : 여기에 비즈니스 로직들이 들어있다.
<br>
main.ts : 앱 실행하는 시작점

<br>

# 앱 실행하기
$ npm run start(맥북에서 실행하는 경우 명령어 앞에 sudo권한 줘야함)
<br>
서버 띄운 후 http://127.0.0.1:3000 또는 http://localhost:3000 웹페이지로 들어가면 Hello Wolrd!가 출력됨.

<br>

# 실행과정
클라이언트: http://127.0.0.1:3000 GET으로 호출
<br>
서버 : main.ts -> app.module.ts -> app.controller.ts -> app.service.ts
순서로 작동
