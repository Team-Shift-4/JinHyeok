# node.js 란
- Node.js는 Chrome V8 JavaScript 엔진으로 빌드 된 JavaScript 런타임<br>
(노드를 통해 다양한 자바스크립트 애플리케이션을 실행할 수 있으며, 서버를 실행하는 데 제일 많이 사용)
- Node.js는 JavaScript를 서버에서도 사용할 수 있도록 만든 프로그램
- Node.js는 V8이라는 JavaScript 엔진 위에서 동작하는 자바스크립트 런타임(환경)
- Node.js는 서버사이트 스크립트 언어가 아님 프로그램(환경)
- Node.js는 웹서버와 같이 확장성 있는 네트워크 프로그램을 제작하기 위해 제작됨
- Node.js는 확장성이 있는 네트워크 어플리케이션 개발에 사용되는 소프트웨어 플랫폼이다. 특히 서버사이트에서 많이 사용되고 있음
- 사용되는 언어로는 자바스크립트(Javascript)를 활용하며, Non-blocking I/O와 단일 스레드 이벤트 루프를 통한 높은 처리 성능을 가지고 있는 것이 특징
- 내장 HTTP 서버 라이브러리를 포함하고 있어 웹 서버에서 아파치 등의 별도 소프트웨어 없이 동작하는 것이 가능<br>
(이를 통한 웹 서버의 동작에 있어 더 많은 통제에서 벗어나 여러 가지 기능을 가능하게 함)

즉, Node.js를 통해 웹어플리케이션이 더욱 발전하게 되었으며, 정적인 홈페이지 뿐만 아니라 쇼핑몰, 티켓 예매사이트, 블로그 등 데이터가 변해가는 사이트를 만들 수 있으며, 여러 개발자가 만든 프로그램과 게임을 웹상에서 구동시켜 안드로이드폰, 아이폰, 윈도우PC, 맥 등 플랫폼의 제약에서 벗어나 어디든 상관없이 실행 가능하게 해준다.<br>
(실시간 온라인 채팅, 실시간 온라인 게임 등 실시간 기능을 넣거나, 로그인 기능을 넣어 유저를 관리하고 점수를 관리하는 데이터베이스 기능을 Node.js를 통해 만들 수가 있다)

# Node.js의 FrameWork Express
- Express는 Node.js의 프레임워크(FrameWork)이다.<br>
(프레임워크는 어떠한 작업을 쉽게 완성하기 위한 라이브러리의 집합)
- Express는 Node.js를 이용하여 웹 애플리케이션을 만들기 위한 틀(Frame)을 제공하는 라이브러리의 집합

# node.js 사용이유
- Node.js를 사용하려면 먼저 JavaScript를 배워야한다.<br>
(JavaScript는 독립적인 언어가 아닌 스크립트 언어)
- Node.js를 이용하여 웹 브라우저와 무관한 프로그램을 만들 수 있음.
- Node.js를 이용하여 서버도 만들 수 있음.
- 이전까지 Server-Client 웹사이트를 만들 때 웹에서 표시되는 부분은 JavaScript 를 사용하여 만들어야만 했으며, 서버는 Reby, Java 등 다른 언어를 써서 만들었어야 했는데 마침내 한 가지 언어로 전체 웹 페이지를 만들 수 있음.

# node.js 사용시 장점
- 멀티 스레드 방식에 비해 적은 컴퓨터 자원을 사용
- I/O 작업이 많은 서버로 적합
- 웹 서버가 내장되어 있어 별도의 웹서버를 설치할 필요가 없음
- 자바스크립트를 사용하기 때문에 JSON 형식과 쉽게 호환

# node.js 사용시 장점
- 이벤트 기반 비동기방식이라 서버단 로직이 복잡한 경우 콜백함수의 늪에 빠질 수 있다.
- 단일 쓰레드(Single Thread)이기 때문에 하나의 작업 자체가 많이 걸리는 웹서비스에는 어울리지 않다. 
- 코드가 수행되어야 코드에 에러가 있는지 알 수 있으며, 에러가 날 경우 프로세스가 내려가기 때문에 테스트가 엄청 중요

# node.js 설치 방법
1. 서버구축을 위해 바탕화면에 프로젝트 폴더 하나 생성 <br>
2. 폴더안에 server.js 파일을 생성하고 아래 내용을 입력

```
var http = require('http'); 
var server = http.createServer(function(request,response){ 

   response.writeHead(200,{'Content-Type':'text/html'}); 
   response.end('Hello node.js!!');

});

server.listen(본인이 원하는 포트번호 입력), function(){ 

   console.log('Server is running...'); 
 
});
```

vscode 로 만든 폴더를 연후 node server를 입력하고 <br> 웹페이지에서 **http://localhost:(본인이 지정한 포트번호)** 입력하면
**Hello node.js** 가 출력됨.

# 소스코드 분석
```
 var http = require('http');
```

웹서버를 실행하기 위해 http 모듈을 requir로 불러옴.<br>  
- require는 다른언어의 import 와 유사한 기능
- 하나의 독립적인 객체로 사용
```
function nameOfFunction(parameters) {
   // 실행로직 
}
```

