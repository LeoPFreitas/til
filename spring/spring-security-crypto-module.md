# Spring Security Crypto module

Spring Security provides its own solution for using encryption and decryption functions and generating keys.

## key generators

- Object used to generate a specific kind of key, generally needed for an encryption or hashing algorithm.
- Two interfaces represent the two main types of key generators: `BytesKeyGenerator` and `StringKeyGenerator`

```java
public interface StringKeyGenerator {
    String generateKey();
}

public interface BytesKeyGenerator {
  int getKeyLength();
  byte[] generateKey();
}

// obtain a salt value
StringKeyGenerator keyGenerator = KeyGenerators.string();
String salt = keyGenerator.generateKey();

BytesKeyGenerator keyGenerator = KeyGenerators.secureRandom();
byte [] key = keyGenerator.generateKey();
int keyLength = keyGenerator.getKeyLength();

// customizing key length - returns a different key
BytesKeyGenerator keyGenerator = KeyGenerators.secureRandom(16);

// returns the same key -- key1 = key2
BytesKeyGenerator keyGenerator = KeyGenerators.shared(16);
byte [] key1 = keyGenerator.generateKey();
byte [] key2 = keyGenerator.generateKey();
```

## Encryptors

```java
public interface TextEncryptor {
  String encrypt(String text);
  String decrypt(String encryptedText);
}

public interface BytesEncryptor {
  byte[] encrypt(byte[] byteArray);
  byte[] decrypt(byte[] encryptedByteArray);
}

// bytes encryptor
String salt = KeyGenerators.string().generateKey();
String password = "secret";
String valueToEncrypt = "HELLO";

BytesEncryptor e = Encryptors.standard(password, salt);
byte [] encrypted = e.encrypt(valueToEncrypt.getBytes());
byte [] decrypted = e.decrypt(encrypted);

BytesEncryptor e = Encryptors.stronger(password, salt);

// text encryptor
String salt = KeyGenerators.string().generateKey();
String password = "secret";
String valueToEncrypt = "HELLO";

TextEncryptor e = Encryptors.text(password, salt);
String encrypted = e.encrypt(valueToEncrypt);
String decrypted = e.decrypt(encrypted);

// encrypted1 = encrypted2
String salt = KeyGenerators.string().generateKey();
String password = "secret";
String valueToEncrypt = "HELLO";

TextEncryptor e = Encryptors.queryableText(password, salt);

String encrypted1 = e.encrypt(valueToEncrypt);
String encrypted2 = e.encrypt(valueToEncrypt);
```