# ํฉํ์ฑ

## ๐ OAuth๋

> ์ธ์ฆ์ ์ํ ๊ฐ๋ฐฉํ ํ์ค ํ๋กํ ์ฝ

> ํน์  ์๋น์ค๊ฐ ์  3์ ํ๋ซํผ์ ๊ธฐ๋ฅ์ ์ ๊ณตํ  ๋, ํด๋น ํ๋ซํผ์ ๋ฑ๋ก๋ ์ ์ ์ ๋ํ ์ ๋ณด์ ์ ๊ทผํ๊ธฐ ์ํด ํด๋น ํ๋ซํผ์ผ๋ก๋ถํฐ ์ ๊ทผ ๊ถํ์ ์์ ๋ฐ์ ์ ์๋๋ก ํ๋ ํ๋กํ ์ฝ

๋ด๊ฐ A๋ผ๋ ํ๋ซํผ๊ณผ ๊ด๋ จ๋ ๊ธฐ๋ฅ์ ์ ๊ณตํ๋ B ์๋น์ค๋ฅผ ๋ง๋ค์์ ๋, ํด๋น ์๋น์ค๋ฅผ C๋ผ๋ ์ ์ ๊ฐ ์ด์ฉํ๋ค๋ฉด ์ฐ์  C๊ฐ A ํ๋ซํผ์ ๋ฑ๋ก๋์ด์๋์ง ํ์ธํด์ผํ๋ค.

์ด๋ฅผ ์ํด C๊ฐ B์๊ฒ A์ ๋ฑ๋ก๋ ์์ด๋์ ๋น๋ฐ๋ฒํธ๋ฅผ ์ ๋ฌํ๋ ๊ฒ์ ๋งค์ฐ ์ํํ ์ผ์ด๋ค.

์ด๋ฌํ ์ํ์ฑ์ ๋ณด์ํ๊ณ  ์์ ํ๊ฒ ์ธ์ฆํ๊ธฐ ์ํด OAuth๊ฐ ๋ฑ์ฅํ์๋ค. 

๋ฌผ๋ก  ๊ธฐ์กด์๋ ์ํ์ฑ์ ์ธ์งํ๊ณ  ๋ค์ํ ๋ฐฉ๋ฒ์ผ๋ก ์ธ์ฆํ๋ ๋ฐฉ์์ด ์์์ง๋ง ํ์คํ ๋์ง๋ ์์๋ค. OAuth๊ฐ ๋ฑ์ฅํ๋ฉด์ ์ ์ฐจ ํ์คํ ๋์๊ณ , ํ์ฌ๋ OAuth 2.1๊น์ง ํ์ฅ๋ ์ํ์ด๋ค.

<br />

## ๐ OAuth์ ์ฃผ์ฒด

OAuth์ ์ฃผ์ฒด๋ 3~4๊ฐ์ง๋ก ๊ตฌ๋ถํ  ์ ์๋ค.

- Resource Server: ์ ์ ๊ฐ ํ์ํ ์์์ ๊ฐ๊ณ  ์๋ ์๋ฒ
- Authorization Server: Resource Owner์ ์ธ์ฆ ์์ฒญ์ ๋ฐ๋ผ Client์๊ฒ ์ก์ธ์ค ํ ํฐ์ ๋ฐ๊ธํ๋ ์๋ฒ
- Resource Owner: Resource Server์ ์์์ ์์ ํ ์ฃผ์ฒด(์ ์ ), ์ฃผ์ธ
- Client: Resource Server์ ์์์ ๊ฐ์ ธ์ ์๋น์ค๋ฅผ ์ ๊ณตํ๋ ์ฃผ์ฒด

Resource Server์ Authorization Server๋ ํ๋๋ก ๊ตฌ์ฑํ๊ฑฐ๋ ๋ถ๋ฆฌํ์ฌ ๊ตฌ์ฑํ  ์ ์๋ค.



|Resource Owner|Client|Authorization Server|Resource Server|
|---|---|---|---|
|๋ถํน์  ์ ์ |๋ด๊ฐ ๋ง๋  ์๋น์ค(์๋ฒ)|ํ์ด์ค๋ถ Authorization Server|ํ์ด์ค๋ถ Resource Server|

<br />

## ๐ OAuth์ ์ ์ฐจ

### Resource Server์ Client๋ฅผ register

- ํด๋ผ์ด์ธํธ๋ง๋ค ์กฐ๊ธ์ฉ ๋ค๋ฅธ ๋ฑ๋ก ๋ฐฉ์
- ๊ณตํต์ ์ผ๋ก ClientID, ClientSecret, Authorized redirect URLs๋ฅผ Resource Server์ ๋ฑ๋ก
- ClientId: ์ ํ๋ฆฌ์ผ์ด์(์๋น์ค)์ ์๋ณ์
- ClientSecretL: ClientId์ ๋ํ ๋น๋ฐ๋ฒํธ
- Authorized redirect URLs: Resource server๊ฐ ์ ๊ณตํ๋ Authorized Code๋ฅผ ๋ฐ์ ์ฃผ์

