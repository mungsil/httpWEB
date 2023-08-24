# Get
# Post
# Put
# Patch
# Delete

<hr>

- 활용은 ppt 5.http method-use 의 12p~14p를 참고하자.

<hr> 

## HTTP API 설계 예시
엔드포인트는 리소스에 집중하자. 동사는 HTTP 메소드를 이용하면 된다.
http 메소드로 해결하기 어려운 경우 컨트롤 uri를 사용하자.

- (HTTP API) post 기반으로 등록할 때와 put 기반으로 등록할 때의 차이점에 주목하자.
- 참고로, html form을 사용할 때는 GET과 POST만 사용할 수 있다.

- POST 메소드로 회원 등록하는 경우
    - 요청 시 등록할 회원의 리소스 uri를 몰라도 된다. 리소스 uri는 서버에서 만들어서 결정해준다.
    - 예시) <br> 요청: POST /members <br> 응답: HTTP/1.1 Created<br> Location: /members/100
    - 이러한 형식을 <b>컬렉션</b>이라고 한다. 컬렉션이란, 서버가 관리하는 리소스 디렉토리를 뜻한다.
    - 여기서 컬렉션은 /members이다.
    
- PUT 메소드로 파일 등록하는 경우
    - 요청 시 클라이언트가 등록할 회원의 리소스 uri를 알고 있어야한다.
    - 이러한 형식을 <b>스토어</b>라고 한다. 스토어는 클라이언트가 관리하는 리소스 저장소이다. 클라이언트가 리소스의 uri를 알고 관리한다.
    - put files/{filename} : 등록하려는 파일 이름과 똑같은 이름을 가진 기존 파일이 있을 경우 이를 삭제하고 완전히 덮어야하기 때문에 PUT이 적절하다.

+) 문서, 컨트롤uri...
 
 - 설계 시 참고: https://restfulapi.net/resource-naming/
  
