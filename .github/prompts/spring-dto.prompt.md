---
mode: 'agent'
tools: ['codebase']
description: 'Generate Spring Boot DTO classes'
---

Generate Data Transfer Object (DTO) classes for Spring Boot 3 REST APIs.

Ask for the entity name and required DTO types if not provided.

Requirements for DTOs:
* Create separate DTOs for requests and responses
* Use validation annotations (@NotNull, @Valid, @Size, etc.)
* Include proper JavaDoc comments
* Use @JsonProperty for JSON field mapping when needed
* Use @JsonIgnore for sensitive fields
* Include builder pattern with @Builder annotation
* Use record classes for simple DTOs when appropriate (Java 17+)

Common DTO types to generate:
* CreateRequestDTO - For POST requests
* UpdateRequestDTO - For PUT/PATCH requests
* ResponseDTO - For GET responses
* ListResponseDTO - For paginated list responses

DTO Guidelines:
* Don't expose internal entity structure
* Include only necessary fields for each operation
* Use appropriate data types and validation rules
* Consider using MapStruct for entity-DTO mapping
* Include proper error messages in validation annotations
