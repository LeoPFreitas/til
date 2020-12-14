# Grouping collectors

## Partitioning

The partitioning operation is presented by the `Collectors.partitioningBy` method that accepts a predicate and splits input elements into a `Map` of two lists:

- Contains elements for which the predicate is true
- Contains elements for which it is false.

The keys of the `Map` has the `Boolean` type.

```java
List<Account> accounts = List.of(
        new Account(3333, "530012"),
        new Account(15000, "771843"),
        new Account(0, "681891")
);

Map<Boolean, List<Account>> accountsByBalance = accounts.stream()
        .collect(Collectors.partitioningBy(account -> account.getBalance() >= 10000));

{
    false=[Account{balance=3333, number='530012'}, Account{balance=0, number='681891'}], 
    true=[Account{balance=15000, number='771843'}]
}
```

The partitioning operation can produce a Map with empty lists, but they will always exist.

## Grouping

Instead of splitting data into two groups based on a predicate, the grouping operation can produce any number of groups based on a classification function that maps elements to some key.

- The grouping operation is presented by the `Collectors.groupingBy` method that accepts a classification function.
- The collector `groupingBy` also produces a `Map`.
- The keys of the `Map` are values produced by applying the classification function to the input elements.
- The corresponding values of the `Map` are lists containing elements mapped by the classification function.

```java
enum Status {
    ACTIVE,
    BLOCKED,
    REMOVED
}

public class Account {
    private long balance;
    private String number;
    private Status status;
    
    // constructors
    // getters and setters
}

List<Account> accounts = List.of(
        new Account(3333L, "530012", Status.REMOVED),
        new Account(15000L, "771843", Status.ACTIVE),
        new Account(0L, "681891", Status.BLOCKED)
)

Map<Status, List<Account>> accountsByStatus = accounts.stream()
        .collect(Collectors.groupingBy(Account::getStatus));

{
    BLOCKED=[Account{balance=0, number='681891'}], 
    REMOVED=[Account{balance=3333, number='530012'}], 
    ACTIVE=[Account{balance=15000, number='771843'}]
}
```

## Downstream collectors

In addition to a predicate or a classification function, `partitioningBy` and `groupingBy` collectors can accept a **downstream** collector.

- Applied to the result of another collector

```java
List<Account> accounts = List.of(
        new Account(3333L, "530012", Status.ACTIVE),
        new Account(15000L, "771843", Status.BLOCKED),
        new Account(15000L, "234465", Status.ACTIVE),
        new Account(8800L, "110011", Status.ACTIVE),
        new Account(45000L, "462181", Status.BLOCKED),
        new Account(0L, "681891", Status.REMOVED)
);

Map<Status, Long> sumByStatuses = accounts.stream()
        .collect(groupingBy(Account::getStatus, summingLong(Account::getBalance)));

{ REMOVED=0, ACTIVE=24133, BLOCKED=60000 }
```