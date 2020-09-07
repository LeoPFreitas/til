# Logging

- Logs were meant to cover server issues, database issues, networking issues, errors from unanticipated user inputs, states of dynamically created objects, configuration values.

There are several common reasons to generate logs:

- **troubleshooting**
- **auditing**
- **profiling**
- **statistics**

```java
[2019-02-02 01:00:10] [INFO] User 'demo' has registered
[2019-02-02 01:00:20] [INFO] User 'demo' has been logged
[2019-02-02 01:30:05] [INFO] User 'demo' has left the site
[2019-02-02 02:20:00] [ERROR] User 'demo' cannot log in because database is temporarily unavailable
```

### Log levels

**Debug** – debug logs are used to **diagnose applications**. It is used by many people other than developers such as
 sysadmins, testers. Values of variables are logged at the debug level.

**Info** – used to log important information about an application. It is used to log service start, service stop
, configurations, assumptions.

**Warn** – warns are used to indicate a potential problem in the application. However, it does not affect the user at
 this point. Warns are considered the **first level** of application failure. Warns are usually applied to log
  repeated attempts of accessing a resource, missing secondary data, switching from a primary server to a back-up server.

**Error** – this log level is used when there is a more critical problem. This kind of issue usually affects the
 operation result but does not terminate the program. Errors are considered the **second level** of application
  failures.

**Fatal** – it is the third level of application failures. It is used to indicate much more serious error which
 causes the **termination of the program**.