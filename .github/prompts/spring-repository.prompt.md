---
mode: 'agent'
tools: ['codebase']
description: 'Generate a new Spring Data JPA repository'
---

Generate a new Spring Data JPA repository interface.

Ask for the entity name and custom query requirements if not provided.

Requirements for the repository:
* Extend JpaRepository<Entity, ID>
* Use @Repository annotation
* Include custom query methods using Spring Data JPA naming conventions
* Add @Query annotations for complex queries
* Use proper parameter binding (@Param annotation)
* Include pagination and sorting support where appropriate
* Add JavaDoc comments for custom methods

Common custom methods to consider:
* findByField() methods for common searches
* findByFieldContaining() for partial matches
* findByFieldAndOtherField() for multiple criteria
* Custom @Query methods for complex business logic
* Native queries when JPQL is not sufficient

Ensure all custom queries are properly tested and documented.
