# Smart Campus Wi-Fi Monitoring & Network Health Dashboard

A responsive web-based platform for monitoring campus Wi-Fi performance, collecting network health data, managing connectivity complaints, identifying recurring network issues, and supporting IT teams in investigating and resolving network problems.

## Project Participants

| Name              | Roll No. |
| ----------------- | -------- |
| Ahmed Memon       | 24SW019  |
| Haroon Zulfiqar   | 24SW101  |
| Syed Sayeel Abbas | 24SW116  |
| Rasool Bux        | 24SW134  |


**University:** Mehran University of Engineering and Technology
**Department:** Software Engineering

---

## 1. Project Overview

The **Smart Campus Wi-Fi Monitoring & Network Health Dashboard** is designed to provide a centralized system for monitoring and managing campus network performance.

Students and staff may experience problems such as slow internet, high latency, frequent disconnections, weak connectivity, or complete network outages. In many cases, IT support receives complaints without sufficient technical information to determine the actual cause or scope of the problem.

This project addresses this issue by combining **network performance testing, location-based monitoring, complaint management, incident detection, IT investigation, analytics, notifications, and verified recovery** within a single platform.

The system enables users to test their connection at a specific campus location, view performance results, submit complaints with supporting evidence, and track the progress of reported issues. IT personnel can investigate complaints, identify related incidents, assign issues, record actions, and verify network recovery through follow-up testing.

---

## 2. Problem Statement

Campus network problems are often difficult to investigate because user complaints may not contain enough technical information.

For example, a user may report:

> "The Wi-Fi is very slow."

However, this does not indicate:

* The user's exact location
* Download or upload performance
* Network latency
* Whether other users are experiencing the same problem
* Whether the problem is temporary or recurring
* Whether the issue is limited to a particular building or floor
* Whether the problem has actually been resolved

The proposed system provides measurable network evidence and organizes complaints and technical investigations into a structured workflow.

---

## 3. Project Objectives

The primary objectives of the system are to:

* Measure network performance at specific campus locations.
* Record download speed, upload speed, and latency.
* Generate an understandable network health score.
* Maintain historical network performance data.
* Allow students and staff to submit connectivity complaints.
* Provide IT personnel with technical evidence for investigation.
* Identify multiple complaints that may represent the same network incident.
* Monitor recurring network problems across campus locations.
* Support assignment and tracking of IT investigations.
* Verify network recovery through follow-up testing.
* Provide dashboards and analytics for IT teams and management.
* Notify relevant users about important complaint or incident updates.
* Maintain appropriate authentication, authorization, and activity records.

---

## 4. Key Features

### 4.1 Network Performance Testing

Users can perform a network test from their device at a selected campus location.

The test can measure:

* Download speed
* Upload speed
* Application-level latency
* Optional packet loss where technically available
* Overall network health score
* Test completion status

The system records the test result together with its location and timestamp.

> **Important:** Network measurements are performed between the user's device and the designated test endpoint. A backend-only test does not represent the user's actual Wi-Fi experience.

---

### 4.2 Network Health Scoring

The system converts available network measurements into an understandable health score.

The proposed scoring model considers:

| Metric         | Proposed Weight |
| -------------- | --------------: |
| Download Speed |             35% |
| Upload Speed   |             20% |
| Latency        |             30% |
| Packet Loss    |             15% |

If a metric is unavailable, the score can be calculated using the available measurements after normalizing their weights.

### Health Categories

|  Score | Status    |
| -----: | --------- |
| 90–100 | Excellent |
|  75–89 | Good      |
|  50–74 | Fair      |
|  25–49 | Poor      |
|   0–24 | Critical  |

These values are configurable starting thresholds and can be adjusted according to the actual campus network requirements.

The system should also distinguish between a numerical health score and conditions such as:

* Unknown
* Stale
* Suspected Outage
* Maintenance

This prevents an unavailable measurement from being incorrectly interpreted as a poor network condition.

---

## 5. Location-Based Monitoring

Network performance is associated with specific campus locations, allowing the system to identify areas where connectivity problems occur repeatedly.

Users can select information such as:

* Building
* Floor
* Specific monitored location

The system maintains historical test information for each location and can display performance trends over time.

This allows IT teams and management to identify locations that may require further investigation or network improvements.

---

