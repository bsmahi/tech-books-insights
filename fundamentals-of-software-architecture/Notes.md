## Title: Fundamentals of Software Architecture
## Authors: Mark Richards & Neal Ford

> [!IMPORTANT]
> Architecture is about the important stuff... whatever that is - Ralph Johnson

- A decade ago, software architects dealt only with the purely technical aspects of architecture, like modularity, components, and patterns.
- Since then, because of new architectural styles that leverage a wider swath of capabilities (like microservices), the role of software architect has expanded.

> Defintion: "_Software Architecture is about making fundamental structural choices which are costly to change once implemented._"
> Yet architects designed modern architectural styles like microservices with the idea of incremental built in -- it is no longer expensive to make structural changes in microservices.

Other means of Software Architecture
 - Software Architecture as the _blueprint_ of the system.
 - The _roadmap_ for developing a system

Software Architecture consists of the _structure_ of the system, combined with 
  - Architecture Characteristics ("_ilities")
  - The system must support
  - Architecture Decisions
  - Architecture Design Principles

> [!Note]
> _Architecture = architecture characteristics + decisions + design principles_

- The structure of the system refers to the type of architectural style the system is implemented in (such as microservices, layered, or microkernel)
- The architectural characteristics define the success criteria of a system, which is generally orthogonal to the functionality of the system.

### Architectural Characteristics 

Architectural Characteristics refers to the _"-ilities"_ that the system must support

1. Availability
2. Scalability
3. Fault Tolerance
4. Performance
5. Reliability
6. Securitt
7. Elasticity
8. Deployability
9. Testability
10. Agility
11. Recoverability
12. Learnability

---

## What is Architecture Decision?

**Architecture Decisions**: _Architecture Decisions_ define the rules for how a system should be constructed. Architecture decisions form the constraints of the system and direct the development teams on what is and what isn't allowed. In a nutshell, _architecture decisions are rules for constructing systems_.

For example, _an architect might make an architecture decision that only the business and services layers within a layered architecture can access the databasse, restricting the presentation layer from making direct database calls_.

## What is Variance?

If a particular architecture decision cannot be implemented in one part of the system due to some condition or other constraint, that decision (or rule) can be broken through something called a _variance_

## What is Design Principles?

A design principle is a _guideline_ rather than a hard-and-fast rule and differs from an architecture decision.

For example, _development teams ought to utilize asynchronous messaging among services in a microservices architecture to enhance performance. Since an architectural decision cannot encompass every possible condition and option for inter-service communication, a design principle can serve as guidance for the preferred method—in this instance, asynchronous messaging. This approach enables developers to select a more suitable communication protocol, such as REST or gRPC, based on the specific circumstances they encounter._

## What are Expections of an Architect?
- Make architecture decisions
- Continually analyze the architecture
- Keep current with latest trends
- Ensure compliance with decisions
- Diverse exposure and experience
- Have business domain knowledge
- Possess interpersonal skills
- Understand and navigate politics
