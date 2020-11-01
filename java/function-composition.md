# Function composition

- It is a mechanism for combining functions to obtain more complicated functions
- The functional interface `Function<T, R>` has two default method `compose` and `andThen` for composing new functions
- Generally, `f.compose(g).apply(x)` is the same as `f(g(x))`, and `f.andThen(g).apply(x)` is the same as `g(f(x))`.

```java
Function<Integer, Integer> adder = x -> x + 10;
Function<Integer, Integer> multiplier = x -> x * 5;

// compose: adder(multiplier(5))
System.out.println("result: " + adder.compose(multiplier).apply(5));
// 35

// andThen: multiplier(adder(5))
System.out.println("result: " + adder.andThen(multiplier).apply(5));
// 75
```

### Composing predicates

All functional interfaces representing predicates (`Predicate<T>`, `IntPredicate` and others) have three methods for composing new predicates: `and`, `or` and `negate`.

```java
IntPredicate isOdd = n -> n % 2 != 0;
IntPredicate lessThan11 = n -> n < 11;

IntPredicate isOddOrLessThan11 = isOdd.or(lessThan11);

System.out.println(isOddOrLessThan11.test(10)); // prints "true"
System.out.println(isOddOrLessThan11.test(11)); // prints "true"
System.out.println(isOddOrLessThan11.test(12)); // prints "false"
System.out.println(isOddOrLessThan11.test(13)); // prints "true"

IntPredicate isOddAndLessThan11 = isOdd.and(lessThan11);

System.out.println(isOddAndLessThan11.test(8));  // prints "false"
System.out.println(isOddAndLessThan11.test(9));  // prints "true"
System.out.println(isOddAndLessThan11.test(10)); // prints "false"
System.out.println(isOddAndLessThan11.test(11)); // prints "false"
```

### Composing consumers

- It is possible to combine consumer by using the method `andThen`
- It is used to output a value to different destinations, like a database or a logger

```java
Consumer<String> consumer = System.out::println;
Consumer<String> doubleConsumer = consumer.andThen(System.out::println);
doubleConsumer.accept("Hi!");

// Hi!
// Hi!
```

### Example

``java
import java.security.MessageDigest;
import java.util.Base64;
import java.util.Scanner;
import java.util.function.BiFunction;
import java.util.function.Function;

class ChainOfResponsibilityDemo {

    /**
     * Accepts a request and returns new request with data wrapped in the tag <transaction>...</transaction>
     */
    static RequestHandler wrapInTransactionTag = req ->
            new Request(String.format("<transaction>%s</transaction>", req.getData()));

    /**
     * Accepts a request and returns a new request with calculated digest inside the tag <digest>...</digest>
     */
    static RequestHandler createDigest = req -> {
        String digest = "";
        try {
            final MessageDigest md5 = MessageDigest.getInstance("MD5");
            final byte[] digestBytes = md5.digest(req.getData().getBytes("UTF-8"));
            digest = new String(Base64.getEncoder().encode(digestBytes));
        } catch (Exception ignored) {
            System.out.println("An error occurred");
        }
        return new Request(req.getData() + String.format("<digest>%s</digest>", digest));
    };

    /**
     * Accepts a request and returns a new request with data wrapped in the tag <request>...</request>
     */
    static RequestHandler wrapInRequestTag = req ->
            new Request(String.format("<request>%s</request>", req.getData()));

    /**
     * It should represents a chain of responsibility combined from another handlers.
     * The format: commonRequestHandler = handler1.setSuccessor(handler2.setSuccessor(...))
     * The combining method setSuccessor may has another name
     */
    static RequestHandler commonRequestHandler = req -> wrapInTransactionTag
            .andThen(createDigest)
            .andThen(wrapInRequestTag)
            .handle(req);

    /**
     * It represents a handler and has two methods: one for handling requests and other for combining handlers
     */
    @FunctionalInterface
    interface RequestHandler {

        // !!! write a method handle that accept request and returns new request here
        // it allows to use lambda expressions for creating handlers below
        Request handle(Request r);

        // !!! write a default method for combining this and other handler single one
        // the order of execution may be any but you need to consider it when composing handlers
        // the method may has any name

        default RequestHandler andThen(RequestHandler requestHandler) {
            return req -> requestHandler.handle(this.handle(req));
        }
    }
    /**
     * Immutable class for representing requests.
     * If you need to change the request data then create new request.
     */
    static class Request {
        private final String data;

        public Request(String requestData) {
            this.data = requestData;
        }

        public String getData() {
            return data;
        }
    }

    // Don't change the code below
    public static void main(String[] args) throws Exception {

        final Scanner scanner = new Scanner(System.in);

        final String requestData = scanner.nextLine();

        final Request notCompletedRequest = new Request(requestData);

        System.out.println(commonRequestHandler.handle(notCompletedRequest).getData());
    }
}
``