## 6. Complaint Management

Users can submit network-related complaints based on their experience.

### Complaint Categories

* No Internet
* Slow Internet
* High Ping / Latency
* Frequent Disconnection
* Weak Signal
* Website or Service Unavailable
* Other

Each complaint can contain relevant information such as:

* User
* Location
* Complaint category
* Description
* Related test result
* Submission time
* Current status

### Complaint Lifecycle

```text
Submitted
    ↓
Reviewed
    ↓
Assigned
    ↓
In Progress
    ↓
Resolved
```

Additional statuses may be used where required, including:

* Awaiting User
* Awaiting External Provider
* Duplicate
* Closed
* Reopened

---

## 7. Incident Detection

A **complaint** represents an individual user's report, while an **incident** represents a potentially shared network problem affecting multiple users or a particular location.

The system can analyze information such as:

* Recent network tests
* Failed test attempts
* Multiple complaints
* Different users reporting similar problems
* Location-based patterns
* Test endpoint availability
* Existing maintenance activities
* Historical network behavior

These signals can help identify whether several complaints may be associated with the same underlying network issue.

### Incident Lifecycle

```text
Suspected
    ↓
Confirmed
    ↓
Investigating
    ↓
Monitoring Recovery
    ↓
Resolved
```

---

## 8. IT Investigation Workflow

IT personnel can use the platform to investigate reported network problems.

The investigation process includes:

1. Review the reported complaint.
2. Examine the affected location.
3. Review recent network test results.
4. Compare current and historical performance.
5. Determine the potential scope of the issue.
6. Assign the investigation to an appropriate IT member.
7. Record investigation notes and actions.
8. Identify or document the probable cause.
9. Perform the required repair or maintenance.
10. Conduct a verification network test.
11. Confirm whether network performance has recovered.
12. Resolve the related complaint or incident.
13. Notify affected users where applicable.

This workflow creates a traceable record from the original complaint through investigation and verified recovery.

---

## 9. Dashboard and Analytics

The dashboard provides different information depending on the user's role.

### Student / Staff

Users can view:

* Current network test results
* Health score
* Test history
* Submitted complaints
* Complaint status
* Relevant notifications

### IT Support

IT personnel can monitor:

* Recent network tests
* Poor-performing locations
* Open complaints
* Active incidents
* Assigned investigations
* Location performance history
* Recovery verification

### Management

Management can review:

* Campus-wide network trends
* Frequently affected locations
* Complaint statistics
* Incident statistics
* Performance trends
* Locations requiring further attention

### Dashboard Filters

The system can support filtering by:

* Location
* Building
* Date range
* Network status
* Complaint category
* Complaint status

A location heatmap may use:

* Green — Healthy
* Yellow — Degraded
* Red — Poor or Critical
* Gray — Unknown or Stale

---

## 10. Authentication and Authorization

The system uses authenticated access to protect user and administrative functionality.

Role-based permissions can separate access for:

* Students / Staff
* IT Support
* Managers
* Administrators

Security considerations include:

* Secure authentication
* Role-based access control
* Protected application routes
* API authorization
* Input validation
* Secure session handling
* Rate limiting
* Bounded network test requests
* Audit logging
* Secure administrative access

User-provided network measurements should also be validated because client-side measurements may be inaccurate or manipulated.

---

## 11. Notifications

The system can notify users about relevant changes, such as:

* Complaint status updates
* Assignment of an issue
* Incident updates
* Resolution notifications
* Verification of network recovery

Notifications help maintain communication between users and IT support throughout the complaint lifecycle.

---

## 12. System Architecture

The proposed architecture separates the user interface, application services, network measurement system, database, and background processing.

```text
                    ┌──────────────────────┐
                    │   Web Application    │
                    │  Students / Staff    │
                    │   IT / Management    │
                    └──────────┬───────────┘
                               │
                               ▼
                    ┌──────────────────────┐
                    │   Backend API        │
                    │ Authentication       │
                    │ Authorization        │
                    │ Application Logic    │
                    └───────┬───────┬──────┘
                            │       │
                ┌───────────┘       └──────────────┐
                ▼                                  ▼
       ┌──────────────────┐               ┌──────────────────┐
       │     Database     │               │ Measurement      │
       │ Users            │               │ Service          │
       │ Locations        │               │ Download         │
       │ Tests            │               │ Upload           │
       │ Complaints       │               │ Latency          │
       │ Incidents        │               │ Optional Loss    │
       └──────────────────┘               └──────────────────┘
                ▲
                │
       ┌────────┴─────────┐
       │ Background       │
       │ Workers          │
       │ Aggregation      │
       │ Incident Rules   │
       │ Notifications    │
       └──────────────────┘
```

