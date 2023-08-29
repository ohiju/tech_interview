# http와 https의 차이점

참고: https://aws.amazon.com/ko/compare/the-difference-between-https-and-http/

- HTTP(Hypertext Transfer Protocol)은 클라이언트와 서버 간 통신을 위한 통신 규칙 세트 또는 프로토콜이다. 사용자가 웹 사이트를 방문하면 사용자 브라우저가 웹 서버에 HTTP 요청을 전송하고 웹 서버는 HTTP 응답으로 응답한다. 웹 서버와 사용자 브라우저는 데이터를 일반 텍스트로 교환한다. 간단히 말해 HTTP 프로토콜은 네트워크 통신을 작동하게 하는 기본 기술이다.

- HTTPS(Hypertext Tranfer Protocol Secure)는 HTTP의 확장 버전 또는 더 안전한 버전이다. HTTPS에서는 브라우저와 서버가 데이터를 전송하기 전에 안전하고 암호화된 연결을 설정한다. 

## HTTP 프로토콜 작동 방식
- HTTP는 [OSI](/OSI_7layer)(Open Systems Interconnection) 네트워크 통신 모델의 애플리케이션 계층 프로토콜이다. HTTP는 여러 유형의 요청과 응답을 정의한다.
    - 웹 사이트의 일부 데이터를 보려는 경우 HTTP GET 요청
    - 연락처 양식 작성과 같은 일부 정소를 전송하려는 경우 HTTP PUT 요청

<br>

- 마찬가지로, 서버는 숫자 코드 및 데이터 양식으로 다양한 유형의 HTTP 응답을 전송.
    - 200 - OK(정상)
    - 400 - Bad request(잘못된 요청)
    - 404 - Resource not found(리소스를 찾을 수 없음)
  
<br>

- 이러한 요청 및 응답 통신은 일반적으로 사용자에게 보이지 않음. 브라우저와 웹 서버가 사용하는 통신 방식이므로 모든 사용자에게 일관되게 작동함.

## HTTPS 프로토콜 작동 방식
- HTTP는 암호화되지 않은 데이터를 전송하므로 제 3자가가로채고 읽을 수 있기에, 통신에 다른 보안 계층을 추가하기 위해 HTTPS로 프로세스가 확장됨.

- HTTPS는 HTTP 요청 및 응답을 SSL 및 TLS 기술에 결합함.

- HTTPS 웹사이트는 독립된 인증 기관(CA-Certificate Authority)에서 SSL/TLS 인증서를 획득해야 한다. 
  1. 사용자 브라우저의 주소 표시줄에 https://URL 형식을 입력하여 HTTPS 웹사이트를 방문한다.
  2. 브라우저는 서버의 SSL 인증서를 요청하여 사이트의 신뢰성을 검증하려고 한다.
  3. 서버는 퍼블릭 키가 포함된 SSL 인증서를 회신으로 전송한다.
  4. 웹 사이트의 SSL 인증서는 서버 아이덴티티를 증명한다. 브라우저에서 인증되면, 브라우저가 퍼블릭 키를 사용하여 비밀 세션 키가 포함된 메시지를 암호화하고 전송한다. 
  5. 웹 서버는 프라이빗 키를 사용하여 메시지를 해독(복호화)하고 세션키를 검색한다. 그런 다음, 세션 키를 암호화하고 브라우저에 승인 메시지를 전송한다.
  6. 이제 브라우저와 웹 서버 모두 동일한 세션 키를 사용하여 메시지를 안전하게 교환하도록 전환한다.

SSL/TSL : https://aws.amazon.com/ko/what-is/ssl-certificate/