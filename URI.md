# URI
Uniform Resource Identifier

- Uniform: 리소스를 식별하는 통일된 방식
- Resource: 자원, URI로 식별할 수 있는 모든 것
- Identifier: 다른 항목과 구분하는데 필요한 정

> URI? URL? URN?
>> URI(Resource Identifier) 개념 안에 URL, URN이 포함되어 있음
>> 
>>URL: Resource Locator - 리소스가 있는 위치를 지정 
>>
>>URN: Resorce Name - 리소스에 이름을 부여

# URL
scheme://[userinfo@]host[:port][/path][?query][#fragment]
https://www.google.com:443/search?q=hello&hl=ko

- 프로토콜: https
- 호스트명: www.google.com
- 포트 번호: 443
- path: /search
- 쿼리 파라미터: q=hello&hl=ko

>scheme
> - 주로 프로토콜이 사용된다.
> - 프로토콜이란: 어떤 방식으로 자원에 접근할 것인가 하는 약속 규칙
>  
>  ex. http(80),https(443),ftp

>host
> - 호스트명을 입력한다. 도메인명 또는 IP주소를 직접 기입해도 된다용~

> PORT
> - 접속포트로, 생략 가능하다.

>PATH
>- 리소스 경로에 해당하며, 계층적 구조를 띤다.

> QUERY
> - key=value 형태로, ?로 시작한다. &를 이용하여 추가가 가능하다.
>
> ex. ?keyA=vauleA&keyB=valueB
> 
> - query parameter, query string 등으로도 불린다.(웹서버에 제공하는 파라미터 정보다~ 숫자를 적어도 문자 형태로 넘어간다~)


> fragment
> - html 내부 북마크 등에 사용된다. 서버에 전송하는 정보는 아니다. 


# 웹 브라우저 요청 흐름
 
