# Web Server, WAS

## 연다은봄

### Web Server
> 웹 브라우저(클라이언트)로 부터 HTTP 요청을 받아 HTML 문서와 같은 정적 컨텐츠를 제공하는 프로그램

\- 클라이언트로 부터 HTTP 요청을 받을 수 있고,  
\- 정적 콘텐츠 요청 시 Web Server 단계에서 제공해주고,  
\- 동적 콘텐츠 요청 시 WAS로 전달하여 WAS가 처리한 결과를 클라이언트에 전달한다.  

※ 정적 컨텐츠: 사용자가 달라지더라도 바뀌지 않는 컨텐츠 (ex) jpeg, html, css 등

<br/>

### WAS(Web Application Server)
> DB조회나 다양한 로직처리를 요구하는 동적인 컨텐츠를 제공하기 위해 만들어진 프로그램  

\- 클라이언트로부터 HTTP 요청을 받을 수 있다 (대부분의 WAS는 Web Server를 내장하고 있음)    
\- 요청에 맞는 정적 콘텐츠를 제공해주고,  
\- DB조회나 다양한 로직 처리를 통해 동적 컨텐츠를 제공할 수 있다.  

(ex) 엘리스 프로젝트에서 WAS는 노드, Web server는 Nginx
\- WAS는 DB에 접근하고 비즈니스 접근에 최적화  
\- Web server는 http에 최적화, 웹에 최적화  

<br/>

### Web Server의 필요성
Web server를 같이 사용했을 때의 장점이 뚜렷하기 때문이다.

**1. 책임 분할을 통한 서버 부하 방지**   
\- 정적 콘텐츠: Web server가 담당   
\- 동적 콘텐츠 : WAS가 담당해서 역할 분배   

<br/>

**2. Web server의 로드밸런싱**   
**로드 밸런서**로서의 역할이 확실하다.  
여러 요청을 여러 WAS가 나누어서 처리할 수 있도록 배분 및 설정해준다.  

<br/>

**3. 여러대의 WAS Health check**    
로드밸런싱을 진행하다보면 특정 WAS에서 정상작동을 하지 않는 경우가 생긴다.  
이때 Web server가 WAS에 주기적으로 http 요청을 보내며 서버의 상태를 체크한다.  
이러한 기능을 Health check(헬스체크)라고 한다.  
(ex) 특정 url 요청에 200 응답이 오는가?  

> **Interval**: 헬스 체크를 통해 서버 상태를 확인하는 요청을 날리는 주기(default: 5초)  
> **Fails**: 몇회 연속 실패하면 서버가 비정상이라고 인지(default: 1회)   
> **Passes**: 서버가 다시 복구되어 몇회 연속 성공하면 서버가 정상으로 인지(default: 1회)   

<br/>

**4. 보안**   
[리버스프록시](https://losskatsu.github.io/it-infra/reverse-proxy/#2-%ED%8F%AC%EC%9B%8C%EB%93%9C-%ED%94%84%EB%A1%9D%EC%8B%9Cforward-%EC%84%9C%EB%B2%84%EB%9E%80)를 통해 WAS(실제서버)를 외부에 노출시키지 않음으로써 보안성을 가져간다.   

<br/>
