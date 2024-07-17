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

Digest
```
<xxx>   => md5(base64("arnav:abcd123"))
```

Why is it bad? 

- have to pass it everytime (might need user to type it every time) 
- sniff - easy to read your password 
  - happens on *EVERY* request - so larger surface area of attack 
- user fetch + password match = large overhead for each request 


### Encoding, Encryption, Signing 

- encoding          decoding
- encryption        decryption
- compression       decompression

- hashing 

### HS256 JWT 


header = `{alg:JWT,typ:HS256}` 
payload = `{"sub":"1234567890","iat":1516239022,"exp":1516239922}` 


hash =  sha256(base64(header) + "." + base64(payload))

26000efbbee7aca101863786306eb5a6537b9daa2d7b04110075ac8940c4d614

signature = hmac (hash, key)

```
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIyMzYyNDU0IiwiaWF0IjoxNTE2MjM5MDIyLCJleHAiOjE1MTYyMzk5MjJ9.nPB0_xHOyOGNgizMfx7_tfjiL_2nquiV2gK1n0GhWSQ
```

```
Authorization: JWT xxxx
```