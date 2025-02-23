2025-02-23 18:16

Tags: [[Spring Framework]]

---
- Using `@RestControllerAd`
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

        return new ResponseEntity<ExceptionResponse>(error, headers, HttpStatus.UNAUTHORIZED);

    }
}
```
- Define exeption class(es)
```java
public class LogisticMgmtUnauthorizedException extends LogisticMgmtException {


    @Serial
    private static final long serialVersionUID = 1L;

    public LogisticMgmtUnauthorizedException(int code,

                                        String message) {
        super(code, message);

    }


    public LogisticMgmtUnauthorizedException(int code,

                                        String message,

                                        Throwable cause) {

        super(code, message, cause);

  

    }

  

    /**

     * Instantiates a new Tug mgmt unauthorized exception.

     *

     * @param code  the code

     * @param cause the cause

     */

    public LogisticMgmtUnauthorizedException(int code,

                                        Throwable cause) {

        super(code, cause);

  

    }

  

    /**

     * Instantiates a new Tug mgmt unauthorized exception.

     *

     * @param message the message

     */

    public LogisticMgmtUnauthorizedException(String message) {

        super(message);

  

    }

  

    /**

     * Instantiates a new Tug mgmt unauthorized exception.

     *

     * @param cause the cause

     */

    public LogisticMgmtUnauthorizedException(Throwable cause) {

        super(cause);

  

    }

  

    /**

     * Instantiates a new Tug mgmt unauthorized exception.

     *

     * @param errorCode the error code

     */

    public LogisticMgmtUnauthorizedException(int errorCode) {

        super(errorCode);

    }

  
  

}
```
---
# References