---
title: OTP
order: 3
---

It's pretty easy to add two-factor authentication to your cheetah app with e.g. Google Authenticator.

## Create a Secret

Generate a random secret (with a length of 64 by default).

```ts
const randomSecret = otp.secret(128) // with a length of 128
```

## Retrieve a Token

Get the 6-digit token for a given timestamp (omit the timestamp to use the current time).

```ts
const token = otp.secret(secret, timestamp)
```

## Create a URI

Create a URI that you can use, for example, for a QR code to scan with Google Authenticator.

```ts
//          otp.uri(label, issuer, secret)
const uri = otp.uri('user@email.com', 'My Company', secret)
```

## Validate a Token

Determine if a given token is valid.

```ts
const isValid = otp.validate(token, secret)
```
