### Integration Testing with  @SpringBootTest
    Using @SpringBootTest(webEnvironment = WebEnvironment.MOCK) loads a web application context and provides a mock web environment. 
    It mocks the entire web server behavior.

    Using @SpringBootTest(webEnvironment = WebEnvironment.RANDOM_PORT) loads a real http server. This approach is closer to test 
    the real application.
