---
name: flask-htmx-fullstack
description: >
  Full-stack web application developer using Flask (server), HTMX + Alpine.js (frontend),
  and sqlite-utils (database). Use this skill whenever the user wants to build, scaffold,
  extend, or debug a personal web project or web application — even if they say things like
  "build me an app", "create a website with a database", "I want a Flask project", "make
  something with HTMX", "help me set up a web app", or "I want a simple full-stack app".
  Also trigger when they mention CRUD apps, admin dashboards, personal tools, note-taking
  apps, todo lists, inventory trackers, or any project involving a server + frontend + database.
  Always use this skill: it encodes a battle-tested, opinionated stack with a structured
  Grill → Plan → Build workflow that ensures clarity before coding, and correctness before aesthetics.
---

# Flask + HTMX + Alpine.js + sqlite-utils — Full-Stack Skill

## Stack Overview

| Layer     | Technology       | Role                                      |
|-----------|------------------|-------------------------------------------|
| Server    | Flask            | Routes, API endpoints, HTML rendering     |
| Frontend  | HTMX + Alpine.js | Interactivity without a JS build step     |
| Database  | sqlite-utils     | Pythonic SQLite — no ORM boilerplate      |
| Templates | Jinja2           | Server-side HTML rendering (Flask default)|

---

## Master Workflow — ALWAYS follow this order

```
1. GRILL     → Ask clarifying questions (buttons preferred)
2. PLAN      → Present full plan, wait for approval
3. BUILD P1  → Bare minimal, functionality only
4. DEBUG     → User tests → fix loop until Phase 1 confirmed working
5. BUILD P2  → Polish: design, styling, UX
6. DEBUG     → User tests → fix loop until Phase 2 confirmed working
7. DOCS      → Generate Technical Guide + User Guidebook
```

Never skip or reorder steps. Never write code before the plan is approved.

---

## Step 1 — Grill (Clarification)

Use the `ask_user_input_v0` tool to present interactive questions as buttons.
Keep the first batch to 3 questions max. After answers, ask follow-up questions
**only if genuine ambiguity remains** — not exhaustively.

### First-batch question categories to cover:
- What does the app do / what problem does it solve?
- What data does it manage? (what tables/entities)
- What actions does the user need? (CRUD, toggle, filter, search, etc.)

### Follow-up if still unclear after first batch:
- Multiple users or single-user?
- Any relationships between data entities?
- Specific UI behaviours (inline edit, drag-reorder, modals)?

Stop grilling once the scope is clear enough to write an unambiguous plan.

---

## Step 2 — Plan (Always all three tiers, wait for approval)

Present the plan in three tiers. Do NOT collapse or omit any tier.
End with: **"Does this plan look right? Reply 'approved' to start building."**
Do not write any code until the user explicitly approves.

### Tier 1 — Feature List
A plain-language bullet list of every user-facing capability.

### Tier 2 — File Structure + Route Table
```
project-name/
├── app.py
├── database.py
├── requirements.txt
├── templates/
│   ├── base.html
│   ├── index.html
│   └── _partials...
└── static/
    └── main.css
```

| Method | URL              | Purpose                        | Returns         |
|--------|------------------|--------------------------------|-----------------|
| GET    | /                | Render main page               | Full HTML page  |
| POST   | /items           | Create new item                | HTML partial    |
| DELETE | /items/<id>      | Remove item                    | Empty string    |
| PATCH  | /items/<id>      | Update item field              | HTML partial    |

### Tier 3 — DB Schema + HTMX Interaction Map + Components

**DB Schema:**
```
table: items
  id       INTEGER PRIMARY KEY
  title    TEXT NOT NULL
  done     INTEGER DEFAULT 0   -- sqlite has no BOOLEAN; use 0/1
  created  TEXT                -- ISO timestamp string
```

**HTMX Interaction Map:** (list every dynamic interaction)
- Add form → POST /items → appends `_item.html` partial to `#item-list`
- Delete button → DELETE /items/<id> → removes `#item-<id>` from DOM
- Toggle checkbox → PATCH /items/<id>/toggle → swaps updated `_item.html`

