# Date and Time

### LocalDate

- The class `LocalDate` represents a single date in a YYYY-MM-dd format
- The class belongs to the `java.time` package.

```jsx
LocalDate now = LocalDate.now();

LocalDate date1 = LocalDate.of(2017, 11, 25); // 2017-11-25 (25 November 2017)
LocalDate date2 = LocalDate.parse("2017-11-25"); // 2017-11-25 (25 November 2017)
LocalDate.ofYearDay(2017, 33); // 2017-02-02 (2 February 2017)
LocalDate tomorrow = date.plusDays(1);    // 2017-01-02 (2 January 2017)
LocalDate yesterday = date.minusDays(1);  // 2016-12-31 (31 December 2016)
LocalDate inTwoYears = date.plusYears(2); // 2019-01-01 (1 January 2019)
LocalDate in2016 = date.withYear(2016);   // 2016-01-01 (1 January 2016)
```

### LocalTime

- Immutable
- TheLocalTime class represents daytime in hours-minutes-seconds format, such as 06:30 or 11:45:30.

```jsx
LocalTime now = LocalTime.now();

LocalTime.of(11, 45);        // 11:45
LocalTime.of(11, 45, 30);    // 11:45:30
LocalTime.parse("11:45:30"); // 11:45:30 (hours, minutes, seconds)
LocalTime time = LocalTime.ofSecondOfDay(12345); // 03:25:45
LocalTime nanotime = LocalTime.ofNanoOfDay(1234567890); // 00:00:01.234567890

// constants
LocalTime.MIN; // 00:00
LocalTime.MAX; // 23:59:59.999999999
LocalTime.NOON; // 12:00
LocalTime.MIDNIGHT; // 00:00

// getters
time.getHour();   // 11
time.getMinute(); // 45
time.getSecond(); // 30
time.getNano();   // 0, nanoseconds
```

### LocalDateTime

- The class `LocalDateTime` is a combination of `LocalDate` and `LocalTime` that keeps such values as `2017-12-03T22:30`
- It still doesn't store information on a time-zone.

```jsx
LocalDate date = LocalDate.of(2017, 11, 25); // 2017-11-25
LocalTime time = LocalTime.of(21, 30); // 21:30       

LocalDateTime dateTime1 = date.atTime(time); // 2017-11-25T21:30
LocalDateTime dateTime2 = time.atDate(date); // 2017-11-25T21:30
```

### Comparing dates and time

- The classes `LocalDate`, `LocalTime`, `LocalDateTime` have methods for comparing their instances according to their position on the timeline.
- The methods compare instances as they go in chronological order (or the order of time).

```jsx
// LocalDate
LocalDate date1 = LocalDate.parse("2017-01-02");
LocalDate date2 = LocalDate.parse("2017-12-12");

date1.compareTo(date1); // 0, date1 and date1 are equal
date1.compareTo(date2); // -11, negative value => date1 is less than date2
date2.compareTo(date1); // 11, positive value => date2 is greater than date1

// LocalTime
LocalTime time1 = LocalTime.parse("15:30:10");
LocalTime time2 = LocalTime.parse("17:50:30");

time1.compareTo(time1); // 0, time1 and time1 are equal
time1.compareTo(time2); // -1, time1 is less than time2
time2.compareTo(time1); // 1, time2 is greater than time1

// LocalDateTime
LocalDateTime dateTime1 = LocalDateTime.parse("2017-01-01T20:30"); // 1 January 2017, 20:30
LocalDateTime dateTime2 = LocalDateTime.parse("2017-01-02T23:00"); // 2 January 2017, 23:00

dateTime1.compareTo(dateTime1); // 0, dateTime1 and dateTime are equal
dateTime1.compareTo(dateTime2); // -1, dateTime1 is less than dateTime2
dateTime2.compareTo(dateTime1); // 1, dateTime2 is greater than dateTime1
```

The classes have also some concise methods to compare dates and time on a timeline that return `boolean` value.

- The method `isAfter` returns `true`, only if this instance is strictly after another instance passed as the argument
, otherwise, the method returns `false`.
- The method `isBefore` returns `true`, only if this instance is strictly before an instance passed as the argument
, otherwise, the method returns `false`.
- The method `isEqual` returns `true`, if instances are equal, otherwise, the method returns `false`.

```jsx
LocalDate date1 = LocalDate.of(2017, 11, 30);
LocalDate date2 = LocalDate.of(2017, 12, 1);

date1.isEqual(date1); // true
date1.isEqual(date2); // false

date1.isBefore(date2); // true
date1.isBefore(date1); // false
date2.isBefore(date1); // false

date2.isAfter(date1); // true
date2.isAfter(date2); // false
date1.isAfter(date2); // false

LocalDateTime dateTime1 = LocalDateTime.parse("2017-12-01T21:30"); // 1 December 2017, 21:30
LocalDateTime dateTime2 = LocalDateTime.parse("2017-12-02T21:30"); // 2 December 2017, 21:30

dateTime1.isEqual(dateTime2); // false
dateTime2.isEqual(dateTime2); // true

dateTime1.isBefore(dateTime2); // true
dateTime1.isAfter(dateTime2); // false
dateTime2.isAfter(dateTime1); // true
```