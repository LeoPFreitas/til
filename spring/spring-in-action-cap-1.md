# Cap 1

## Spring Security

- Spring Security is used to bake application-level security into application in the "Spring" way (annotations, beans, SpEL...)
- It is a framework that lets the developer build application-level security, but the framework does not secure an application by itself. The developer must understand and configure properly Spring Security.

## Software Security

- The application should ensure that there’s no chance for that information to be accessed, changed, or intercepted. No parties other than the users to whom this data is intended should be able to interact in any way with it.
- Security is a cross-cutting concern that should be design on multiple layers.
- It’s a best practice when addressing the security concerns of one of the layers to assume as much as possible that the above layer doesn't exist.

## Authorization x Authentication

**Authentication →** Identifies the user

**Authorization →** Decide if an identified user is allowed to perform an action

## Common Security Problems

### Session Fixation

- If present, it permits an attacker to impersonate a valid user by reusing a previously generated session ID.
- Exploiting this vulnerability consists of obtaining a valid session ID and making the intended victim’s browser use it.

**Session ID in the URL →** the victim could be tricked into clicking on a malicious link

**Hidden attribute →** the attacker can fool the victim into using a foreign form and post the action to the server

**Session in a cookie →** the attacker can inject a script and force the victim's browser to execute it

### Cross-site scripting (XSS)

- Allows the injection of client-side scripts into web services exposed by the server, thereby permitting other users to run these.

### Cross-site request forgery (CSRF)

- CSRF attacks assume that a URL that calls an action on a specific server can be extracted and reused from outside the application
- Attacker can make a user execute undesired actions on a server by hiding the actions.

### Injections

There are many types of injections attacks. The objective is to harm the system.

Some examples: SQL injection XPath injection, OS command injection, LDAP injection, SMTP header injection, SMTP body injection...