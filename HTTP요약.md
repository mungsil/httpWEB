# HTTP
> HypeText Transfer Protocol
> 
> html, text, 이미지, json, xml 등의 binary형태 데이터를 HTTP를 이용하여 전송한다.
- 클라이언트 서버 구조
- 무상태 프로토콜(스테이스리스), 비연결성
- HTTP메시지
- 단순함, 확장 가능

# HTTP 메세지

- 메시지 구조는 다음과 같다.

  - start-line

  - header

  - empty line(CRLF)

  - message body
  
## 시작 라인

> ## 요청 메세지

### 예시) GET /search?q=hello&hl=ko HTTP/1.1

- start-line = request-line / status-line
- request-line= method SP(공백)request-target SP HTTP-version CRLF(엔터)

  - method(HTTP 메서드) : GET(=조회)
  
  - request-target(요청 대상) : /search?q=hello&hl=ko
   
  - HTTP version : HTTP/1.1


> ### HTTP 메서드 

- 종류: GET, POST, PUT, DELETE
- 서버가 수행해야 할 동작을 지정한다.
- GET은 리소스를 조회하고, POST는 요청 내역을 처리한다.


> ### request-target(요청 대상)

- absolute-path[?query] (절대경로[?쿼리])

  +) 절대경로= "/"로 시작하는 경로

  +) *, http://...?x=y와 같이 다른 유형의 경로지정 방법도 있다.

   


> ## 응답 메시지
- start-line = request-line / status-line
- status-line = HTTP-version SP status-code SP reason-phrase CRLF


  - HTTP 상태 코드 : 요청 성공, 실패를 나타냄


    - 200 : 성공 
    - 400 : 클라이언트 요청 오류
    - 500 : 서버 내부 오류 
  
  - reason-phrase: OK (사람이 이해할 수 있을 정도의 짧은 상태 코드 설명)


## HTTP 헤더

- header-field = field-name ":" OWS field-value OWS            *OWS:띄어쓰기 허용

- 요청 메시지에서의 header
    - Host: www.google.com
   
- 응답 메시지에서의 header
    - Content-Type: text/html;charset=UTF-8
    - Content-Length: 3423
- field-name은 대소문자 구분 없음

> ## 용도

- HTTP 전송에 필요한 모든 부가정보를 담는다.

-  예시) 메세지 바디가 html/ image/ json...등 어떤 내용인지, 메시지 바디의 크기, 압축, 인증, 요청 클라이언트 정보, 서버 애플리케이션 정보, 캐시 관리 정보 ...

-  필요 시 임의의 헤더를 추가할 수 있다.

## HTTP 바디
- 실제 전송할 데이터

- HTML 문서, 이미지, 영상, JSON 등등 byte로 표현할 수 있는 모든 데이터를 저송 가능하다.