### Resource Owner์ ์น์ธ

Resource Server๊ฐ ์ ๊ณตํ๋ ๊ธฐ๋ฅ ์ค ํ์ํ ๊ธฐ๋ฅ๋ง ์ธ์ฆ์ ๋ฐ์ ๋ Resource Owner์ ์น์ธ์ด ํ์ํจ

1. Resource Owner๊ฐ Client๋ฅผ ์ด์ฉํ  ๋ Resource Server์ ์์์ ์ ๊ทผํด์ผํ  ๊ฒฝ์ฐ๊ฐ ์์

2. Client๋ Resource Owner์๊ฒ ๋ณดํต Resource Server์ ๋ก๊ทธ์ธํ  ์ ์๋ ํผ์ ๋ณด์ฌ์ค, client_id์ scope์ redirect_uri์ด ๋ช์๋ ๋งํฌ๋ก Resource Owner๋ฅผ ์ด๋ํ๊ฒํจ

3. ํด๋น ๋งํฌ๋ก Resource Owner๋ Resource Server์ ์ ์ํ๊ฒ ๋๋ฉด ๋ก๊ทธ์ธ ์ ๋ฌด๋ฅผ ํ๋จ, ๋ก๊ทธ์ธ์ด ์๋์ ๊ฒฝ์ฐ ๋ก๊ทธ์ธ ํผ์ ๋ณด์ฌ์ค

4. ๋ก๊ทธ์ธ์ด ์ฑ๊ณตํ๋ค๋ฉด Resource Server๋ Resource Owner๊ฐ ํ๊ณ  ๋ค์ด์จ ๋งํฌ์ client_id๊ฐ Resource Server์ ๋ฑ๋ก๋ client_id ์ธ์ง ํ์ธ, ์๋ค๋ฉด ์ ๊ทผ ๋ถ๊ฐ

5. ์๋ค๋ฉด Resource Owner๊ฐ ํ๊ณ  ๋ค์ด์จ ๋งํฌ์ redirect_uri ๊ฐ๊ณผ Resource Server์ ๋ฑ๋ก๋ client_id์ redirect URL์ด ๊ฐ์ ์ง ํ์ธ, ๋ค๋ฅด๋ฉด ์ ๊ทผ ๋ถ๊ฐ

6. ๊ฐ๋ค๋ฉด Resource Owner์๊ฒ scope์ ํด๋นํ๋ ๊ถํ์ Client์๊ฒ ๋ถ์ฌํ  ๊ฒ์ธ์ง ํ์ธ

7. ํ์ฉํ๋ค๋ฉด Resource Server๋ Resource Owner(user)์ ๋ํ ๊ณ ์  ์์ด๋์ ํด๋น Resource Owner(user)๊ฐ ๊ถํ์ ํ๋ฝํ ์ค์ฝํ ์ ๋ณด๋ฅผ ์ ์ฅ

### Resource Server์ ์น์ธ

1. Resource Server๋ Resource Owner์ ์ ๋ณด๋ฅผ ์ ์ฅํ๋ฉด์ Authorization code๋ฅผ ๋ง๋ค์ด Resource Owner์๊ฒ ์ ๋ฌ
```
ex) Location: https://client/callback?code=3
```
2. Resource Owner๋ ์๋์ผ๋ก ํด๋น ์ฃผ์(Client ์๊ฒ)๋ก ๋ฆฌ๋ค์ด๋ ์, Client๋ Resource Owner์ Authorization code ๊ฐ์ ์ ์ฅ

3. ์ดํ Client๋ Resource Server์ ์ง์  ์ ์, ์ ์ํ  ๋ Authorization code, redirect_url, client_id, client_secret ๊ฐ์ ์ ๋ฌ

4. Resource Server๋ Client์๊ฒ ๋ฐ์ ๋ฐ์ดํฐ๊ฐ Resource Server๊ฐ ๊ฐ๊ณ  ์๋ ๋ฐ์ดํฐ์ ์ผ์นํ๋ ์ง ํ์ธ

### Access Token ๋ฐ๊ธ

1. ์ผ์นํ๋ฉด Resource Server์ Client๋ authorization code๋ฅผ ์ง์

2. Resource Server๋ accessToken์ ๋ฐ๊ธํ๊ณ  Client์๊ฒ ์ ๋ฌ

3. ์ดํ Resource Server๋ access Token์ ํ์ธํ๊ณ  access Token์ ํด๋นํ๋ Resource Owner์๊ฒ scope์ ๋ง๋ ๊ธฐ๋ฅ๊ณผ ๊ถํ์ ํ์ฉ


์ฐธ๊ณ  : [์ํ์ฝ๋ฉ OAuth ๊ฐ์](https://www.youtube.com/watch?v=hm2r6LtUbk8&list=PLuHgQVnccGMA4guyznDlykFJh28_R08Q-&index=1)
