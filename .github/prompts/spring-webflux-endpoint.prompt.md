---
mode: 'agent'
tools: ['codebase', 'terminal']
description: 'Generate a Spring WebFlux endpoint with best practices'
---

# Spring WebFlux Endpoint Generator

## Context

You are working in a Java project that uses Spring Boot 3.x and want to add a new reactive REST API endpoint using Spring WebFlux. The endpoint should follow modern Spring Boot conventions, use Project Reactor types (`Mono`, `Flux`), and demonstrate best practices for non-blocking, reactive programming.

## Goal

Generate a complete, production-ready Spring WebFlux endpoint that handles HTTP requests reactively, including input validation, error handling, and proper response types.

## Requirements

- Use Spring Boot 3.x and Java 17+ features
- Use `@RestController` and WebFlux annotations
- Use `Mono` or `Flux` for return types
- Use constructor injection for dependencies
- Validate request bodies with `@Valid` and validation annotations
- Include logging using `LoggerFactory.getLogger()`
- Handle errors reactively and return appropriate HTTP status codes
- Provide JavaDoc for public classes and methods
- Use camelCase for variables/methods, PascalCase for classes, UPPER_SNAKE_CASE for constants
- Include an example request/response

## Instructions

1. Create a new class `${input:ControllerClassName:SampleWebFluxController}` in the appropriate package (e.g., `com.example.controller`).
2. Annotate the class with `@RestController` and add a request mapping (e.g., `/api/items`).
3. Define a method to handle a specific HTTP verb (e.g., `@PostMapping` for creating an item).
4. Use a DTO class for the request body, annotated with validation constraints.
5. Inject any required services via constructor injection.
6. Use `Mono` or `Flux` as the return type.
7. Add logging at the start and end of the method.
8. Handle validation and business errors reactively, returning meaningful HTTP status codes.
9. Add JavaDoc to the class and method.
10. Provide an example request and expected response.

## Examples

**Input**:

Create a POST endpoint `/api/items` that accepts a JSON body with `name` (not null, min 3 chars) and `quantity` (positive integer), and returns the created item.

**Expected Output**:

```java
package com.example.controller;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.http.ResponseEntity;
import org.springframework.validation.annotation.Validated;
import org.springframework.web.bind.annotation.*;
import reactor.core.publisher.Mono;
import javax.validation.Valid;
import javax.validation.constraints.Min;
import javax.validation.constraints.NotNull;

/**
 * REST controller for managing items reactively.
 */
@RestController
@RequestMapping("/api/items")
@Validated
public class ItemController {

    private static final Logger LOGGER = LoggerFactory.getLogger(ItemController.class);

    private final ItemService itemService;

    public ItemController(ItemService itemService) {
        this.itemService = itemService;
    }

    /**
     * Create a new item.
     *
     * @param request the item to create
     * @return the created item
     */
    @PostMapping
    public Mono<ResponseEntity<ItemResponse>> createItem(
            @Valid @RequestBody ItemRequest request) {
        LOGGER.info("Received request to create item: {}", request);
        return itemService.createItem(request)
                .map(item -> {
                    LOGGER.info("Item created: {}", item);
                    return ResponseEntity.ok(item);
                })
                .onErrorResume(e -> {
                    LOGGER.error("Error creating item", e);
                    return Mono.just(ResponseEntity.badRequest().build());
                });
    }
}

class ItemRequest {
    @NotNull(message = "Name must not be null")
    @javax.validation.constraints.Size(min = 3, message = "Name must be at least 3 characters")
    public String name;

    @Min(value = 1, message = "Quantity must be positive")
    public int quantity;
}

class ItemResponse {
    public String name;
    public int quantity;
}
```

**Example Request**:

```json
POST /api/items
{
  "name": "Widget",
  "quantity": 5
}
```

**Example Response**:

```json
{
  "name": "Widget",
  "quantity": 5
}
```

## Validation

- [ ] The endpoint uses `@RestController` and WebFlux types (`Mono`/`Flux`)
- [ ] Input is validated with `@Valid` and constraint annotations
- [ ] Logging is present using `LoggerFactory.getLogger()`
- [ ] Errors are handled reactively with appropriate HTTP status codes
- [ ] JavaDoc is included for public classes and methods
- [ ] Example request/response is provided

## References

- [Spring WebFlux Documentation](https://docs.spring.io/spring-framework/docs/current/reference/html/web-reactive.html)
- [Project Reactor](https://projectreactor.io/)
- #file:src/main/java/com/example/controller