Measurement traffic is handled separately from normal application API traffic so that the network test reflects the user's connection to the designated test endpoint.

---

## 13. Proposed Data Model

The main entities of the system include:

* **User**
* **Building / Location**
* **Test Attempt**
* **Test Result**
* **Complaint**
* **Complaint Event**
* **Incident**
* **Incident Link**
* **Maintenance**
* **Threshold Configuration**
* **Notification**
* **Audit Event**

These entities support network monitoring, complaint management, investigation tracking, reporting, and system administration.

---

## 14. API Structure

The backend can provide REST-based API endpoints such as:

```text
POST   /auth/login
GET    /auth/me

GET    /locations

POST   /test-sessions
POST   /test-sessions/{id}/result
GET    /tests

POST   /complaints
GET    /complaints
PATCH  /complaints/{id}/assignment
POST   /complaints/{id}/transitions
POST   /complaints/{id}/notes

GET    /incidents

GET    /dashboard
GET    /analytics

GET    /admin/locations
GET    /admin/users
GET    /admin/thresholds
```

The exact implementation may be adjusted according to the selected backend framework and project requirements.

---

## 15. Example Test Result

A network test result can be represented as:

```json
{
  "test_id": "test_001",
  "location_id": "library_floor_2",
  "download_mbps": 36,
  "upload_mbps": 14,
  "latency_ms": 28,
  "packet_loss_percent": null,
  "health_score": 82,
  "health_status": "Good",
  "outcome": "completed",
  "tested_at": "2026-10-01T10:00:00Z"
}
```

---

## 16. Test Outcomes and Error Handling

The system should clearly distinguish successful tests from incomplete or unsuccessful attempts.

Possible outcomes include:

* Complete
* Partial
* Cancelled
* Endpoint Unreachable
* Internet Unavailable
* Save Failed
* Duplicate
* Invalid

Clear error states prevent users and IT personnel from interpreting incomplete measurements as valid network results.

---

## 17. Browser and Measurement Considerations

Because the application is designed as a web application, certain network information may not be directly available to the browser.

For example:

* Application-level round-trip time is not identical to ICMP ping.
* Failed HTTP requests cannot automatically be treated as true packet loss.
* Browser APIs may not expose Wi-Fi signal strength, SSID, or access-point information.
* Network Information API support may vary between browsers.
* Measurements depend on the selected test endpoint.
* Crowdsourced measurements represent sampled observations rather than continuous monitoring.

For the initial project implementation, reliable download speed, upload speed, and application-level latency measurements provide the core network monitoring functionality. Unsupported measurements can be displayed as **Not Measured** instead of being treated as zero.

---

## 18. Optional Intelligent Features

The system can be extended with intelligent or AI-assisted functionality, including:

* Network anomaly detection
* Automatic complaint classification
* Outage prediction
* Peak-usage prediction
* Identification of frequently problematic locations
* Complaint summarization
* Investigation recommendations

These features are optional and can be introduced after the core monitoring and complaint-management workflow is functional.

---

## 19. Project Structure

A proposed repository structure is:

```text
project/
│
├── frontend/
│   ├── user/
│   ├── it/
│   ├── manager/
│   └── admin/
│
├── backend/
│   ├── authentication/
│   ├── api/
│   ├── permissions/
│   └── services/
│
├── measurement/
│   ├── test-sessions/
│   └── transfer-endpoints/
│
├── intelligence/
│   ├── scoring/
│   ├── trends/
│   ├── incidents/
│   └── ai/
│
├── database/
│   ├── schema/
│   ├── migrations/
│   └── seed-data/
│
├── workers/
│   ├── aggregation/
│   └── notifications/
│
├── tests/
│   ├── integration/
│   └── acceptance/
│
├── docs/
│   ├── architecture/
│   ├── setup/
│   └── project-documentation/
│
└── deployment/
```

---

