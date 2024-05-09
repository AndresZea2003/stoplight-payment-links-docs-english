---
stoplight-id: y9sjfrpqghub7
---

# Authentication

To interact with the Payment Link API, you use an authentication similar to that of
[Checkout](https://docs.placetopay.dev/checkout/authentication) to ensure that your operations are secure and authenticated.

## Credentials

To authenticate, you must have your `login` and `secretKey` credentials.

- **login:** Site identifier, which can be considered public as it travels as plain data in API requests.
- **secretKey:** Site's secret key, which must be kept private. A new `tranKey` will be generated from this data and sent in the requests.

### How to generate authentication?

You must know and prepare the following data:

- **login:** Login credential provided when starting your integration. Site identifier.

- **secretKey:** secretKey credential provided when starting your integration. Site's secret key.

- **seed:** This is the date when the authentication was generated. The date must be in ISO 8601 format. `Example: 2023-06-21T09:56:06-05:00`

- **nonce:** An arbitrary value that identifies a request as unique. It is generated and used for other operations. When sending it, it must be encoded in base 64. `Example: base64('927342197')`

- **tranKey:** It is generated programmatically for each request. It is generated using the following formula `Base64(SHA-256(nonce + seed + secretKey))`. This formula must be translated according to the programming language used.