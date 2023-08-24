# HTTP
> HypeText Transfer Protocol
> 
> html, text, 이미지, json, xml 등의 binary형태 데이터를 HTTP를 이용하여 전송한다.

# 특징
 
 ### 클라이언트 서버 구조
  - 클라이언트가 서버에 request를 보내고 response를 받기위해 대기한다.
  - 서버는 request를 받고 이에 따라 response를 생성한 후 클라이언트에 응답한다.

 ### 무상태 프로토콜(스테이스리스)
  - 서버가 클라이언트의 상태를 보존하지 않는다는 뜻이다.
> Ex) 현실에서 아이스초코에 펄 두 번을 추가한 음료를 주문한다고 생각해보자.
>
> - 일반적인 점원에게 구매할 경우(stateful)
>   - 나: 아이스초코 하나 주세요.
>   - 점원: ㅇㅇ
>   - 나: 테이크 아웃할게요.
>   - 점원: ㅇㅇ
>   - 나: 앗 그리고 펄 두 번 추가해주세요.
>   - 점원: ㅇㅇ. 아이스초코에 펄 두 번 추가, 테이크아웃 맞으시죠?
>   - 나: 네.
>   - (5분 후)
>   - 나: 왜 음료 안나오나요?
>   - 점원: 죄송합니다. 곧 나올거예요
>  
> - stateless한 점원에게 주문할경우
>   - 나: 아이스초코 하나 주세요.
>   - 점원: ㅇㅇ
>   - 나: 테이크 아웃할게요.
>   - 점원: 뭘요?
>   - 나: 그리고 펄 두 번 추가해주세요.
>   - 점원: 어디에요?
>   - (5분 후)
>   - 나: 왜 음료 안나오나요?
>   - 점원: 누구세요?
>     
> - stateless한 점원에게 올바르게 주문하는 경우
>     - 나: 아이스 초코에 펄 두 번 추가해주세요. 포장해갈게요!
>     - 점원 : ㅇㅇ. 주문번호 3번이세요.
>     - (5분 후)
>     - 나: 저 주문번호 3번인데, 제 음료 언제나오나요?
>     - 점원: 죄송합니다. 곧 나올거예요     
<br>

- 정리
  <br>
  
  - 상태 유지(stateful): 중간에 다른 점원으로 바뀌면 안된다. 예를 들어 주문 후 음료가 왜 안나오냐고 묻기 전에 점원이 교대를 한다면 너 누구냐라는 말이 나올 수 밖에 없다.
    <br>
    
  - 무상태(stateless) : 중간에 다른 점원으로 바뀌어도 된다. <br> 
    +) 주문이 많아진다면 점원을 여러 명 투입해서 해결할 수 있다.
     <br>
     
  - 무상태 서버의 경우 클라이언트의 요청이 증가하면 서버를 증설하면 된다. (응답 서버 바꾸기 쌉가능이니까)<br>
    만약 요청을 보낸 서버 1에 장애가 난다면 중계 서버는 서버2로 이 요청을 던져 서버2가 이 요청에 응답하도록 한다.
    <br>
    
  - stateful 서버의 증설이 어려운 이유: 클라이언트A에게 응답한 서버1은 계속해서 A와 응답해야한다. 중간에 서버1에 장애가 난다면 클라이언트A는 처음부터 다시 요청을 보내야한다.
 <br>


 ### 비연결성
클라이언트가 서버에 요청을 보내고 서버가 클라이언트에 응답을 보내면, 서버는 연결을 유지하지 않고 연결을 끊어버린다. 따라서 최소한의 자원 유지가 가능하다. <br>
단점: tcp/ip연결을 다시해야하므로 3 way handshake 시간이 추가된다. 또 요청마다 수많은 자원을 반복적으로 다운로드 받아야한다. <br>
이 문제는 현재 http 지속 연결로 해결한다.

 ### HTTP메시지 
 ### 단순함, 확장 가능
 <br>

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
