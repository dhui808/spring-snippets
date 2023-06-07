### Security Configuration with defaults
	@Bean
	public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
		http	//Allows restricting access via URL patterns. 
				.authorizeHttpRequests((authorize) -> authorize
						//any request needed to be authenticated
						.anyRequest().authenticated()
				)
				//Configures HTTP Basic authentication with defaults
				.httpBasic(withDefaults())
				// Configure form based authentication with defaults - 
				// generating a login page atthe URL "/login", 
				// redirecting to "/login?error" for authentication failure. 
				.formLogin(withDefaults());
		return http.build();
	}

### 
