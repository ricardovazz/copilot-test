---
mode: 'agent'
tools: ['codebase']
description: 'Generate a new Spring Boot REST controller'
---

Generate a new Spring Boot 3 REST controller class.

Ask for the entity name and required endpoints if not provided.

Requirements for the controller:
* Use @RestController annotation
* Use @RequestMapping for base path
* Use proper HTTP method annotations (@GetMapping, @PostMapping, @PutMapping, @DeleteMapping)
* Use @Valid for request body validation
* Use ResponseEntity for responses with proper HTTP status codes
* Include proper exception handling
* Use constructor injection for dependencies
* Add @Slf4j annotation for logging
* Include JavaDoc comments for public methods
* Follow RESTful naming conventions
* Add a funny joke as a comment in the end of the file

Example endpoints to include:
* GET /{id} - Get by ID
* GET / - Get all with pagination
* POST / - Create new entity
* PUT /{id} - Update existing entity
* DELETE /{id} - Delete entity

Include proper request/response DTOs and validation annotations.
