# Authentication and Authorization 

## Session 1 : 2024-07-17 


## Topics 

- authentication 
  - for webservice
  - how API requests are authenticated 
- identification vs authentication vs authorization
  - authentication via authorization 
  - oauth 2.0 
  - SSO 
  - third party auth 
  - federated auth 
- tokens 
  - bearer tokens
  - JWTs
  - cookies 
  - stateless vs stateful authentication 
- 2FA / MFA 
  - TOTP
  - OTP 

-------- 

- access control
- role based auth 


## Notes 

### Basic Auth 

Request Header 

```
Authorization: Basic <xxxxxx>
```

```
<xxx>   =>  base64(username + ":" + password)
            base64("arnav:abcd123")

```

Why is it bad? 

- have to pass it everytime (might need user to type it every time) 
- sniff - easy to read your password 
  - happens on *EVERY* request - so larger surface area of attack 
- user fetch + password match = large overhead for each request 