
# Green Summer
Green Summer is a set of different utilities that can be added on top of Spring to augment the basic functionality.
It started as a set of controllers and configuration that I felt temped to copy/paste into each of my projects. So I decided to create a shared library instead. Some of the functionality might be developed in the future in Spring (Boot) itself, and then I'll be more than happy to deprecate it and move along.
In the mean time, this is a brief summary of the utilities that one can find in Green Summer

 - **Log4JController**: A controller to list/modify the Log4j log levels configuration at runtime.
 - **HealthController**: A simple controller with an actionable toggle that can be used from balancers or health checks to control whether the application should be used or not.
 - **Slf4jMDCFilter**:  A servlet filter that adds a unique ID to all the log messages that belong to each request. This way you can track all the log messages for a given request, even if the intermix with messages from other requests.
 - **ProfilingAspect**: An aspect that can be easily used to profile method calls. With the appropriate AOP configuration, it can be used to profile also private methods and/or methods belonging to classes outside Spring.
 - **CustomXMLHttpMessageConverter**: A message converter that overrides Jaxb2RootElementHttpMessageConverter and uses a pool of Marshallers to convert your objetcs to XML, instead of the "a new marshaller per request" approach that the regular Jaxb2RootElementHttpMessageConverter uses. The performance difference in applications with heavy traffic is quite noticeable.
 - **LoggingClientHttpRequestInterceptor**: An interceptor to log the traffic back & forth when using a RestTemplate. INFO shows basic info, DEBUG includes headers and TRACE includes request and response bodies. Useful for debugging RestTemplate calls at runtime with the help of Log4JController.
 - **CacheConfiguration**: A configuration class for the Caffeine cache so you can initialised multiple caches using configuration properties easily. 
 - **SummerXSLTView**: An XSLTView that allows you to specify a result object and an XSLT. The result object is marshalled first to XML, using JAXB, and then the XSLT stylesheet is used to transform the XML to the final result. Useful to get different XML/HTML views without having to create extra Java classes.
 - **SummerJoltView**: A view that allows you to specify a result object and a Jolt specification. The result object is marshalled first to JSON, using Jackson, and then the Jolt spec is used to transform the JSON to the final JSON. Useful to get different JSON views without having to create extra Java classes.
 - **ObjectJoiner**: Just a simple convenient utility to create strings from a number of objects, specified as varargs or collection, optionally using a separator. 

The Spring integrated utilites can be enabled using the annotation @EnableSummer and specifying the appropriate parameters.

I'll be adding documentation as time permits.