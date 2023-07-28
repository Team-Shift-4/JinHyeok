# node.js 설치 방법
1. 서버구축을 위해 바탕화면에 프로젝트 폴더 하나 생성 <br>
2. 폴더안에 server.js 파일을 생성하고 아래 내용을 입력

>var http = require('http'); <br>
>var server = http.createServer(function(request,response){ 
>
>   response.writeHead(200,{'Content-Type':'text/html'}); <br>
>   response.end('Hello node.js!!');
>
>});
>
>server.listen(8080, function(){ <br> 
>
>   console.log('Server is running...'); <br>
> 
>});

vscode 로 만든 폴더를 연후 node server를 입력하고 <br> 웹페이지에서 http://localhost:8080 입력하면
**Hello node.js** 가 출력됨.

# 소스코드 분석
> var http = require('http');

웹서버를 실행하기 위해 http 모듈을 requir로 불러옴.<br>  
- require는 다른언어의 import 와 유사한 기능<br>
- 하나의 독립적인 객체로 사용

> function nameOfFunction(parameters) { <br>
>   // 실행로직 <br>
>}

createServer( ) 에 파라미터로 입력되는 function(request,response){ } 은 함수명이 없음<br>
- 함수명이 없이 function 이라고만 작성된 파라미터는 이벤트 발생시에 callback 되고 생성된 서버로 어떤 요청이 들어오면 function 내부의 <br>로직이 실행되면서 function 내부에 선언한 request와 response라는 이름으로 사용할 수 있는 값을 넘겨주고 function 블럭 { } 내부에서는 <br>request 와 response로 넘어오는 어떤 값을 사용할 수 있게 됨
  
>var server = http.createServer( function(request,>response) { 
>
>   response.writeHead(200,{'Content-Type':'text/html'}); <br>
>    response.end('Hello node.js!!');
>
>});

- function 내부 로직을 살펴보면 response로 넘어온 값으로 함수를 실행 함. <br>
즉 callback 되었을 때 response 에 담겨저 오는 값은 require로 가져온 http 모듈처럼 내부적으로 함수를 가지고 있는 객체라는 의미.<br>
- response 객체는 서버로 웹브라우저나 또는 앱으로 부터 어떤 요청이 있을 때 요청한 사용자 측으로 값을 반환해 줄 때 사용하는 객체<br>
- 반대로 request 객체는 사용자가 요청한 내용이 담겨있는 객체

>response.writeHead(200, {'Content-Type':'text/html'});

- 첫번째 200 이라는 숫자값은 웹서버 들어오는 어떤 요청에 대해 정상적으로 값을 리턴할 때 사용하는 http 상태코드 오류가 없이 서버에서 처리가 정상적으로 완료되면 200 코드를 담아서 응답헤더를 설정해 줌<br>
- 브라우저는 header 값을 보고 서버에서 넘어온 값이 어떤 형태인지를 파악하고 실제 값을 header 에 세팅된 설정에 맞게 보여주게 됨
- 두번째 {'Content-Type' : 'text/html'} 값은 서버측에서 보내주는 컨텐츠의 타입이 텍스트이고, html 형태라는 것을 정의
- 두번째 값은 Content-Type 이라는 키값 이외에도 Authorization, Cookie 등의 다양한 값들을 지정할 수 있음

>response.end('Hello node.js!!');

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
>var http = require('http');
>
>// 1. 요청한 url을 객체로 만들기 위해 url 모듈사용<br>
>var url = require('url');<br>
>// 2. 요청한 url 중에 Query String 을 객체로 만들기 위해 querystring 모듈 사용<br>
>var querystring = require('querystring'); 
>
>var server = http.createServer(function(request,response){<br>
>   // 3. 콘솔화면에 로그 시작 부분을 출력<br>
>   console.log('--- log start ---');<br>
>   // 4. 브라우저에서 요청한 주소를 parsing 하여 객체화 후 출력<br>
>   var parsedUrl = url.parse(request.url);<br>
>   console.log(parsedUrl);<br>
>   // 5. 객체화된 url 중에 Query String 부분만 따로 객체화 후 출력<br>
>   var parsedQuery = querystring.parse(parsedUrl.query,'&','=');<br>
>   console.log(parsedQuery);<br>
>   // 6. 콘솔화면에 로그 종료 부분을 출력<br>
>   console.log('--- log end ---');<br>
>
>   response.writeHead(200, {'Content-Type':'text/html'});<br>
>   response.end('Hello node.js!!');<br>
>});
>
>server.listen(8080, function(){<br>
>   console.log('Server is running...');<br>
>});