**Alpine.js Components:** (list every stateful UI element)
- `{ open: false }` — controls add-form visibility

---

## Step 3 — Build Phase 1 (Bare Minimal)

Generate ALL files at once with complete, commented code.
No CSS framework. Minimal inline styles only. Pure function over form.

### `app.py` must always include:
```python
if __name__ == "__main__":
    # debug=True enables auto-reload on file save — no manual restart needed
    # reloader_type="stat" is more reliable across OSes
    app.run(debug=True, use_reloader=True)
```

Run instruction to give the user:
```
python app.py
```
Flask will auto-reload every time you save a file. No restart needed.

After delivering all files, say:
> **"Run `python app.py` in your terminal. Flask will auto-reload on every save.
> Test [specific feature] and let me know what happens."**

---

## Step 4 — Debug Loop

When the user reports an error or requests a change:

1. Read the traceback or description carefully
2. Identify the file(s) and line(s) to fix
3. Output the **complete updated file** (never partial snippets — avoids copy-paste errors)
4. At the top of the file, add a comment: `# UPDATED: <what changed and why>`
5. End with:
   > **"Save `filename.py` — Flask will reload automatically.
   > Test [specific thing] and report back."**

Repeat until the user confirms the feature works.
Only move to Phase 2 after explicit user confirmation ("works", "looks good", etc.).

---

## Step 5 — Build Phase 2 (Design & Polish)

Add styling only after Phase 1 is confirmed working. Apply:
- Tailwind CSS via CDN (default) or user-specified framework
- Consistent colour palette, spacing, typography
- Responsive layout (mobile-first)
- Loading indicators (`hx-indicator`) on HTMX requests
- Transitions and animations (Alpine `x-transition`)
- Empty-state messages when lists are empty
- Success/error feedback toasts or inline messages

Use the same debug loop (Step 4) for Phase 2 issues.

---

## Step 6 — Documentation (generate at end of Phase 2)

### Technical Guide (`TECHNICAL_GUIDE.md` or `TECHNICAL_GUIDE.html`)
Sections:
- Architecture overview (ASCII diagram)
- File-by-file explanation with purpose of each
- Full route reference (method, URL, params, return shape)
- Database schema (all tables, columns, types, constraints)
- HTMX interaction map (trigger → request → DOM target → swap)
- Alpine.js component inventory (where used, what state)
- How to add a new feature (step-by-step walkthrough)
- Local dev setup + deployment guide (Gunicorn / Render / Railway)

### User Guidebook (`USER_GUIDE.md` or `USER_GUIDE.html`)
Sections:
- What the app does (plain language, no jargon)
- Installation and first run
- Feature-by-feature usage instructions
- Troubleshooting / FAQ

> **HTML output:** If the user requests `.html` instead of `.md`, generate a
> self-contained single file with embedded CSS — no external dependencies,
> opens offline in any browser.

---

## Code Rules (apply to every file)

1. **Comment every block** — explain what it does and why, not just what it is
2. **Comment every route** — method, URL, purpose, return value
3. **Comment every `hx-*` attribute** inline — trigger, target, swap behaviour
4. **Comment every `x-*` directive** inline — what state it tracks or reacts to
5. **Comment every DB operation** — table, query intent, shape of data returned
6. Keep routes thin — delegate all DB logic to `database.py`
7. Always use `alter=True` in sqlite-utils inserts to allow schema evolution
8. Always return HTML partials from HTMX-targeted routes, not JSON

---

## Canonical Patterns

### `database.py`
```python
# database.py
# All DB access lives here. Import get_db() in app.py.
from sqlite_utils import Database

DB_PATH = "data.db"

def get_db() -> Database:
    """Return a live sqlite-utils Database. Auto-creates file if missing."""
    return Database(DB_PATH)

def init_db():
    """Create all tables at app startup. Safe to call multiple times."""
    db = get_db()
    if "items" not in db.table_names():
        db["items"].insert(
            {"title": "Welcome item", "done": False},
            alter=True  # allows adding columns later without schema migration
        )
```

