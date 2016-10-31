# Crypto

The Crypto method is a powerful tool which performs basic encryption and decryption which can be done so that each user will have a unique encrypted value, or a shared value. It uses OpenSSL to do all of its encryption, but more importantly its encrypted result is entirely URL friendly which enables you to use it as a UUID to be displayed in your URLs rather than obvious ID values.

## encrypt()

```
Crypto::encrypt('testing');
// helper
crypto_encrypt();
```

## decrypt()

```
Crypto::decrypt('encrypted-text');
// helper
crypto_decrypt();
```

## uuid()

```
Crypto::uuid();
// helper
crypto_uuid();
```

## shared()

The shared as mentioned uses a common encryption key so that the encrypted values can be shared.

```
Crypto::shared()->encrypt('testing');
Crypto::shared()->decrypt('encrypted-text');
```
