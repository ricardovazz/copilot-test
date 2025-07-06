# Spring Boot 3 Project Custom Instructions

## Technology Stack Preferences
- We use Spring Boot 3.x with Java 17+ features
- We use Maven for dependency management, not Gradle
- We follow Spring Boot conventions and best practices
- We use Spring Data JPA for database operations
- We use Spring Security for authentication and authorization

## Code Style and Conventions
- Always use @Override annotations when implementing interface methods or overriding methods
- Use LoggerFactory.getLogger() for logger initialization in all classes
- Follow camelCase naming conventions for variables and methods
- Use PascalCase for class names
- Use UPPER_SNAKE_CASE for constants

## Spring Boot Specific Guidelines
- Use @RestController for REST API endpoints, not @Controller + @ResponseBody
- Use @Service for business logic classes
- Use @Repository for data access classes
- Use @Component for general Spring-managed beans
- Always use constructor injection over field injection
- Use @ConfigurationProperties for configuration binding
- Use @Transactional on service methods that modify data

## Testing Preferences
- Use JUnit 5 for unit tests
- Use @SpringBootTest for integration tests
- Use @WebMvcTest for controller tests
- Use @DataJpaTest for repository tests
- Use MockMvc for testing REST endpoints
- Use TestContainers for integration tests with databases

## Documentation and Comments
- Include JavaDoc comments for public classes and methods
- Add meaningful method and variable names that are self-documenting
- Include validation annotations (@NotNull, @Valid, etc.) with clear messages

## Error Handling
- Use @ControllerAdvice for global exception handling
- Create custom exceptions that extend RuntimeException
- Always include proper HTTP status codes in REST responses
- Use ResponseEntity for REST controller methods when appropriate

## Security Guidelines
- Always validate user inputs
- Use Spring Security annotations (@PreAuthorize, @Secured)
- Hash passwords using BCryptPasswordEncoder
- Implement proper CORS configuration when needed
