---
mode: 'agent'
tools: ['codebase']
description: 'Generate a new Spring Boot service class'
---

Generate a new Spring Boot 3 service class for business logic.

Ask for the entity name and required operations if not provided.

Requirements for the service:
* Use @Service annotation
* Use constructor injection for dependencies
* Add @Slf4j annotation for logging
* Use @Transactional annotation on methods that modify data
* Include proper exception handling with custom exceptions
* Add JavaDoc comments for public methods
* Include validation logic
* Use Optional for methods that might not find results
* Log important operations at appropriate levels (debug, info, error)

Common operations to include:
* findById() - Find entity by ID
* findAll() - Find all entities with pagination
* save() - Save new entity
* update() - Update existing entity
* delete() - Delete entity
* Custom business logic methods as needed

Include proper error handling and logging for each operation.
