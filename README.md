do these steps to test proj
1.  npm install
2.  install rest client extension by huachao mao.
3.  generate ACCESS_TOKEN_SECRET and REFRESH_TOKEN_SECRET
4.  paste them in .env.
5.  start npm run devStartAuth and npm run devStart.
6.  open requests.rest editor and press "send request" above POST localhost:4000/login when y have rest client ext installed.
7.  this will request app.post('/login') in authServer.js editor and returns access token and refresh token.
8.  paste access token behind Authorization: Bearer in GET localhost:3000/posts in server.js.
9.  when access token expired in GET, use POST localhost:4000/token with refresh token from /login response.
10. try delete refresh token.


how to generate ACCESS_TOKEN_SECRET and REFRESH_TOKEN_SECRET?
1.  new terminal.
2.  typein node and press enter.
3.  typein require('crypto').randomBytes(64).toString('hex') and press enter.
4.  paste the output without apostrophe "'".
5.  paste the another output without apostrophe in REFRESH_TOKEN_SECRET.

why we use refresh token?
1.  invalidating someone who've stolen access token with little expiration time if he is without refresh token.
2.  both access and refresh token decouples away from sv-session management that uses cl-cookie. jwt enables microservices, authorization and decouple one-server-to-another that delegates token and bases on crypto-signed string.

Ref:: JWT Authentication Tutorial - Node.js by Web Dev Simplified.