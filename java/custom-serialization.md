# Custom serialization

Java has two methods that can be used to customize the serialization process:

- `writeObject()`
- `readObject()`

```java
public class ClassName implements Serializable {
    
    // transient and non-transient fields

    private void writeObject(ObjectOutputStream oos) throws Exception {
       // write the custom serialization code here
    }

    private void readObject(ObjectInputStream ois) throws Exception {
       // write the custom deserialization code here
    }
}
```

### Initialize transient variables

- Since `writeObject` doesn't serialize the password (use transient), we can solve this problem by initializing the password when deserializing the object.

```java
public class User implements Serializable {
    String userName = "admin";
    transient String password = "password";
  
    private void readObject(ObjectInputStream ois) throws Exception {
        ois.defaultReadObject();
        password = new String(" ");
    } 
}
```

### Uses for custom serialization

- To encrypt important fields of a class
- To use a more compressed serialization

```java
public class User implements Serializable {
    String userName = "admin";
    transient String password = "password";

    private void writeObject(ObjectOutputStream oos) throws Exception {
        oos.defaultWriteObject();
        String encryptPassword = encrypt(password);
        oos.writeObject(encryptPassword);
    }

    private void readObject(ObjectInputStream ois) throws Exception {
        ois.defaultReadObject();
        String password = decrypt((String) ois.readObject());
    }
}
```