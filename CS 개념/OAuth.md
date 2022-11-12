# 황현성

## 🍏 OAuth란

> 인증을 위한 개방형 표준 프로토콜

> 특정 서비스가 제 3의 플랫폼의 기능을 제공할 때, 해당 플랫폼에 등록된 유저에 대한 정보에 접근하기 위해 해당 플랫폼으로부터 접근 권한을 위임 받을 수 있도록 하는 프로토콜

내가 A라는 플랫폼과 관련된 기능을 제공하는 B 서비스를 만들었을 때, 해당 서비스를 C라는 유저가 이용한다면 우선 C가 A 플랫폼에 등록되어있는지 확인해야한다.

이를 위해 C가 B에게 A에 등록된 아이디와 비밀번호를 전달하는 것은 매우 위험한 일이다.

이러한 위험성을 보완하고 안전하게 인증하기 위해 OAuth가 등장하였다. 

물론 기존에도 위험성을 인지하고 다양한 방법으로 인증하는 방식이 있었지만 표준화 되지는 않았다. OAuth가 등장하면서 점차 표준화 되었고, 현재는 OAuth 2.1까지 확장된 상태이다.

<br />

## 🍊 OAuth의 주체

OAuth의 주체는 3~4가지로 구분할 수 있다.

- Resource Server: 유저가 필요한 자원을 갖고 있는 서버
- Authorization Server: Resource Owner의 인증 요청에 따라 Client에게 액세스 토큰을 발급하는 서버
- Resource Owner: Resource Server의 자원을 소유한 주체(유저), 주인
- Client: Resource Server의 자원을 가져와 서비스를 제공하는 주체

Resource Server와 Authorization Server는 하나로 구성하거나 분리하여 구성할 수 있다.



|Resource Owner|Client|Authorization Server|Resource Server|
|---|---|---|---|
|불특정 유저|내가 만든 서비스(서버)|페이스북 Authorization Server|페이스북 Resource Server|

<br />

## 🍋 OAuth의 절차

### Resource Server에 Client를 register

- 클라이언트마다 조금씩 다른 등록 방식
- 공통적으로 ClientID, ClientSecret, Authorized redirect URLs를 Resource Server에 등록
- ClientId: 애플리케이션(서비스)의 식별자
- ClientSecretL: ClientId에 대한 비밀번호
- Authorized redirect URLs: Resource server가 제공하는 Authorized Code를 받을 주소

### Resource Owner의 승인

Resource Server가 제공하는 기능 중 필요한 기능만 인증을 받을 때 Resource Owner의 승인이 필요함

1. Resource Owner가 Client를 이용할 때 Resource Server의 자원에 접근해야할 경우가 있음

2. Client는 Resource Owner에게 보통 Resource Server에 로그인할 수 있는 폼을 보여줌, client_id와 scope와 redirect_uri이 명시된 링크로 Resource Owner를 이동하게함

3. 해당 링크로 Resource Owner는 Resource Server에 접속하게 되면 로그인 유무를 판단, 로그인이 안됐을 경우 로그인 폼을 보여줌

4. 로그인이 성공했다면 Resource Server는 Resource Owner가 타고 들어온 링크의 client_id가 Resource Server에 등록된 client_id 인지 확인, 없다면 접근 불가

5. 있다면 Resource Owner가 타고 들어온 링크의 redirect_uri 값과 Resource Server에 등록된 client_id의 redirect URL이 같은 지 확인, 다르면 접근 불가

6. 같다면 Resource Owner에게 scope에 해당하는 권한을 Client에게 부여할 것인지 확인

7. 허용한다면 Resource Server는 Resource Owner(user)에 대한 고유 아이디와 해당 Resource Owner(user)가 권한을 허락한 스코프 정보를 저장

### Resource Server의 승인

1. Resource Server는 Resource Owner의 정보를 저장하면서 Authorization code를 만들어 Resource Owner에게 전달
```
ex) Location: https://client/callback?code=3
```
2. Resource Owner는 자동으로 해당 주소(Client 에게)로 리다이렉션, Client는 Resource Owner의 Authorization code 값을 저장

3. 이후 Client는 Resource Server에 직접 접속, 접속할 때 Authorization code, redirect_url, client_id, client_secret 값을 전달

4. Resource Server는 Client에게 받은 데이터가 Resource Server가 갖고 있는 데이터와 일치하는 지 확인

### Access Token 발급

1. 일치하면 Resource Server와 Client는 authorization code를 지움

2. Resource Server는 accessToken을 발급하고 Client에게 전달

3. 이후 Resource Server는 access Token을 확인하고 access Token에 해당하는 Resource Owner에게 scope에 맞는 기능과 권한을 허용


참고 : [생활코딩 OAuth 강의](https://www.youtube.com/watch?v=hm2r6LtUbk8&list=PLuHgQVnccGMA4guyznDlykFJh28_R08Q-&index=1)
