# copilot-test


MCP - far easier to build Gen AI applications, through providing a consistent interface to tools for LLMs to call.

A2A - aims at a h.igher level of integration, seeking to standardize agent discovery and collaboration. A2A has yet to prove itself in practice

Tools

Embabel - Agent Framework - Declarative like Kubernetes, uses Spring AI in the background

Embabel Coding Agent -  implementation of that framework designed specifically for software development tasks





https://medium.com/@springrod/embabel-a-new-agent-platform-for-the-jvm-1c83402e0014

https://medium.com/@springrod/the-embabel-vision-967654f13793

Higher level orchestration technology is needed:

Explainability: Why were choices made in solving a problem?
Discoverability: MCP skirts this important problem. How do we find the right tools at each point, and ensure that models aren’t confused in choosing between them?
Ability to mix models, so that we are not reliant on God models but can use local, cheaper, private models for many tasks
Ability to inject guardrails at any point in a flow
Ability to manage flow execution and introduce greater resilience
Composability of flows at scale. We’ll soon be seeing not just agents running on one system, but federations of agents.
Safer integration with sensitive existing systems such as databases, where it is dangerous to allow even the best LLM write access.~

Why the JVM?

    For normal ML, we have a bunch of python libraries. TF, PyTorch, etc.
    
    With Gen AI we are not doing comparable low level work. We’re contacting multiple LLMs via simple HTTP calls.

    The critical adjacency for building business apps with LLMs is existing business logic and infrastructure. And the critical skill set is building sophisticated business applications. In both these areas, the JVM is far ahead of Python and likely to remain so.

    Much of the critical business logic in the world is running on the JVM


Embabel:
    -Embabel introduces a planning step (plan towards goal after input, GOAP (Goal-Oriented Action Planning - planner looks for actions until desired state is satisfied))

    -Embabel encourages building a rich domain model (Java records)

    building agents with Embabel to be as natural as building a Spring MVC REST interface

Key objectives:

To bring the disruptive power of deterministic planning: The ability to extend system capabilities without modifying existing code.

To leverage the power of domain modeling to maximize reuse, explainability, auditability, and fidelity to business requirements.

To enable deep, frictionless integration with existing business applications.

To enable the use of software engineering best practices to build Gen AI applications. Proven practices remain essential. No one is going to vibe code their way to unlocking the potential of Gen AI in critical systems.

To embrace emerging standards such as MCP and A2A to help build the agentic web, so developers can focus on business logic.

To explore the potential to create agents in natural language. While the skills of enterprise developers create the foundation, it’s now possible to empower business users.

To offer inspirational examples that are useful in their own right and demonstrate the power of a good agent platform. Watch this space!

To demonstrate the value of a consistent approach that, as with Spring, is bigger than the sum of its parts.


Power of planning:

    - No planning,  require developers to specify how actions are chained together, state machines, or rely on LLMs for planning

    - System autonomy to determine the best way to perform tasks
    
    - Deterministic, safe and explainable

    - While predictable, it remains intelligent, as the system can chain existing actions together in ways that were not explicitly programmed, and grow in power as more actions and goals are added


Best of both worlds: 
    Embabel servers can solve problems in ways that weren’t explicitly programmed, while only using steps that were designed into the system.


Domain Modeling:

    Conditions used in planning are expressed in terms of the data flow of domain objects. As per good OO practice, domain objects can have behavior as well as state, and Embabel even provides the ability to selectively expose safe functions to LLMs as tools.


MCP has had a transformational impact in connecting LLMs to the outside world. Tying into existing systems is even more important.

By building on Spring, which runs a huge proportion of the world’s critical applications, and following Spring patterns, it offers frictionless integration into enormous business value.

Toward The PaaS for Natural Language:

We’re seeing two major vectors in agent platforms: Code-centric approaches like Crew AI, Google ADK and LangGraph, and graphical approaches like HyperMode, Sema4.ai and many others.

- Embabel comes from the code-centric direction, but its strong concepts can underpin higher level functionality and greater use of natural language.

- Embabel is ideally placed to push the use of natural language to define agents, given its ability to balance autonomy and control and its emphasis on a domain model that can provide a lingua franca.


**Spring AI**:

```java
// Manual prompt construction
String prompt = String.format("Analyze sentiment: %s", content);
ChatResponse response = chatClient.prompt(prompt).call();
// Manual parsing with potential runtime errors
SentimentAnalysis result = parseSentiment(response.getResult().getOutput().getContent());
```

**Embabel**:

```kotlin
// Declarative, type-safe interaction
@Action(description = "Analyze sentiment of content")
fun analyzeSentiment(@Parameter("Content to analyze") content: String): SentimentAnalysis
```


### **3. Testing Approach**

**Spring AI Testing**:

```java
@Test
void testNewsAnalysis() {
    // Mock ChatClient responses
    when(chatClient.prompt(any())).thenReturn(mockResponse);
    
    // Test entire orchestration manually
    NewsSummary result = newsAnalyzer.analyzeNews("AI");
    
    // Verify each step manually
    assertThat(result.getArticles()).hasSize(5);
    assertThat(result.getSentiments()).hasSize(5);
}
```

**Embabel Testing**:

```kotlin
@Test
fun testNewsAnalysis() {
    // Test individual actions in isolation
    val articles = agent.searchNews("AI")
    val sentiment = agent.analyzeSentiment(articles[0])
    
    // Test goal achievement
    val analysis = agent.analyzeNews("AI")
    
    // Framework handles orchestration testing
    assertThat(analysis.topic).isEqualTo("AI")
}
```


## **Summary**

The **Spring AI approach** gives you **full control** but requires **manual orchestration** of complex workflows. You're working at the "Servlet API level" - handling requests, responses, and flow control manually.

The **Embabel approach** provides **declarative agent definitions** where the framework handles the complex orchestration automatically. You're working at the "Spring MVC level" - focusing on **what** you want to achieve rather than **how** to orchestrate it.

**Spring AI** is excellent for simple integrations, while **Embabel** shines for complex, multi-step agentic workflows where intelligent planning and type safety are crucial.

