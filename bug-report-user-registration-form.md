# Bug Report: User Registration Form

| Bug ID  | Title                                            | Field              | Severity |
| ------- | ------------------------------------------------ | ------------------ | -------- |
| Bug_001 | Duplicate registration allowed with same email   | Sign Up            | Major    |
| Bug_002 | Full Name field accepts invalid values           | Full Name          | Major    |
| Bug_003 | Invalid email formats show generic error         | Email              | Major    |
| Bug_004 | Unclear warning message on trailing dot in email | Email              | Minor    |
| Bug_005 | Leading/trailing spaces accepted in email        | Email              | Major    |
| Bug_006 | Unclear warning message on accented characters   | Email              | Major    |
| Bug_007 | Unclear warning message on multiple @ symbols    | Email              | Major    |
| Bug_008 | Very long email (>254 characters) accepted       | Email              | Major    |
| Bug_009 | Password field accepts weak/invalid values       | Password           | Critical |
| Bug_010 | Confirm Password mismatch accepted               | Confirm Password   | Major    |
| Bug_011 | T&C checkbox not enforced                        | Terms & Conditions | Major    |
| Bug_012 | Accessibility issues                             | Accessibility      | Major    |

---

Bug_001 – Duplicate registration allowed with same email

Severity: Major

Steps to Reproduce:
1. Sign up with test@example.com using valid details.
2. Sign up again with the same email.

Actual Result:
* System allows registration multiple times with the same email.

Expected Result:
* Registration should be rejected with a clear and user-friendly message.

---

Bug_002 – Full Name field accepts invalid values

Severity: Major

Steps to Reproduce:
1. Enter only a space.
2. Leave blank (auto-fills “anonymous”).
3. Enter very long string (>120 chars).
4. Enter numeric (John123).
5. Enter emoji (John😀).
6. Enter <script>alert(1)</script>.

Actual Result:
* All values accepted.

Expected Result:
* Spaces/Blanks rejected.
* Spaces trimmed.
* Enforce sensible length (2–120).
* Reject digits, emoji, and scripts.

---

Bug_003 – Invalid email formats show generic error

Severity: Major

Steps to Reproduce:
1. Enter a@b and submit.
2. Enter a..b@c.com and submit.

Actual Result:
* A generic error is displayed: "An error has occurred"

Expected Result:
* Invalid formats should be rejected with a clear and user-friendly message.

---

Bug_004 – Unclear warning message on trailing dot in email

Severity: Minor

Steps to Reproduce:
1. Enter a@b. as email.
2. Submit form.

Actual Result:
* Shows unclear warning: “'.' is used at a wrong position in ‘b.’”

Expected Result:
* Should reject with a clear and user-friendly message.

---

Bug_005 – Leading/trailing spaces accepted in email

Severity: Major

Steps to Reproduce:
1. Enter test@example.com (with spaces).
2. Submit form.

Actual Result:
* Email accepted with leading/trailing spaces.

Expected Result:
* Spaces should be trimmed automatically or rejected with an error.

---

Bug_006 – Unclear warning message on accented characters

Severity: Major

Steps to Reproduce:
1. Enter Üser@exámple.es.
2. Submit form.

Actual Result:
* Shows unclear warning: “A part followed by ‘@’ should not contain the symbol ‘ũ’.”
* Accepts accented characters after the @.

Expected Result:
* Should consistently accept accented characters.

---

Bug_007 – Unclear warning message on multiple @ symbols

Severity: Major

Steps to Reproduce:
1. Enter a@b@c.com.
2. Submit form.

Actual Result:
* Shows unclear warning: “A part following ‘@’ should not contain the symbol ‘@’.”

Expected Result:
* Should reject with a clear and user-friendly message.

---

Bug_008 – Very long email (>254 characters) accepted

Severity: Major

Steps to Reproduce:
1. Enter an email longer than 254 characters.
2. Submit form.

Actual Result:
* Accepted without validation.

Expected Result:
* Should reject with a clear and user-friendly message.

---

Bug_009 – Password field accepts weak or invalid values

Severity: Critical

Steps to Reproduce:
1. Enter empty password and submit.
2. Enter only spaces and submit.
3. Enter short (7 char) password and submit.
4. Enter 256+ char password and submit.
5. Enter password with `" ' \ / ; : < > { } [ ] | ~ `` and submit.
6. Enter password with Unicode (e.g., Pässwörd✓).

Actual Result:
* No rules enforced; all values accepted.

Expected Result:
* Minimum length ≥8 enforced.
* Reject empty or all-space passwords.
* Reject unsafe/injection strings.

---

Bug_010 – Confirm Password mismatch accepted

Severity: Major

Steps to Reproduce:
1. Enter Password: Qwe12345!.
2. Enter Confirm Password: Qwe12345?.
3. Submit.

Actual Result:
* Form accepts mismatched passwords.

Expected Result:
* Should reject with a clear and user-friendly message.

---

Bug_011 – T&C checkbox not enforced

Severity: Major

Steps to Reproduce:
1. Fill all fields correctly.
2. Leave Terms & Conditions unchecked.
3. Submit form.

Actual Result:
* Form submitted successfully.

Expected Result:
* Should reject with a clear and user-friendly message.

---

Bug_012 – Accessibility issues

Severity: Major

Steps to Reproduce:
1. Load registration page.
2. Observe initial focus.
3. Navigate with keyboard only.
4. Trigger errors on invalid fields.

Actual Result:
* No auto-focus in first field.
* Errors vague, not tied to fields.
* No aria-live announcements.
* No error summary for screen readers.

Expected Result:
* Auto-focus on first field.
* Errors tied to fields with aria-describedby.
* Errors announced with aria-live.
* Clear error summary at top of form.

# Improvements

| Improvement ID  | Title                         | Field    | Type      |
| --------------- | ----------------------------- | -------- | --------- |
| Improvement_001 | Add show/hide password option | Password | Usability |

---

Improvement_001 – Add show/hide password option

Type: Usability / Accessibility Improvement

Reason:
* Users cannot verify their password before submission, increasing chance of typos and failed logins.
* A show/hide toggle is a common UX pattern in modern registration forms.

Suggested Implementation:
* Add a toggle icon/button next to the password field.