- 입력 후 터미널에서 node server_request_get 을 입력하면 실행됨
- 브라우저에서 http://localhost:8080/?var1=newData&var2=153&var3=testdata2017  주소를 입력하면 hello node.js!!라는 메세지가 출력됨
  
# cmd 창에 뜨는 로그분석
 (정확하진 않습니다..수정해서 다시 올릴게요)
>--- log start ---<br>
>// 1. 이부분이 var parsedUrl = url.parse(주소) 함수로 주소값을 객체화 한 부분입니다.<br>
>//객체화 되기 때문에 parsedUrl.search 형태로 객체 내부의 변수값을 사용할 수 있습니다.<br>
>//아래에서는 객체 내부의 query 라는 변수값을 가져와서 다시 객체화 합니다.<br>
>Url {<br>
> protocol: null,<br>
> slashes: null,<br>
> auth: null,<br>
> host: null,<br>
> port: null,<br>
> hostname: null,<br>
> hash: null,<br>
> search: '?var1=newData&var2=153&var3=testdata2017',<br>
> query: 'var1=newData&var2=153&var3=testdata2017',<br>
> pathname: '/',<br>
> path: '/?var1=newData&var2=153&var3=testdata2017',<br>
> href: '/?var1=newData&var2=153&var3=testdata2017' }<br>
>
>// 2. 이 부분이 var parsedQuery = querystring.parse(parsedUrl.query,'&','=')<br>
>//parsedUrl 객체에서 query 라는 변수값을 다시 querystring 으로 parsing 하여 객체화하였습니다.<br>
>//해당 객체는 parsedQuery.var1 형태로 객체내부의 값을 사용할 수 있게 됨. <br>
>{ var1: 'newData', var2: '153', var3: 'testdata2017' }<br>
>--- log end ---

- url과 querystring 모듈에 있는 parse( ) 함수로 클라이언트가 요청한 주소값을 javascript 객체로 만들어서 사용할 수 있음

# 소스코드 분석

>var url = require('url');
- node.js 에는 console 과 같은 내장객체와 더불어 미리 정의되어 있는 내장 module 이 있음
- 그중 url 은 클라이언트가 요청한 주소값을 javascript 객체로 변환해서 사용할 수 있게 하는 모듈

>var querystring = require('querystring');
- querystring은 주소로 전달된 Query String 을 변환해서 javascript 객체로 사용할 수 있게 해주는 모듈

>console.log('--- log start ---');
>
>...
>
>console.log('--- log end ---');
- 이 코드에서는 서버에서 처리되는 내용을 콘솔화면에 출력하는데 로그의 시작과 끝을 알기 위해서 아래와 같이 로그의 시작과 끝을 출력

>var parsedUrl = url.parse(request.url);<br>
>console.log(parsedUrl);
- url 모듈의 parse( ) 함수를 사용해서 request 객체에 있는 url 값을 parsedUrl 변수에 담은후에 로그로 출력
- request 객체 내부에 url 이라는 변수가 존재하고 이 url 변수는 주소를 문자열 값으로 가지고 있음
- parsedUrl 객체에 담겨 있는 내용이 출력

>var parsedQuery = querystring.parse(parsedUrl.query,'&','=');<br>
>console.log(parsedQuery);
- parsedUrl 에는 객체화된 url 값이 들어가 있음
- 이중에 Query String 이 담겨있는 query 변수를 가져온 후 querystring 모듈의 parse( ) 함수를 이용해서 객체화함
- 역시 log( ) 함수를 이용해서 객체를 출력하면 Query String 으로 전달된 변수와 값이 로그분석 의 내용과 같이 출력

# 클라이언트 요청(POST) 처리