createServer( ) 에 파라미터로 입력되는 function(request,response){ } 은 함수명이 없음<br>
- 함수명이 없이 function 이라고만 작성된 파라미터는 이벤트 발생시에 callback 되고 생성된 서버로 어떤 요청이 들어오면 function 내부의 <br>로직이 실행되면서 function 내부에 선언한 request와 response라는 이름으로 사용할 수 있는 값을 넘겨주고 function 블럭 { } 내부에서는 <br>request 와 response로 넘어오는 어떤 값을 사용할 수 있게 됨
  
```
var server = http.createServer( function(request,>response) { 

   response.writeHead(200,{'Content-Type':'text/html'}); 
    response.end('Hello node.js!!');

});
```

- function 내부 로직을 살펴보면 response로 넘어온 값으로 함수를 실행 함. <br>
즉 callback 되었을 때 response 에 담겨저 오는 값은 require로 가져온 http 모듈처럼 내부적으로 함수를 가지고 있는 객체라는 의미.<br>
- response 객체는 서버로 웹브라우저나 또는 앱으로 부터 어떤 요청이 있을 때 요청한 사용자 측으로 값을 반환해 줄 때 사용하는 객체<br>
- 반대로 request 객체는 사용자가 요청한 내용이 담겨있는 객체
  
```
response.writeHead(200, {'Content-Type':'text/html'});
```

- 첫번째 200 이라는 숫자값은 웹서버 들어오는 어떤 요청에 대해 정상적으로 값을 리턴할 때 사용하는 http 상태코드 오류가 없이 서버에서 처리가 정상적으로 완료되면 200 코드를 담아서 응답헤더를 설정해 줌
- 브라우저는 header 값을 보고 서버에서 넘어온 값이 어떤 형태인지를 파악하고 실제 값을 header 에 세팅된 설정에 맞게 보여주게 됨
- 두번째 {'Content-Type' : 'text/html'} 값은 서버측에서 보내주는 컨텐츠의 타입이 텍스트이고, html 형태라는 것을 정의
- 두번째 값은 Content-Type 이라는 키값 이외에도 Authorization, Cookie 등의 다양한 값들을 지정할 수 있음

```
response.end('Hello node.js!!');
```

- 위 코드는 end( ) 라는 함수에 'Hello node.js!!'라는 실제 컨텐츠를 담아서 브라우저 측에 전달
- 실제 코드 값을 end( ) 함수로 전달하면 브라우저는 해당 컨텐츠를 받은 후 html 형태로 화면에 출력

# http 상태코드

**100** 
- 요청을 받았고, 작업을 진행 중이라는 의미

| 100 | Continue |
| :--: | :--: | 
| 101 | Switching Protocols | 

**200** 
- 요청이 정상적으로 처리 되었을 때 사용

| 200 | OK |
| :--: | :--: | 
| 201 | Created |
| 202 | Accepted |
| 203 | Non-Authoritative Information |
| 204 | No Content |
| 205 | Reset Content |
| 206 | Partial Content|

**300**
- 클라이언트가 Redirection 등의 추가적인 작업을 해야 한다는 의미
- 브라우저에서 요청했을 경우 응답을 받은 브라우저는 다른페이지로 Redirection 처리를 하고 작업을 완료
  
| 300 | Multiple Choices |
| :--: | :--: | 
| 301 | Moved Permanently |
| 302 | Found |
| 303 | See Other |
| 304 | Not Modified |
| 305 | Use Proxy |
| 306 | (Unused in version 1.1)|
| 307 | Temporary Redirect|

**400**
- 요청이 잘못되었을 때 사용 
- 예를 들어 주소체계가 틀렸거나, 존재하지 않는 페이지를 요청했을 때 사용
  
| 400 | Bad Request |
| :--: | :--: |
| 401 | Unauthorized |
| 402 | Payment Required |
| 403 | Forbidden |
| 404 | Not Found |
| 405 | Method Not Allowed |
| 406 | Not Acceptable |
| 407 | Proxy Authentication Required |
| 408 | Request Timeout |
| 409 | Conflict |
| 410 | Gone |
| 411 | Length Required |
| 412 | Precondition Failed |
| 413 | Request Entity Too Large |
| 414 | Request-URI Too Long |
| 415 | Unsupported Media Type |
| 416 | Requested Range Not Satisfiable |
| 417 | Expectation Failed |

**500**
- 요청은 정상적이지만 서버측 오류로 정상적인 처리가 되지 않았을때 사용
- 일반적인 서버오류에 많이 사용
  
| 500 | Internal Server Error |
| :--: | :--: |
| 501 | Not Implemented |
| 502 | Bad Gateway |
| 503 | Service Unavailable |
| 504 | Gateway Timeout |
| 505 | HTTP Version Not Supported |

# 클라이언트 요청(GET) 처리

  **주소값을 이용해 요청하는 방식**
> http://naver.com/Post.nhn?postId=3572432&cafeId=158763

