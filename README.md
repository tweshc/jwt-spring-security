# jwt-spring-security
JWT Generation and Validation using Spring Boot + Spring Security
/**
 * Following tutorial from https://www.javainuse.com/spring/boot-jwt
 *
 * 2 operations are happening in this project:
 * Generating JWT - Expose a POST API with mapping /authenticate. On passing correct username and password it will generate a JSON Web Token(JWT)
 * Validating JWT - If user tries to access GET API with mapping /hello. It will allow access only if request has a valid JSON Web Token(JWT)
 */
