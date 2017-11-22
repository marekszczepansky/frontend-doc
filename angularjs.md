# AngularJS

### decorator
```javascript
    function handleExceptionDelegate($delegate) {
      function exceptionHandler(exception, cause) {
        3rdPartyLogger.fatalException(cause, exception);
        $delegate(exception, cause);
      }
      return exceptionHandler;
    }

    $provide.decorator('$exceptionHandler', handleExceptionDelegate);
```
