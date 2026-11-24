# TrackerApp

A task and follow-up tracker in the smarterSec platform style, built as a single HTML page.

## What it does

- **Overview** cards for all items and each category (open, in progress, overdue, done, completion).
- **Items** table with search and filters for status, category, company and sort. Each card remembers its own filters.
- **Change log** of every create, edit, status change and delete, with a date-range delete for Admins.
- **Users** with the roles Admin, Member and Read-only.

## Where it runs

| Where | Data | Users and roles |
|---|---|---|
| Published on claude.ai | Shared database of the artifact, live for everyone with access | Yes |
| Opened from this folder in a browser | This browser only ("Saved in this browser only") | No, everything allowed |

Open it locally for testing:

```powershell
Start-Process .\trackerapp.html
```

The live version is published from this file to claude.ai only when a change set is ready.

## Data model (claude.ai database)

| Collection | Contents |
|---|---|
| `items` | Item subject, status, priority, company, category, due date, notes, timestamps |
| `log` | Change log entries: time, who, item, field changes |
| `categories` | Defined categories and their order (write: Admins only) |
| `roles` | Role per user (write: Admins only) |
| `members` | Who opened the tracker and when (each person writes their own) |
| `data/users/<id>/prefs` | Each person's remembered filters (private) |
