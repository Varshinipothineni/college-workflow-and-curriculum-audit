# Workflow Test Cases and Expected Results

These are documented scenario tests of the proposed workflow design; they are not results from a deployed application.

| Case | Input condition | Expected result | Recovery / control |
|---|---|---|---|
| Normal request | Complete, valid request from an authorized student | Request is accepted, assigned an ID, and routed to the responsible owner | Status remains visible; owner completes and closes request |
| Missing information | Required field or attachment absent | Request is marked `Needs information`; it is not approved or processed further | Student receives a clear request for the missing item and can resubmit |
| Duplicate | Same request submitted twice with matching identifying fields | Duplicate is flagged and linked to the existing request rather than counted as a new independent case | Owner checks the match and merges or rejects the duplicate with an audit note |
| Unauthorized request | Requester lacks the role or permission for the requested action | Access is denied and no protected change is made | Explain the authorization boundary; route to an authorized approver if appropriate |
| Failed step | Owner or service cannot complete the next workflow step | Request is marked `Blocked` or `Failed` with a reason; it is not silently lost | Retry safely, escalate to the accountable owner, and preserve the audit trail |

## Interpretation
Expected results describe acceptance criteria for the proposed process. They should be run against a working implementation before being described as executed tests.
