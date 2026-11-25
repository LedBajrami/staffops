# StaffOps requirements

StaffOps is a web platform for managing employee leave, work arrangements, and attendance. It gives employees a way to track their requests, managers a queue for decisions, and HR a way to calculate worked hours from card-reader events.

The stories below describe the planned StaffOps prototype. Recruitment is outside the project scope.

## Functional requirements

See the [StaffOps use-case diagram](diagrams/use-cases.png) for how each role interacts with StaffOps.

| ID | Priority | User story | Acceptance criteria |
| --- | --- | --- | --- |
| US-01 | Must | As an HR Admin or Super Admin, I want to manage companies and departments so the organisation is represented in StaffOps. | Both roles can manage companies and departments. A newly created company appears in the company list. A subsidiary can be linked to its parent company, and a department can be linked to its parent. |
| US-02 | Must | As an HR Admin, I want to create employee accounts. As a Super Admin, I want to manage and assign roles. | HR Admins can create an employee account with valid details. Super Admins can manage and assign roles. An employee can sign in and access the features allowed by their assigned role. |
| US-03 | Must | As an HR Admin, I want to assign one or more managers to an employee so new requests reach the right approvers. | New requests appear in the assigned managers’ approval queues. Changing the assignment leaves earlier requests and their approvers intact. |
| US-04 | Must | As an employee, I want to submit and track leave requests. | A request with valid dates and leave type is saved as Pending and is visible to the employee and assigned managers. Invalid or overlapping dates produce a clear error. |
| US-05 | Must | As a manager, I want to approve or reject leave requests from my team. | A manager can decide a pending request from their team. StaffOps saves the decision and displays the updated status to the employee. |
| US-06 | Must | As an employee, I want to request a work arrangement such as remote, hybrid, or on-site work. | A request with valid dates and an arrangement type reaches the employee’s manager for a decision. The employee can see the final status. |
| US-07 | Must | As the system, I want to import check-in and check-out events from the card-reader API automatically. | The import stores new events without duplicates. Failed imports are logged and retried. |
| US-08 | Must | As an HR Admin, I want to calculate attendance for selected employees and a date range. | The report shows worked hours per day and in total, taking approved leave into account. |

The application roles are Employee, HR Admin, and Super Admin. A manager is an employee with direct reports. Managers can submit and track their own leave and work arrangement requests, which go to their assigned managers for a decision. HR creates employee accounts.

## Non-functional requirements

These acceptance and deployment targets come from the project proposal.

| ID | Quality | Target |
| --- | --- | --- |
| NFR-01 | Performance | At least 95% of API requests complete in under 500 ms with 50 concurrent users. |
| NFR-02 | Availability | StaffOps is available at least 99.5% of the time during working hours (08:00–18:00). |
| NFR-03 | Security | All traffic uses HTTPS, passwords are stored as hashes, and every endpoint enforces its access rules. |
| NFR-04 | Data freshness | Card-reader events appear in StaffOps within 15 minutes of being recorded. |
| NFR-05 | Correctness | Attendance calculations match a manually verified dataset in 100% of test cases. |
| NFR-06 | Usability | A new employee can submit a leave request in under two minutes without training. |
