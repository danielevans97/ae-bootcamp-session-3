# Product Requirements Document (PRD) - TODO App Upgrade

## 1. Overview

We are upgrading the basic TODO app so users can better plan and triage work without increasing system complexity. The current app only tracks a task title and completion state. This enhancement adds lightweight task planning features centered on due dates, priority, and date-based filtering while keeping the implementation teachable and fully local.

The MVP is intentionally constrained to frontend-focused changes with no backend or external storage work. The goal is to make the app more practical for day-to-day task management while preserving a simple data model and straightforward user experience.

---

## 2. MVP Scope

- Add an optional `dueDate` field to each task.
- Require `dueDate`, when present, to use ISO date format `YYYY-MM-DD`.
- Treat invalid `dueDate` values as absent rather than blocking task use.
- Add a `priority` field with allowed values `P1`, `P2`, and `P3`.
- Default `priority` to `P3` when a value is not provided.
- Keep `title` as a required field.
- Add task filters for `All`, `Today`, and `Overdue`.
- Keep completed tasks visible in the `All` filter.
- Hide completed tasks in the `Today` and `Overdue` filters so those views only show incomplete tasks.
- Keep all task storage local only.
- Do not introduce backend changes, shared persistence, or external storage integrations.

---

## 3. Post-MVP Scope

- Visually highlight overdue tasks so they stand out in the list.
- Add task sorting with this order: overdue tasks first, then priority from `P1` to `P3`, then due date ascending, with tasks that have no due date placed last.
- Consider visual priority treatments such as color-coded badges after the MVP behavior is complete and stable.

---

## 4. Out of Scope

- Notifications
- Recurring tasks
- Multi-user support
- Keyboard navigation and additional accessibility-specific enhancements beyond the current baseline
- External storage or backend-backed persistence