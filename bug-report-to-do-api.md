| Bug ID  | Title                                         | Endpoint                 | Severity |
| ------- | --------------------------------------------- | ------------------------ | -------- |
| API_001 | GET /tasks returns items with `title: null`   | GET /tasks               | Major    |
| API_002 | Inconsistent `id` type (string vs number)     | All responses            | Major    |
| API_003 | POST accepts `null` or empty `title`          | POST /tasks              | Major    |
| API_004 | DELETE succeeds (204) but GET by id still 200 | DELETE + GET /tasks/{id} | Major    |

---

API_001 – GET /tasks returns items with title: null

Severity: Major 

Steps to Reproduce:
1. Call GET /tasks.
2. Inspect returned items.

Actual Result:
* Some task objects have "title": null.

Expected Result:
* title should always be a non-empty string.

---

API_002 – Inconsistent id type (string vs number)

Severity: Major Steps to Reproduce:
1. Call POST /tasks to create a task.
2. Call GET /tasks.
3. Compare id types.

Actual Result:
* Some responses return "id": "183" (string), others return "id": 189 (number).

Expected Result:
* id type should be consistently integer only.

---

API_003 – POST accepts null or empty title

Severity: Major 

Steps to Reproduce:
1. Send POST /tasks with body { "title": null}.
2. Send POST /tasks with body { "title": "" } or { "title": " " }.

Actual Result:
* Tasks are created with invalid/empty titles.

Expected Result:
* API should reject invalid titles with 400 Bad Request and a clear error message.

---

API_004 – DELETE succeeds (204) but GET by id still 200

Severity: Major Steps to Reproduce:
1. POST /tasks → capture id.
2. DELETE /tasks/{id} → returns 204.
3. GET /tasks/{id} → returns 200.
4. GET /tasks → task no longer listed.

Actual Result:
* GET by id still returns 200.

Expected Result:
* GET /tasks/{id} should return 404 Not Found after deletion.