## 20. Testing Strategy

The system should be tested at multiple levels.

### Functional Testing

Verify that:

* Users can authenticate successfully.
* Locations can be selected.
* Network tests execute correctly.
* Results are stored correctly.
* Health scores are calculated correctly.
* Complaints can be submitted.
* IT personnel can assign and update complaints.
* Incidents can be created and managed.
* Recovery tests can verify resolution.
* Notifications are generated correctly.

### Integration Testing

Verify communication between:

* Frontend and backend
* Backend and database
* Backend and measurement service
* Complaint and incident modules
* Dashboard and analytics services
* Notification services

### Acceptance Testing

The complete user workflow should be tested from:

```text
Login
  ↓
Select Location
  ↓
Run Network Test
  ↓
View Result
  ↓
Submit Complaint
  ↓
IT Investigation
  ↓
Assignment
  ↓
Repair / Maintenance
  ↓
Verification Test
  ↓
Resolution
  ↓
Notification
  ↓
Analytics Update
```

---

## 21. Demonstration Workflow

The recommended project demonstration follows a complete real-world scenario:

1. Student or staff member logs into the system.
2. User selects a campus location.
3. User performs a live network test.
4. System displays download, upload, latency, and health score.
5. Test result is stored in the user's history.
6. User submits a complaint with the test result as supporting evidence.
7. IT support receives and reviews the complaint.
8. IT assigns the investigation.
9. The system identifies related complaints or repeated problems where applicable.
10. IT investigates the affected location.
11. Repair or maintenance is performed.
12. A verification test is conducted.
13. Recovery is confirmed.
14. Complaint or incident status is updated.
15. Relevant users receive a notification.
16. Dashboard and analytics reflect the updated network condition.

Any intentionally simulated poor-performance or outage scenario used during the demonstration should be clearly identified as a simulation.

---

## 22. Deployment Considerations

The application is designed as a responsive web application that can be accessed from:

* Desktop computers
* Laptops
* Tablets
* Mobile devices

The deployment environment should provide:

* Application hosting
* Database hosting
* Network test endpoint
* Secure HTTPS communication
* Environment-based configuration
* Secure secret management
* Logging and monitoring
* Database backups
* Appropriate data retention policies

---

## 23. Expected Outcome

The completed system provides a structured approach to campus network monitoring and support.

A user should be able to:

**Measure a location's connection → Report a problem with evidence → Track its progress → Receive verified resolution**

At the same time, IT teams and management should be able to:

**Monitor network performance → Identify recurring problems → Investigate incidents → Verify recovery → Analyze campus-wide trends**

The overall objective is to transform unstructured network complaints into measurable, traceable, and actionable network information.

---

## 24. Team Contributions

| Team Member           | Roll No. | Department | Contribution                                 |
| --------------------- | -------- | ---------- | -------------------------------------------- |
| **Ahmed Memon**       | 24SW019  | Software   | Frontend & Backend Integration, UI/UX Design |
| **Haroon Zulfiqar**   | 24SW101  | Software   | Authentication, Documentation & Testing      |
| **Syed Sayeel Abbas** | 24SW116  | Software   | Backend & Database Development               |
| **Rasool Bux**        | 24SW134  | Software   | Frontend Development                         |

---

## 25. Project Completion Criteria

The project will be considered complete when the core workflow is functional and a user can:

* Select a monitored campus location.
* Perform a network performance test.
* View measurable network results.
* Receive a health assessment.
* Submit a complaint with supporting evidence.
* Track the complaint status.
* Allow IT personnel to investigate and manage the issue.
* Associate related complaints with a common incident where appropriate.
* Perform a recovery verification test.
* Confirm resolution.
* Receive relevant notifications.
* Provide management with meaningful network trends and recurring-problem information.

---

## Project Status

**Project Type:** Academic / University Software Project
**Application Type:** Responsive Web Application
**Domain:** Campus Network Monitoring and IT Support
**Department:** Software

## Requirements

- Node.js 22.13 or newer and npm.
- Python 3.12 or newer.
- Four local terminals for the frontend, API, measurement service and worker.

## First setup — Windows PowerShell

Open a terminal in the extracted `smart-campus` folder:

