    @Configuration
    @EnableWebSecurity
    public class SecurityConfig extends KeycloakWebSecurityConfigurerAdapter {

        @Autowired
        public void configureGlobal(AuthenticationManagerBuilder auth) throws Exception {
            KeycloakAuthenticationProvider keycloakAuthenticationProvider = keycloakAuthenticationProvider();
            keycloakAuthenticationProvider.setGrantedAuthoritiesMapper(new SimpleAuthorityMapper());
            auth.authenticationProvider(keycloakAuthenticationProvider);
        }

        @Bean
        public KeycloakConfigResolver KeycloakConfigResolver() {
            return new KeycloakSpringBootConfigResolver();
        }

        @Bean
        @Override
        protected SessionAuthenticationStrategy sessionAuthenticationStrategy() {
            return new RegisterSessionAuthenticationStrategy(new SessionRegistryImpl());
        }

        @Override
        protected void configure(HttpSecurity http) throws Exception {
            super.configure(http);
            http
                .authorizeRequests()
                .antMatchers("/api/**").authenticated()
                .anyRequest().permitAll();
        }
    }

    The SecurityConfig class extends KeycloakWebSecurityConfigurerAdapter to enable Keycloak for authentication. 
    The configureGlobal method configures Keycloak as the authentication provider and maps the Keycloak roles to Spring Security authorities.

    The KeycloakConfigResolver bean is used to resolve the Keycloak configuration. The sessionAuthenticationStrategy bean 
    is used to register the Keycloak authentication session.

    Finally, the configure method is used to configure the HTTP security for the application. It restricts access to the 
    /api/** endpoint to authenticated users, while allowing access to all other endpoints without authentication.

    You will also need to configure Keycloak by setting up a realm and creating a client for your application.

    pom.xml
    <dependency>
        <groupId>org.keycloak</groupId>
        <artifactId>keycloak-spring-boot-starter</artifactId>
        <version>7.0.1</version>
    </dependency>
    <dependency>
        <groupId>org.springframework.security</groupId>
        <artifactId>spring-security-web</artifactId>
        <version>5.4.0</version>
    </dependency>
    <dependency>
        <groupId>org.springframework.security</groupId>
        <artifactId>spring-security-config</artifactId>
        <version>5.4.0</version>
    </dependency>

    @Configuration
    public class KeycloakConfig {

        @Bean
        public KeycloakSpringBootConfigResolver keycloakConfigResolver() {
            return new KeycloakSpringBootConfigResolver();
        }

        @Bean
        @Scope(ConfigurableBeanFactory.SCOPE_PROTOTYPE)
        public KeycloakClientRequestFactory keycloakClientRequestFactory(
                KeycloakRestTemplate keycloakRestTemplate) {
            return new KeycloakClientRequestFactory(keycloakRestTemplate);
        }

        @Bean
        public KeycloakRestTemplate keycloakRestTemplate(
                KeycloakClientRequestFactory keycloakClientRequestFactory) {
            return new KeycloakRestTemplate(keycloakClientRequestFactory);
        }
    }

    application.yml
    keycloak:
      realm: your-realm-name
      auth-server-url: http://keycloak-server:8080/auth
      resource: your-client-id
      public-client: true
      principal-attribute: preferred_username

    security:
      oauth2:
        client:
          provider:
            keycloak:
              issuer-uri: http://keycloak-server:8080/auth/realms/your-realm-name


    The Keycloak configuration properties specify the following information:

    realm: The name of the Keycloak realm that your application belongs to.  
    auth-server-url: The URL of the Keycloak authorization server.  
    resource: The client ID of your application that is registered in the Keycloak realm.  
    public-client: A flag that indicates whether your application is a public client or not.
    principal-attribute: The name of the attribute that contains the user's preferred username.
    The Spring Security OAuth2 client configuration properties specify the following information:

    provider: The OAuth2 provider that the client should use. In this case, the provider is Keycloak.
    issuer-uri: The URL of the Keycloak realm's issuer.
