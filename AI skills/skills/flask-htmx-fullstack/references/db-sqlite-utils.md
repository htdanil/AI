# Database Layer: sqlite-utils (default)

Use this when the Grill step resulted in the **sqlite-utils** choice (the default when
the user doesn't explicitly pick a database layer).

sqlite-utils gives you a Pythonic, no-ORM interface directly over a SQLite file. No
migrations framework, no model classes — just dicts in, dicts out.

---

## `requirements.txt`
```
flask>=3.0
sqlite-utils>=3.35
```
`pip install -r requirements.txt`

---

## `database.py`
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

## `app.py` shell
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

## HTMX-targeted route + DB call
```python
@app.route("/items", methods=["POST"])
def create_item():
    """POST /items — insert row, return HTML partial for HTMX to inject."""
    title = request.form.get("title", "").strip()
    if not title:
        return "<p class='error'>Title is required.</p>", 400
    db = get_db()
    db["items"].insert({"title": title, "done": False}, alter=True)
    new_item = list(db["items"].rows_where("title = ?", [title]))[-1]
    return render_template("_item.html", item=new_item)
```

## Rules specific to sqlite-utils
- Always pass `alter=True` on inserts/upserts so new columns can be added later without
  a migration step.
- sqlite has no native BOOLEAN — store as `0`/`1` (Python `True`/`False` round-trips fine).
- Use `db["table"].rows_where("col = ?", [val])` for parameterized queries — never
  f-string values into SQL.
- `db["table"].update(id, {...})`, `db["table"].delete(id)` for update/delete.
- Only ever targets a local SQLite file — if the user later wants Postgres/MySQL, that
  means switching to SQLAlchemy (`references/db-sqlalchemy.md`), not sqlite-utils.