- 위와 같이 브라우저를 통해 naver.com/Post.nhn 주소로 요청을 하게 되는데 서버측에서는 ?(물음표) 다음의 값들을 변수와 값의 형태로 받아서 사용하게 되는데, 이렇게 실제 주소값 뒤에 붙어가는 값을 Query String 이라고 함
- Query String 은 주소형태로 요청할 수도 있고, HTML에 있는 form 태그를 사용해서 요청할수도 있음

**아래 방법을 참고하여 실습 해보기**
- server_request_get.js 파일 만들기
- 아래 코드 입력하기

```
var http = require('http');

// 1. 요청한 url을 객체로 만들기 위해 url 모듈사용
var url = require('url');
// 2. 요청한 url 중에 Query String 을 객체로 만들기 위해 querystring 모듈 사용
var querystring = require('querystring'); 

var server = http.createServer(function(request,response){
   // 3. 콘솔화면에 로그 시작 부분을 출력
   console.log('--- log start ---');
   // 4. 브라우저에서 요청한 주소를 parsing 하여 객체화 후 출력
   var parsedUrl = url.parse(request.url);
   console.log(parsedUrl);
   // 5. 객체화된 url 중에 Query String 부분만 따로 객체화 후 출력
   var parsedQuery = querystring.parse(parsedUrl.query,'&','=');
   console.log(parsedQuery);
   // 6. 콘솔화면에 로그 종료 부분을 출력
   console.log('--- log end ---');

   response.writeHead(200, {'Content-Type':'text/html'});
   response.end('Hello node.js!!');
});

server.listen(본인이 원하는 포트번호, function(){
   console.log('Server is running...');
});
```

- 입력 후 터미널에서 node server_request_get 을 입력하면 실행됨
- 브라우저에서 **http://localhost:(본인이 지정한 포트번호)/?var1=newData&var2=153&var3=testdata2017**  주소를 입력하면 hello node.js!!라는 메세지가 출력됨
  
# cmd 창에 뜨는 로그분석
 (정확하진 않습니다..수정해서 다시 올릴게요)

 ```
--- log start ---
// 1. 이부분이 var parsedUrl = url.parse(주소) 함수로 주소값을 객체화 한 부분입니다.
//객체화 되기 때문에 parsedUrl.search 형태로 객체 내부의 변수값을 사용할 수 있습니다.
//아래에서는 객체 내부의 query 라는 변수값을 가져와서 다시 객체화 합니다.
Url {
   protocol: null,
   slashes: null,
   auth: null,
   host: null,
   port: null,
   hostname: null,
   hash: null,
   search: '?var1=newData&var2=153&var3=testdata2017',
   query: 'var1=newData&var2=153&var3=testdata2017',
   pathname: '/',
   path: '/?var1=newData&var2=153&var3=testdata2017',
   href: '/?var1=newData&var2=153&var3=testdata2017' }

// 2. 이 부분이 var parsedQuery = querystring.parse(parsedUrl.query,'&','=')
//parsedUrl 객체에서 query 라는 변수값을 다시 querystring 으로 parsing 하여 객체화하였습니다.
//해당 객체는 parsedQuery.var1 형태로 객체내부의 값을 사용할 수 있게 됨. 
{ var1: 'newData', var2: '153', var3: 'testdata2017' }
--- log end ---
```

- url과 querystring 모듈에 있는 parse( ) 함수로 클라이언트가 요청한 주소값을 javascript 객체로 만들어서 사용할 수 있음

# 소스코드 분석

```
var url = require('url');
```

- node.js 에는 console 과 같은 내장객체와 더불어 미리 정의되어 있는 내장 module 이 있음
- 그중 url 은 클라이언트가 요청한 주소값을 javascript 객체로 변환해서 사용할 수 있게 하는 모듈

```
var querystring = require('querystring');
```

- querystring은 주소로 전달된 Query String 을 변환해서 javascript 객체로 사용할 수 있게 해주는 모듈
  
```
console.log('--- log start ---');



console.log('--- log end ---');
```

- 이 코드에서는 서버에서 처리되는 내용을 콘솔화면에 출력하는데 로그의 시작과 끝을 알기 위해서 아래와 같이 로그의 시작과 끝을 출력
  
```
var parsedUrl = url.parse(request.url);
console.log(parsedUrl);
```

- url 모듈의 parse( ) 함수를 사용해서 request 객체에 있는 url 값을 parsedUrl 변수에 담은후에 로그로 출력
- request 객체 내부에 url 이라는 변수가 존재하고 이 url 변수는 주소를 문자열 값으로 가지고 있음
- parsedUrl 객체에 담겨 있는 내용이 출력

```
var parsedQuery = querystring.parse(parsedUrl.query,'&','=');
console.log(parsedQuery);
```

- parsedUrl 에는 객체화된 url 값이 들어가 있음
- 이중에 Query String 이 담겨있는 query 변수를 가져온 후 querystring 모듈의 parse( ) 함수를 이용해서 객체화함
- 역시 log( ) 함수를 이용해서 객체를 출력하면 Query String 으로 전달된 변수와 값이 로그분석 의 내용과 같이 출력

# 클라이언트 요청(POST) 처리
- POST는 주소만 요청하고 변수와 값을 주소가 아닌 요청 BODY에 담아서 서버측에 요청
- 