```powershell
npm ci
Copy-Item .env.example .env.local
py -3.12 -m venv backend/.venv
backend/.venv/Scripts/python.exe -m pip install -r backend/requirements.txt
Set-Location backend
Copy-Item .env.example .env
.venv/Scripts/python.exe -m alembic upgrade head
.venv/Scripts/python.exe -m app.bootstrap --email your-admin@university.edu --campus "Mehran University of Engineering and Technology" --demo-locations
```

Bootstrap prompts for an administrator password of at least 10 characters. It creates the campus, initial administrator, threshold configuration, measurement endpoint and optional placeholder locations. It never creates fake measurement history. Use Locations in the administrator dashboard to replace placeholder names and place actual campus pins. The map defaults to MUET, Jamshoro; its center is not a building survey.

If upgrading an existing backend database, back it up, configure its `DATABASE_URL`, run `alembic upgrade head`, and sign in with existing accounts. Do not bootstrap a second campus unless intended.

## Run — separate terminals

All backend commands run from the `backend` folder, using the same `.env` and database:

```powershell
# Terminal 1: backend API
.venv/Scripts/python.exe -m uvicorn app.main:app --host 127.0.0.1 --port 8000
```

```powershell
# Terminal 2: browser measurement service
.venv/Scripts/python.exe -m uvicorn app.measurement:app --host 127.0.0.1 --port 8001
```

```powershell
# Terminal 3: incident detection and expired-session processing
.venv/Scripts/python.exe -m app.worker
```

```powershell
# Terminal 4: frontend, from the smart-campus root folder
npm run dev
```

Open `http://127.0.0.1:5173`. The Vite development proxy forwards `/api` to port 8000 and `/measure` to port 8001. Sign in with the administrator created above. Students can create accounts through the existing sign-up page; administrators can then change their roles to IT Support or Manager in Users. If there is more than one campus, set `VITE_CAMPUS_ID` in the frontend `.env.local` to the campus ID printed by bootstrap and restart Vite.

Swagger API documentation is available at `http://127.0.0.1:8000/docs`. Initial endpoint health is deliberately unconfirmed. After testing endpoint reachability and capacity, an administrator can enable `operator_healthy` through `PATCH /admin/endpoints/{id}` in Swagger; this is required for reliable automatic incident detection.

## What is connected

- Authenticated role-specific dashboards with server-enforced campus scope.
- Real browser-to-endpoint RTT, download and upload measurements, scoring and history.
- Complaints with map-selected locations, optional test attachments, assignment and investigation notes.
- Manual IT complaint resolution from any status, with optional resolution notes and an audit trail.
- Custom map locations and administrator pin/name editing.
- Persistent maintenance notes, support activity and recurring-problem reporting.
- Account roles, activation, role capabilities and versioned health thresholds.
- Persistent user notifications, read state, error feedback and recorded analytics.

See [INTEGRATION.md](INTEGRATION.md) for architecture, schema changes, validation and limitations.

## Validate

```powershell
# Project root: TypeScript and frontend production build
npm run build
npm test
# backend folder: backend tests, migration drift and integration coverage
.venv/Scripts/python.exe -m pytest tests -q
```

The integrated build and all 18 backend tests pass. Live browser verification used an isolated synthetic database; its users, credentials and records are not packaged.

## Deployment and measurement limits

Deploy the frontend build with a reverse proxy for `/api`, or set `VITE_API_URL` before building. The measurement endpoint returned by the API must be reachable from the user's device. Configure HTTPS, CORS origins, production secrets, PostgreSQL, backups and shared rate limiting. See [backend/docs/DEPLOYMENT.md](backend/docs/DEPLOYMENT.md).

The dashboard measures the device’s active internet connection directly against Cloudflare. Each full test transfers about 26 MiB and never proxies speed traffic through localhost. The optional canonical campus measurement API still measures its configured endpoint. HTTP tests cannot measure packet loss or Wi-Fi signal, and selecting a campus location does not prove Wi-Fi association. Campus-wide history omits user identities. The supplied backend has no email password-recovery service; the existing recovery form reports this limitation. Notifications are in-app and refresh every 30 seconds.

`VITE_USE_BACKEND=false` explicitly restores the original local demo workspace for demonstrations. It should not be enabled for live campus operations.

The ZIP excludes dependencies, virtual environments, caches, credentials and databases. Install dependencies with the commands above.
