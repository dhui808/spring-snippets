### HttpRequestHandler
	In spring-web, HttpRequestHandlerServlet.java:
		target = wac.getBean(getServletName(), HttpRequestHandler.class);
	This allows multiple instances of HttpRequestHandler - multi-behavior interface
	
	In spring-webmvc, AbstractHandlerMapping.PreFlightHandler, not a managed bean
	HttpRequestHandlerAdapter:
		((HttpRequestHandler) handler).handleRequest(request, response);
	DefaultServletHttpRequestHandler: serving static files using the Servlet container's "default" Servlet.
	ResourceHttpRequestHandler: serves static resources
	
	In spring-websocket
	WebSocketHttpRequestHandler: processing WebSocket handshake requests.
	SockJsHttpRequestHandler
	
