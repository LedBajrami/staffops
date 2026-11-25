# StaffOps database design

This draft outlines the main entities and their relationships in MariaDB.

| Entity | Planned relationship or purpose |
| --- | --- |
| Company | A company may have a parent company to represent a subsidiary. |
| Department | A department belongs to a company and may have a parent department. |
| User | An employee account has a role and can be assigned to a department. |
| Reporting relationship | Links an employee to a manager. Multiple links support employees who report to more than one manager. |
| Leave request | Belongs to an employee and records a leave type, dates, and status. |
| Work arrangement request | Belongs to an employee and records an arrangement type, dates, and status. |
| Request approver | Records who was assigned to a request when it was submitted and captures the decision. Later reporting changes apply to new requests. |
| Attendance event | Records a check-in or check-out from the card-reader system. The source event identifier supports duplicate detection on reimport. |

See the [requirements](requirements.md) for acceptance criteria and the [architecture diagram](architecture.md) for how Laravel and MariaDB interact.
