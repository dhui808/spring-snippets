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
