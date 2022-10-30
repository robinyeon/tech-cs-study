# SOP, CORS
### 연다은봄

**1. SOP (Same-Origin Policy)**        
\- 동일한 출처, 똑같은 URL끼리만 API 등의 데이터 접근이 가능하게 하는 것                      
\- 어떤 출처에서 불러온 문서나 스크립트가 다른 출처에서 가져온 리소스와 상호작용하는 것을 제한하는 보안방식                   
\- 잠재적으로 해로울 수 있는 문서를 분리함으로써 공격받을 수 있는 경로를 줄임                       
\- 두 URL의 프로토콜, 포트, 호스트가 모두 같아야 동일한 출처라고 봄                    

**2. CORS (Cross-Origin Resource Sharing)**       
\- 다른 출처 간에 리소스를 공유하여 정보 요청과 반환이 가능하게끔 하는 것                 
\- req에 Origin이라는 헤더를 추가해 특정 도메인이나 * (모든 도메인)을 적어준다.                
\- 이 Origin에서 보낸 출처 값이 서버의 답장 헤더에 담긴 Access-Control-Allow-Origin에 똑같이 있다면 안전한 요청으로 간주하고 응답 진행                   
\- GET, POST 외의 PUT, DELETE 등은 서버의 데이터에 영향을 줄 수 있는 요청들이기 때문에 Simple-request 이전에 **Preflight**라는 사전 허락이 진행되어야 한다. (허용여부 검증)      
          
[참고](https://youtu.be/bW31xiNB8Nc)      
              
-----------------------
