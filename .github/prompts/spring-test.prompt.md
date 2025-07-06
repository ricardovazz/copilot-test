---
mode: 'agent'
tools: ['codebase']
description: 'Generate Spring Boot test classes'
---

Generate comprehensive test classes for Spring Boot 3 application.

Ask for the component type to test (Controller, Service, Repository) if not provided.

Requirements for test classes:
* Use JUnit 5 annotations (@Test, @BeforeEach, @AfterEach)
* Use appropriate Spring Boot test annotations
* Use MockMvc for controller tests
* Use @MockBean for mocking dependencies
* Include proper test data setup
* Test both positive and negative scenarios
* Use AssertJ assertions for better readability
* Include integration tests with @SpringBootTest
* Use TestContainers for database integration tests

Test types to generate:
* Unit Tests - @ExtendWith(MockitoExtension.class)
* Web Layer Tests - @WebMvcTest
* Service Layer Tests - @SpringBootTest
* Repository Tests - @DataJpaTest
* Integration Tests - @SpringBootTest with TestContainers

Testing best practices:
* Follow AAA pattern (Arrange, Act, Assert)
* Use meaningful test method names
* Test edge cases and error conditions
* Use @DirtiesContext when needed
* Include proper cleanup in @AfterEach
* Use @Sql for test data setup when appropriate
