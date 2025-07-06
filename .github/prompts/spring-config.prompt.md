---
mode: 'agent'
tools: ['codebase']
description: 'Generate Spring Boot configuration classes'
---

Generate Spring Boot 3 configuration classes.

Ask for the configuration type (Security, Database, Web, etc.) if not provided.

Requirements for configuration classes:
* Use @Configuration annotation
* Use @EnableConfigurationProperties when binding properties
* Use @Bean annotations for bean definitions
* Include proper JavaDoc comments
* Use @ConditionalOnProperty for conditional configuration
* Include @Profile annotations for environment-specific configs
* Use constructor injection for dependencies

Common configuration types:
* Security Configuration - Spring Security setup
* Database Configuration - DataSource and JPA configuration
* Web Configuration - CORS, interceptors, converters
* Application Properties - @ConfigurationProperties classes
* Cache Configuration - Redis, Ehcache setup
* OpenAPI Configuration - Swagger/OpenAPI 3 setup

Configuration best practices:
* Use type-safe configuration properties
* Include default values where appropriate
* Document configuration options clearly
* Use environment-specific profiles
* Include proper exception handling
