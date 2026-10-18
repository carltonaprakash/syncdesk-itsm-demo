# syncdesk-itsm-demo
# SyncDesk

A unified service desk demo that combines **ServiceNow-style IT service management** with **Jira-style issue tracking** in one employee-facing website.

**Live demo:** https://carltonaprakash.github.io/syncdesk-itsm-demo/

**Demo login:** username `admin`, password `admin`

> SyncDesk is an independent demo project that simulates ServiceNow-style incident handling and Jira-style issue tracking. It is not affiliated with or connected to ServiceNow or Atlassian, and all tickets shown are sample data.

---

## The problem

Service desks and development teams usually work in separate tools. When an incident needs a developer fix, someone copies the details across by hand, and the employee who raised the ticket never sees the progress.

## The solution

One site, opened only after login, where employees raise incidents, L1 agents work them, and anything that needs engineering is raised as a linked Jira-style issue. Status changes flow in both directions and the employee is notified at every step.

## Features

| Area | What it does |
| --- | --- |
| Login | Gate in front of the whole site (demo credentials only) |
| Dashboard | Service health, quick actions, filterable ticket queue, 3-step new request form, SLA heatmap and ticket aging |
| Service Desk (ServiceNow side) | Create incidents, move them through New, In Progress, On Hold, Resolved and Closed, live SLA timers |
| Board (Jira side) | Kanban board with To Do, In Progress, In Review and Done; raise incidents as linked Jira issues |
| Knowledge base | 8 searchable troubleshooting guides; raise an incident if the fix fails |
| Change and problem | Change requests with an approval workflow; problem records linked to incidents |
| Alerts | Dropdown notifications with an unread count, plus SLA warnings |
| Fresher guide | A 10-step walkthrough with a progress bar, key terms and good habits for people new to IT support |

## How the two sides stay in sync

1. An employee raises a ticket, for example `INC0010231`.
2. An L1 agent tries the knowledge base fix.
3. If it is not fixed, **Raise in Jira** creates a linked issue such as `SD-14`.
4. Moving the Jira card to **In Progress** sets the incident to In Progress.
5. Moving the card to **Done** sets the incident to **Resolved**, and resolving the incident moves the card to Done.

## SLA rules

| Priority | Respond within | Resolve within |
| --- | --- | --- |
| P1 Critical | 15 min | 4 hrs |
| P2 High | 30 min | 8 hrs |
| P3 Moderate | 2 hrs | 24 hrs |
| P4 Low | 4 hrs | 72 hrs |

- Timer colors: green under 70% of the resolve time, amber 70% to 100%, red when breached.
- Setting a ticket to **On Hold** pauses its clock (the "Waiting for user" rule).
- Alerts are sent at 80% of the resolve time, on a breach, and on a missed response.
- The targets live in one `SLA` setting in `index.html`, so they are easy to change.

## Tech

A single `index.html` file using plain **HTML, CSS and JavaScript**. No frameworks, build step or backend. It has a burgundy and cream theme, light and dark modes, and a responsive layout for phones and laptops.

## Run it locally

Download `index.html` and open it in any browser.

## Limitations

- It is a workflow simulation. It does not connect to a real ServiceNow or Jira instance.
- The login is checked inside the page, so it is a demo gate and not real security.
- Data lives in the browser and resets when the page is refreshed.
- Notifications appear only on the device where the page is open.

## Possible next steps

- Connect to a ServiceNow developer instance and Jira's free tier through their REST APIs.
- Add a database and real sign-in (for example Firebase or Supabase) so tickets persist and are shared.
- Link change requests to Jira tasks and add SLA performance reports.

## Author

**Carlton Anthony Prakash**, BCA graduate focused on IT Support and IT Operations.
LinkedIn: https://www.linkedin.com/in/carltonaprakash

## License

MIT, see [LICENSE](LICENSE).
