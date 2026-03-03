# Project Agents Guide for OpenAI Codex (com.dev.raise)

This document defines mandatory rules and conventions for OpenAI Codex and other AI agents interacting with this Spring Boot + Thymeleaf CRUD application.  
It ensures consistency, safety, readability, and architectural integrity across the codebase.

Codex must follow the rules in this document unless explicitly instructed otherwise by the user.

---

## 1. Project Structure for Codex Navigation

The project follows a standard Spring Boot structure. Codex must interpret all directories as follows:

src/
main/
java/
com/dev/raise/
model/        ← JPA Entity classes
repository/   ← Spring Data JPA repositories
service/      ← Business logic (interfaces & implementations)
controller/   ← MVC (Thymeleaf) + REST controllers
resources/
application.properties   ← Application & DB configuration
templates/               ← Thymeleaf HTML templates
static/                  ← CSS/JS/images
test/                        ← JUnit + Spring Boot Tests
pom.xml
README.md

### Requirements for Codex:
- All source code must live under `src/main/java/com/dev/raise/...`.
- Entities → `model/`
- Repositories → `repository/`
- Services → `service/`
- Controllers (MVC + REST) → `controller/`
- HTML templates → `resources/templates`
- Static assets → `resources/static`
- Codex must never modify files outside these folders unless explicitly commanded.

---

## 2. Domain Naming Pattern Using `<Domain>`

Because actual domain names may change, Codex must use the following naming pattern for any CRUD entity:

### Entity
- `com.dev.raise.model.<Domain>`

### Repository
- `com.dev.raise.repository.<Domain>Repository`

### Service Interface
- `com.dev.raise.service.<Domain>Service`

### Service Implementation
- `com.dev.raise.service.<Domain>ServiceImpl`

### MVC Controller (Thymeleaf)
- `com.dev.raise.controller.<Domain>Controller`

### REST Controller (JSON API)
- `com.dev.raise.controller.<Domain>RestController`

Codex must:
- Replace `<Domain>` with the actual domain name (e.g., Employee, Customer).
- Not introduce random or alternative naming conventions.
- Follow this pattern consistently across all newly created classes.

---

## 3. Controller Architecture (MVC + REST)

Both patterns are valid and must remain strictly separated by responsibility.

### MVC Controllers (`@Controller`)
- Return Thymeleaf views.
- Expose HTML pages.
- Use Spring `Model`, `ModelAndView`, etc.

### REST Controllers (`@RestController`)
- Return JSON responses.
- Use `@GetMapping`, `@PostMapping`, etc.
- Must not return view names.

### URL Namespace Rules
Codex must enforce:

- **MVC / HTML pages:**  
  `GET /app/<domain>/...`

- **REST API:**  
  `GET /api/<domain>/...`

Codex must never:
- Mix API paths with HTML paths.
- Reuse the same URL for both HTML and JSON endpoints.

---

## 4. Coding Conventions (Readability-First)

Codex must prioritize **clarity and maintainability**:

### Naming Rules
- Class names: PascalCase (`EmployeeService`)
- Methods & fields: camelCase (`findAllEmployees`)
- Constants: UPPER_SNAKE_CASE (`MAX_PAGE_SIZE`)
- Packages: lowercase (`com.dev.raise.service`)

### Style Expectations
- Use descriptive names, not abbreviations.
- Add comments for complex logic.
- Avoid deep nesting; prefer early returns.
- Split large logic into smaller methods where appropriate.

---

## 5. Thymeleaf Templates & Static Files

### Thymeleaf (`/resources/templates`)
Codex must:
- Store all HTML under `templates/`
- Use Thymeleaf syntax (`th:text`, `th:each`, `th:if`, `th:field`)
- Escape user inputs by default (`th:text`)
- Follow MVC patterns where controllers return logical view names

### Static Resources (`/resources/static`)
Codex must:
- Place JavaScript, CSS, and images in `static/`
- Avoid inlining large JS/CSS directly into templates
- Follow typical structure:

static/
css/
js/
images/

---

## 6. Database (MySQL Local)

Codex must assume local MySQL usage.

### Entities
- Must use JPA annotations (`@Entity`, `@Id`, `@GeneratedValue`, etc.)

### Repository Layer
- Must extend `JpaRepository<Domain, Long>` unless otherwise specified.

### Database Configuration (example)
Codex must not modify this unless clearly instructed:

```properties
spring.datasource.url=jdbc:mysql://localhost:3306/<db_name>?useSSL=false&serverTimezone=UTC
spring.datasource.username=<user>
spring.datasource.password=<password>
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true


⸻

7. Service Layer Rules

Codex must follow:
	•	Services contain business logic.
	•	Controllers must remain thin.
	•	Service class names follow:
	•	Interface: <Domain>Service
	•	Impl: <Domain>ServiceImpl
	•	Method names should represent business operations:
	•	create<Domain>()
	•	update<Domain>()
	•	delete<Domain>()
	•	findAll<Domain>()

Codex must not duplicate business logic across controllers.

⸻

8. Testing Requirements

Frameworks
	•	JUnit 5 (Jupiter)
	•	Spring Boot Test (@SpringBootTest, @WebMvcTest, etc.)
	•	Mockito when needed

Test Naming
	•	Tests stored under src/test/java/
	•	Suffix must be *Test, e.g.:
	•	EmployeeServiceTest
	•	EmployeeControllerTest

Test Command

Codex must assume:

<!-- ./mvnw test -->

Codex must:
	•	Ensure newly generated code does not break existing tests.
	•	Add/update tests when introducing behavior.

⸻

9. Pull Request Guidelines (GitHub Workflow)

Codex must follow:
	1.	PRs must focus on a single responsibility.
	2.	Include clear description of:
	•	What changed
	•	Why it changed
	•	Which domain(s) were affected
	3.	Reference related issues (Closes #123) where applicable.
	4.	Ensure all tests pass before creating the PR.
	5.	For UI changes:
	•	Include screenshots (before/after) if possible.

Codex must avoid mixing unrelated refactors, formatting, or feature changes in a single PR.

⸻

10. Programmatic Checks Before Merge

Codex must ensure the following succeeds before considering a change valid:

<!-- ./mvnw test -->

If additional checks are introduced (linting, formatting, integration tests), Codex must also use them.

⸻

11. Safety Rules and Forbidden Actions for Codex

Codex must strictly follow these rules:
	1.	No file deletions unless explicitly told.
	2.	No destructive changes to public method signatures or API contracts.
	3.	Do not modify application.properties unless directly instructed.
	4.	Do not rewrite existing Thymeleaf templates except when explicitly requested.
	5.	Do not modify static resources (css, js, images) unless requested.
	6.	Do not interact with secrets:
	•	.env
	•	*.key
	•	*.pem
	•	config/secrets.*
	7.	No large-scale refactoring without explicit approval.
	8.	Do not introduce speculative features or new domains not described by the user.
	9.	When uncertain, Codex must ask for clarification instead of guessing.

⸻

12. General Behavior for Codex

Codex must:
	•	Respect the existing architecture.
	•	Make small, incremental changes unless instructed otherwise.
	•	Prefer readable, maintainable code.
	•	Generate tests when adding business logic.
	•	Never assume external web access or external services unless already present.

This document acts as the authoritative guide for Codex’s behavior in this repository.

---
