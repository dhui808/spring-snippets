### exchange vs execute vs postForEntity
    execute: The most generalized way to perform a request, with full control over request preparation and response 
        extraction via callback interfaces.
    exchange: much more convenient than execute methods
      Can pass an HttpEntity directly, whereas in execute it needed to be set manually using the RequestCallback.
      Deserialization mechanics are provided out of the box by passing the desired response type Class, instead 
      of using ResponseExtractor callback.
    postForEntity: calls execute themselves under the hood - it's simply a matter of convenience
    
### Timeout
    1. Read timeout: When the request gets read timed out, Spring will throw ResourceAccessException. Underlying exception 
    will be java.net.SocketTimeoutException.
    2. Connect timeout: When the request gets connect timed out, Spring will throw ResourceAccessException. Underlying 
    exception is org.apache.http.conn.HttpHostConnectException
    3. When SSL certificate is expired, Spring will throw ResourceAccessException. Underlying exception is 
    javax.net.ssl.SSLHandshakeException
    
