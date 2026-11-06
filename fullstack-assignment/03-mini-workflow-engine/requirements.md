# Assignment 03 — Requirements

**v1.0 — 2026-11-06**

## A. Functional requirements
- Create, view, edit and delete a task.
- Each task has title, description, priority (Low / Medium / High), status (Todo / In Progress / Done), created_at, updated_at.
- List tasks with status and priority filters and text search.
- Show task details and a chronological activity history.
- Record activity when a task is created, edited, deleted, or changes status.
- Basic validation with useful error messages.

## B. Database (suggested)

| Table | Suggested fields |
|---|---|
| tasks | id, title, description, priority, status, created_at, updated_at |
| task_activities | id, task_id, action, old_value, new_value, created_at, actor_id (optional) |

Deliverables: schema or migration, keys, constraints, indexes with justification.

## C. API scope (adjustable if documented)

| Method | Endpoint | Purpose |
|---|---|---|
| POST | /tasks | Create a task |
| GET | /tasks | List with filters, search, pagination |
| GET | /tasks/{id} | Fetch task details |
| PATCH | /tasks/{id} | Update fields or status |
| DELETE | /tasks/{id} | Delete a task |
| GET | /tasks/{id}/activities | Retrieve history |

## D. Engineering depth checks (answer in README)
- What happens when a client updates a task that does not exist?
- How do you ensure the task update and the activity record commit together?
- Where should filtering, sorting and pagination happen, and why?
- How do you validate status and priority values?
- What if two users update the same task at nearly the same time?
- Which operations need transactions? How would you test failure cases?

## E. Code structure expectations
- Separate routes/controllers from business logic and database access.
- Reusable UI components. No duplicated task form or list logic.
- Clear types or schemas for request and response data.
- Handle loading, empty, success and error states.
- No unnecessary frameworks, abstractions or infrastructure.

## F. Live follow-up
The interviewer may ask you to add a **Blocked** status and propagate it through the UI, API validation, database representation (if applicable), activity history and tests. Structure the code so this is a small change.
