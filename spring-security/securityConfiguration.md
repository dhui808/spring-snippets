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

### No Spring Bean of type SecurityFilterChain 
	Same effects as above.

### Certian URLs od not need authentication. User need to have certain roles to access some URLs
	@Bean
	public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
		
	    final String[] ENDPOINTS_WHITELIST = {
	            "/css/**",
	            "/",
	            "/login"
	    };
	    
		http	
		//Allows restricting access via URL patterns. 
        	.authorizeHttpRequests(authorize -> authorize
        	// Whitelist urls does not need to be authenticated
                .requestMatchers(ENDPOINTS_WHITELIST).permitAll()
                // /message the user must be in role ADMIN 
                .requestMatchers("/message").hasRole("ADMIN")
                // everything else must be authenticated
                .anyRequest().authenticated()
                // But /logout does not need to be authenticated
                )
				.httpBasic(withDefaults())
				.formLogin(withDefaults());
		return http.build();
	}
	
