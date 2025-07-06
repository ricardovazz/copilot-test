---
mode: 'agent'
tools: ['codebase']
description: 'Generate a new JPA entity class'
---

Generate a new JPA entity class for Spring Boot 3.

Ask for the entity name, fields, and relationships if not provided.

Requirements for the entity:
* Use @Entity annotation
* Use @Table annotation with proper naming
* Use @Id and @GeneratedValue for primary key
* Include proper JPA annotations (@Column, @JoinColumn, etc.)
* Use validation annotations (@NotNull, @Size, @Email, etc.)
* Include proper relationship annotations (@OneToMany, @ManyToOne, etc.)
* Use @CreationTimestamp and @UpdateTimestamp for audit fields
* Include proper equals(), hashCode(), and toString() methods
* Use @Builder annotation from Lombok
* Add JavaDoc comments for the class and important fields

Standard fields to include:
* id (Long) - Primary key
* createdAt (LocalDateTime) - Creation timestamp
* updatedAt (LocalDateTime) - Update timestamp

Follow JPA best practices:
* Use appropriate fetch types
* Consider cascade operations carefully
* Use proper column definitions
* Include database constraints in annotations
