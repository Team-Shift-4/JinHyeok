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
- response 객체는 서버로 웹브라우저나 또는 앱으로 부터 어떤 요청이 있을 때 요청한 사용자 측으로 값을 반환해 줄 때 사용하는 객체<br>반대로 request 객체는 사용자가 요청한 내용이 담겨있는 객체

>response.writeHead(200, {'Content-Type':'text/html'});

- 첫번째 200 이라는 숫자값은 웹서버 들어오는 어떤 요청에 대해 정상적으로 값을 리턴할 때 사용하는 http 상태코드 오류가 없이 서버에서 처리가 정상적으로 <br>완료되면 200 코드를 담아서 응답헤더를 설정해 줌
를 담고 있는 것으로 브라우저 화면에는 나타나지 않는 값
- 브라우저는 header 값을 보고 서버에서 넘어온 값이 어떤 형태인지를 파악하고 실제 값을 header 에 세팅된 설정에 맞게 보여주게 됨

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

test1