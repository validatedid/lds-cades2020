# CMS Advanced Digital Signatures for Linked Data

This suite is intended to provide Advanced Digital (AdES) RSA signature support to Linked Data.

An advanced electronic signature (AdES) is an electronic signature that has met the requirements set forth under EU Regulation No 910/2014 (eIDAS-regulation) on electronic identification and trust services for electronic transactions in the European Single Market.

The main document describing the format is ETSI TS 101 733 Electronic Signature and Infrastructure (ESI) – CMS Advanced Electronic Signature (CAdES).


## CAdES Signature Suite

Following [Linking Data Proofs document](https://w3c-ccg.github.io/ld-proofs/), the following proof types have been defined and will be supported by the SSI eIDAS Bridge:

2020 CAdES Signature Suite using RSA signatures:
```JSON
{
  "id": "https://xxx/v1#CAdESRSASignature2020",
  "type": "RSAVerificationKey2018",
  "canonicalizationAlgorithm": "https://w3id.org/security#URDNA2015",
  "digestAlgorithm": "https://www.ietf.org/assignments/jwa-parameters#SHA256",
  "signatureAlgorithm": "https://tools.ietf.org/html/rfc5126"
}
```

## CAdES RSA Signature

```json
"proof": {
  "type": "CAdESSignature2020",
  "proofPurpose": "assertionMethod",
  "created": "2019-08-23T20:21:34Z",
  "x509CertificateChain": "MIIEEzCCAvugAwIBAgIUJ0hTJswF5BBreQgbEQL8FTLXwHAwDQYJKoZIhvcNAQELBQAwgZgxCzAJBgNVBAYTAk5MMRYwFAYDVQQIDA1Ob29yZC1Ib2xsYW5kMRIwEAYDVQQHDAlBbXN0ZXJkYW0xFDASBgNVBAoMC1Rlc3RDb21wYW55MQswCQYDVQQLDAJJVDEVMBMGA1UEAwwMU2NvdHQgTWFsbGV5MSMwIQYJKoZIhvcNAQkBFhRzbWFsbGV5QHNwaGVyZW9uLmNvbTAeFw0yMDEyMDIxNDMxMDVaFw0zMDExMzAxNDMxMDVaMIGYMQswCQYDVQQGEwJOTDEWMBQGA1UECAwNTm9vcmQtSG9sbGFuZDESMBAGA1UEBwwJQW1zdGVyZGFtMRQwEgYDVQQKDAtUZXN0Q29tcGFueTELMAkGA1UECwwCSVQxFTATBgNVBAMMDFNjb3R0IE1hbGxleTEjMCEGCSqGSIb3DQEJARYUc21hbGxleUBzcGhlcmVvbi5jb20wggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDkZfqj459pkdt5GLelamSySQP3owkyYOXW1NLTLr3dC_RzE8x3SRpHQwaRErm0VYvV35JVvubGZgatm5SNsTUHw7Ywrwy-hGFCXo2JOabL0lj3EpkpRPpVS7GXAlMxTvfZihw8IgmA3ZEnhnCYbyfKiCAOmVGLc_dViFTUuk2O6t6gkAdL0MhzU6nCBBariqlwWQxXf7z-nFubBrBio2l_GL6Pf6orvB_67V2PQEYnYlf24VtfdV34_QcU3T9bQjN2RhSzT9HYrYZtEXEmS4ARaN4mSoCnkITNsrGUz3LpX0ozxk2kQCUe89v8TUd-uYzA_sHXJXa7oHqTA1ZJVrtDAgMBAAGjUzBRMB0GA1UdDgQWBBT2b43zVAuqVWwFIZLSTSOdI3n5IDAfBgNVHSMEGDAWgBT2b43zVAuqVWwFIZLSTSOdI3n5IDAPBgNVHRMBAf8EBTADAQH_MA0GCSqGSIb3DQEBCwUAA4IBAQBnKynE3w04FyEHpYJs94eYrvKAgH6lvavHlDbiZxq1YgPwQN7lbFKIyZxsfcx1QGu1Rk_e-B7D-peIYGtL0-lQxbC88ogh03CaPqrJEhhmSxLEN-L3HQl-pItVUTKH8kaxHeC86ym2pOEJW2y7mVtPYkrgMiTjmOJj60hJEQE87VT_TB_soAXOm8oVXy1Ha3HwHZ4vouG_SwYhXWaqnOUDOifR579Cy53sMkuG0m7SuXxOZp20jnX7TaR8ElH8mZifTSBjkT2RNj1QhFG-Tl5nR_Q63j4xIw9f2Sj-jVclsuIcEQh00bo8pfdMhA-sMX1zCsOvG3sDnsfsqLmL7guV",
  "x509CertificateFingerprint": "MEiB6BbyLEylDZbtIbjpj5nM+QJQyPGartYi4x6Cj0Jl2FQ==",
  "verificationMethod": "did:factom:5d0dd58757119dd437c70d92b44fbf86627ee275f0f2146c3d99e441da342d9f#MEiB6BbyLEylDZbtIbjpj5nM+QJQyPGartYi4x6Cj0Jl2FQ==",
  "proofValue": "-----BEGIN PKCS7----- iG9w0BCRABCaB0MHICAQAwDQYLK... -----END PKCS7-----"
}
```


## Multiple proofs in json-ld document

```json
{
  "@context": [
    "https://www.w3.org/2018/credentials/v1",
    "https://www.w3.org/2018/credentials/examples/v1"
  ],
  "title": "Hello World!",
  "proof": [{
    "type": "Ed25519Signature2018",
    "proofPurpose": "assertionMethod",
    "created": "2019-08-23T20:21:34Z",
    "verificationMethod": "did:example:123456#key1",
    "challenge": "2bbgh3dgjg2302d-d2b3gi423d42",
    "domain": "example.org",
    "jws": "eyJ0eXAiOiJK...gFWFOEjXk"
  },
  {
    "type": "CAdESSignature2020",
    "proofPurpose": "assertionMethod",
    "created": "2017-09-23T20:21:34Z",
    "x509CertificateChain": "MIIEEzCCAvugAwIBAgIUJ0hTJswF5BBreQgbEQL8FTLXwHAwDQYJKoZIhvcNAQELBQAwgZgxCzAJBgNVBAYTAk5MMRYwFAYDVQQIDA1Ob29yZC1Ib2xsYW5kMRIwEAYDVQQHDAlBbXN0ZXJkYW0xFDASBgNVBAoMC1Rlc3RDb21wYW55MQswCQYDVQQLDAJJVDEVMBMGA1UEAwwMU2NvdHQgTWFsbGV5MSMwIQYJKoZIhvcNAQkBFhRzbWFsbGV5QHNwaGVyZW9uLmNvbTAeFw0yMDEyMDIxNDMxMDVaFw0zMDExMzAxNDMxMDVaMIGYMQswCQYDVQQGEwJOTDEWMBQGA1UECAwNTm9vcmQtSG9sbGFuZDESMBAGA1UEBwwJQW1zdGVyZGFtMRQwEgYDVQQKDAtUZXN0Q29tcGFueTELMAkGA1UECwwCSVQxFTATBgNVBAMMDFNjb3R0IE1hbGxleTEjMCEGCSqGSIb3DQEJARYUc21hbGxleUBzcGhlcmVvbi5jb20wggEiMA0GCSqGSIb3DQEBAQUAA4IBDwAwggEKAoIBAQDkZfqj459pkdt5GLelamSySQP3owkyYOXW1NLTLr3dC_RzE8x3SRpHQwaRErm0VYvV35JVvubGZgatm5SNsTUHw7Ywrwy-hGFCXo2JOabL0lj3EpkpRPpVS7GXAlMxTvfZihw8IgmA3ZEnhnCYbyfKiCAOmVGLc_dViFTUuk2O6t6gkAdL0MhzU6nCBBariqlwWQxXf7z-nFubBrBio2l_GL6Pf6orvB_67V2PQEYnYlf24VtfdV34_QcU3T9bQjN2RhSzT9HYrYZtEXEmS4ARaN4mSoCnkITNsrGUz3LpX0ozxk2kQCUe89v8TUd-uYzA_sHXJXa7oHqTA1ZJVrtDAgMBAAGjUzBRMB0GA1UdDgQWBBT2b43zVAuqVWwFIZLSTSOdI3n5IDAfBgNVHSMEGDAWgBT2b43zVAuqVWwFIZLSTSOdI3n5IDAPBgNVHRMBAf8EBTADAQH_MA0GCSqGSIb3DQEBCwUAA4IBAQBnKynE3w04FyEHpYJs94eYrvKAgH6lvavHlDbiZxq1YgPwQN7lbFKIyZxsfcx1QGu1Rk_e-B7D-peIYGtL0-lQxbC88ogh03CaPqrJEhhmSxLEN-L3HQl-pItVUTKH8kaxHeC86ym2pOEJW2y7mVtPYkrgMiTjmOJj60hJEQE87VT_TB_soAXOm8oVXy1Ha3HwHZ4vouG_SwYhXWaqnOUDOifR579Cy53sMkuG0m7SuXxOZp20jnX7TaR8ElH8mZifTSBjkT2RNj1QhFG-Tl5nR_Q63j4xIw9f2Sj-jVclsuIcEQh00bo8pfdMhA-sMX1zCsOvG3sDnsfsqLmL7guV",
    "x509CertificateFingerprint": "MEiB6BbyLEylDZbtIbjpj5nM+QJQyPGartYi4x6Cj0Jl2FQ==",
    "verificationMethod": "did:factom:5d0dd58757119dd437c70d92b44fbf86627ee275f0f2146c3d99e441da342d9f#MEiB6BbyLEylDZbtIbjpj5nM+QJQyPGartYi4x6Cj0Jl2FQ==",
    "proofValue": "-----BEGIN PKCS7----- iG9w0BCRABCaB0MHICAQAwDQYLK... -----END PKCS7-----"
  }]
}
```
