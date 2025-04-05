2025-02-23 18:16

Tags: [[Spring Framework]] [[Exception Handling]] [[REST API]]

---

- Using `@RestControllerAdvice`

```java
@RestControllerAdvice
public class WebControllerAdvice {
    private static final String ERROR_CAUGHT_IN_ADVICE = "Error caught in advice-";
    private static final int _9999 = 9999;
    private static final Logger log = LoggerFactory.getLogger(WebControllerAdvice.class);

    @ExceptionHandler(LogisticMgmtUnauthorizedException.class)
    @ResponseStatus(value = HttpStatus.UNAUTHORIZED)
    public ResponseEntity<ExceptionResponse> handleUnAuthorizedException(
            final LogisticMgmtUnauthorizedException exception,
            final HttpServletRequest request) {

        ExceptionResponse error = new ExceptionResponse();
        log.error(ERROR_CAUGHT_IN_ADVICE, exception);
        error.setErrorCode(exception.getCode());
        error.callerURL(request.getRequestURI());
        error.setErrorMessage(exception.getMessage());
        HttpHeaders headers = new HttpHeaders();
        headers.setContentType(MediaType.APPLICATION_JSON);
        return new ResponseEntity<>(error, headers, HttpStatus.UNAUTHORIZED);
    }
}
```

- Define exception class(es)

```java
public class LogisticMgmtUnauthorizedException extends LogisticMgmtException {
    @Serial
    private static final long serialVersionUID = 1L;

    public LogisticMgmtUnauthorizedException(int code, String message) {
        super(code, message);
    }

    public LogisticMgmtUnauthorizedException(int code, String message, Throwable cause) {
        super(code, message, cause);
    }
}

public class LogisticMgmtException extends Exception {
    private static final long serialVersionUID = 1L;
    private int code;
    protected String[] resources;

    public LogisticMgmtException(int code, String message) {
        super(message);
        this.code = code;
    }
}
```

- Define response class

```java
public class ResponseEntity<T> extends HttpEntity<T> {
    private final Object status;

    public ResponseEntity(HttpStatus status) {
        this(null, null, status);
    }

    public ResponseEntity(@Nullable T body, HttpStatus status) {
        this(body, null, status);
    }
}
---
# References
```