### `app.py` shell
```python
# app.py
from flask import Flask, render_template, request
from database import get_db, init_db

app = Flask(__name__)

with app.app_context():
    init_db()  # ensure tables exist before first request

@app.route("/")
def index():
    """GET / — render main page with all rows from DB."""
    db = get_db()
    items = list(db["items"].rows)
    return render_template("index.html", items=items)

if __name__ == "__main__":
    # debug=True: auto-reloads on file save, shows tracebacks in browser
    app.run(debug=True, use_reloader=True)
```

### `templates/base.html`
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>{% block title %}App{% endblock %}</title>

  <!-- HTMX: AJAX via HTML attributes, no JS needed -->
  <script src="https://unpkg.com/htmx.org@1.9.12" defer></script>

  <!-- Alpine.js: reactive local state for UI components -->
  <script src="https://unpkg.com/alpinejs@3.x.x/dist/cdn.min.js" defer></script>

  <!-- Phase 2: uncomment when ready for Tailwind styling -->
  <!-- <script src="https://cdn.tailwindcss.com"></script> -->

  <link rel="stylesheet" href="{{ url_for('static', filename='main.css') }}">
</head>
<body>
  <nav><a href="/">Home</a></nav>
  <main>{% block content %}{% endblock %}</main>
</body>
</html>
```

### HTML partial pattern (routes returning fragments)
```python
@app.route("/items", methods=["POST"])
def create_item():
    """POST /items — insert row, return HTML partial for HTMX to inject."""
    title = request.form.get("title", "").strip()
    if not title:
        # 400 so HTMX knows it failed; hx-on::after-request can check event.detail.successful
        return "<p class='error'>Title is required.</p>", 400
    db = get_db()
    db["items"].insert({"title": title, "done": False}, alter=True)
    new_item = list(db["items"].rows_where("title = ?", [title]))[-1]
    # Return only the new <li> fragment — HTMX swaps it into #item-list
    return render_template("_item.html", item=new_item)
```

---

## HTMX Quick Reference

| Attribute      | Meaning                                                   |
|----------------|-----------------------------------------------------------|
| `hx-get/post/delete/patch` | HTTP method + URL to call                  |
| `hx-target`    | CSS selector of element to update                         |
| `hx-swap`      | innerHTML · outerHTML · beforeend · afterbegin · delete   |
| `hx-trigger`   | Event to fire on (default: click or submit)               |
| `hx-indicator` | Show this element while request is in flight              |
| `hx-confirm`   | Browser confirm dialog before request                     |
| `hx-push-url`  | Update browser URL bar after request                      |
| `hx-on::after-request` | JS to run after response (check `event.detail.successful`) |

## Alpine.js Quick Reference

| Directive    | Meaning                                        |
|--------------|------------------------------------------------|
| `x-data`     | Declare reactive component state               |
| `x-show`     | Toggle visibility (element stays in DOM)       |
| `x-if`       | Conditionally render (removes from DOM)        |
| `x-model`    | Two-way bind input ↔ state                     |
| `x-text`     | Set element text from state                    |
| `@click`     | Shorthand for `x-on:click`                     |
| `x-transition` | Animate show/hide                            |
| `$el`        | Reference the root element of the component    |

---

## `requirements.txt`
```
flask>=3.0
sqlite-utils>=3.35
```
`pip install -r requirements.txt`

---

## Phase Checklists

**Phase 1 done when user confirms:**
- [ ] `python app.py` starts without errors
- [ ] All CRUD operations work end-to-end
- [ ] HTMX requests visible in browser DevTools → Network tab
- [ ] `data.db` created and rows persist across restarts
- [ ] No JS console errors

**Phase 2 done when user confirms:**
- [ ] Styling applied consistently across all pages
- [ ] Responsive on mobile viewport
- [ ] Loading states and empty states handled
- [ ] Technical Guide generated
- [ ] User Guidebook generated
