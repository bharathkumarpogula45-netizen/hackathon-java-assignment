# Questions

Here are 2 questions related to the codebase. There's no right or wrong answer - we want to understand your reasoning.

## Question 1: API Specification Approaches

When it comes to API spec and endpoints handlers, we have an Open API yaml file for the `Warehouse` API from which we generate code, but for the other endpoints - `Product` and `Store` - we just coded everything directly. 

What are your thoughts on the pros and cons of each approach? Which would you choose and why?

**Answer:**
```txt
Using an OpenAPI YAML file to generate code has the advantage of consistency and automation. It ensures that the API contract is clearly defined up front, and both client and server code can be generated from the same specification. This reduces human error, makes documentation easier, and helps align multiple teams around a single source of truth.

On the other hand, hand coding endpoints (like Product and Store) gives developers more flexibility and speed, especially for simple CRUD operations. It avoids the overhead of maintaining a spec file and generator, but it can lead to inconsistencies if different developers implement endpoints differently.

If the project is expected to grow, or if multiple teams/clients consume the APIs, I would choose the OpenAPI driven approach because it enforces standards and makes integration smoother. For small, internal, or prototype features, direct coding is fine since it’s faster and less ceremony.


```

---

## Question 2: Testing Strategy

Given the need to balance thorough testing with time and resource constraints, how would you prioritize tests for this project? 

Which types of tests (unit, integration, parameterized, etc.) would you focus on, and how would you ensure test coverage remains effective over time?

**Answer:**
```txt

I would prioritize tests based on risk and business value. Core domain logic and persistence should be covered first with unit tests to ensure correctness of calculations, validations, and repository interactions. Integration tests are important for verifying that the REST endpoints, database, and transaction boundaries work together as expected. For example, optimistic locking in Warehouse or event firing in Store should be validated with integration tests.

Parameterized tests can be useful for edge cases (e.g., invalid IDs, missing fields) without duplicating code. Over time, I’d enforce coverage on critical paths (create, update, delete flows) and use CI pipelines to run tests automatically. To keep coverage effective, I’d review tests whenever new features are added, and focus on regression tests for bugs that were previously found, so they don’t reappear.


```
