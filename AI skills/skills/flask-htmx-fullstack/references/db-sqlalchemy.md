# Database Layer: SQLAlchemy

Use this when the Grill step resulted in the **SQLAlchemy** choice. SQLAlchemy is an ORM:
tables are Python model classes, and the same code works across SQLite, Postgres, and
MySQL by swapping the connection URL and driver.

After confirming SQLAlchemy, you must also have asked (and settled) **which engine**:
- **SQLite** (default when SQLAlchemy is chosen but no engine specified)
- **PostgreSQL**
- **MySQL**
- **Other** — ask the user for the specific engine/driver and adapt the connection URL accordingly

Use `flask_sqlalchemy` (the Flask extension) rather than raw SQLAlchemy — it removes
session/app-context boilerplate and matches Flask idioms.

---

## `requirements.txt` — pick the block matching the chosen engine

**SQLite (default):**
```
flask>=3.0
flask-sqlalchemy>=3.1
```
(No extra driver needed — Python's stdlib `sqlite3` is used under the hood.)

**PostgreSQL:**
```
flask>=3.0
flask-sqlalchemy>=3.1
psycopg[binary]>=3.1
```

**MySQL:**
```
flask>=3.0
flask-sqlalchemy>=3.1
pymysql>=1.1
```

`pip install -r requirements.txt`

---

## `database.py`
```python
# database.py
# Central place for the SQLAlchemy instance and model definitions.
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()

class Item(db.Model):
    """items table — one row per to-do item."""
    __tablename__ = "items"

    id = db.Column(db.Integer, primary_key=True)
    title = db.Column(db.String, nullable=False)
    done = db.Column(db.Boolean, default=False)
    created = db.Column(db.DateTime, server_default=db.func.now())

def init_db():
    """Create all tables at app startup. Safe to call multiple times."""
    db.create_all()
    if not Item.query.first():
        db.session.add(Item(title="Welcome item", done=False))
        db.session.commit()
```

## `app.py` shell — connection URL varies by engine

**SQLite (default):**
```python
# app.py
from flask import Flask, render_template, request
from database import db, init_db, Item

app = Flask(__name__)
app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///data.db"
db.init_app(app)

with app.app_context():
    init_db()

@app.route("/")
def index():
    """GET / — render main page with all rows from DB."""
    items = Item.query.all()
    return render_template("index.html", items=items)

if __name__ == "__main__":
    app.run(debug=True, use_reloader=True)
```

**PostgreSQL** — same shell, just change the URI (read from an env var, never hardcode
credentials):
```python
import os
app.config["SQLALCHEMY_DATABASE_URI"] = os.environ.get(
    "DATABASE_URL", "postgresql+psycopg://user:password@localhost:5432/appdb"
)
```

**MySQL** — same shell, swap the URI:
```python
import os
app.config["SQLALCHEMY_DATABASE_URI"] = os.environ.get(
    "DATABASE_URL", "mysql+pymysql://user:password@localhost:3306/appdb"
)
```

For Postgres/MySQL, tell the user to create a `.env` file (or export `DATABASE_URL`
directly) rather than committing credentials, and mention `python-dotenv` if they want
`.env` file support.

## HTMX-targeted route + DB call
```python
@app.route("/items", methods=["POST"])
def create_item():
    """POST /items — insert row, return HTML partial for HTMX to inject."""
    title = request.form.get("title", "").strip()
    if not title:
        return "<p class='error'>Title is required.</p>", 400
    new_item = Item(title=title, done=False)
    db.session.add(new_item)
    db.session.commit()
    # Return only the new <li> fragment — HTMX swaps it into #item-list
    return render_template("_item.html", item=new_item)
```

## Rules specific to SQLAlchemy
- Define every table as a `db.Model` subclass in `database.py` — never issue raw SQL
  strings unless doing something the ORM genuinely can't express.
- Use `db.session.add(...)` + `db.session.commit()` for writes; `Model.query...` for reads.
- For schema changes after the first working version, prefer `Flask-Migrate` (Alembic)
  over repeatedly calling `db.create_all()`, which only creates missing tables and never
  alters existing ones. For quick prototypes, `db.create_all()` at startup is fine —
  mention the Alembic upgrade path in the Technical Guide.
- Booleans and datetimes map automatically (`db.Boolean`, `db.DateTime`) — no manual
  0/1 or ISO-string conversion needed, unlike sqlite-utils.
- Keep the connection URL out of source code for Postgres/MySQL — use an environment
  variable with a local-SQLite fallback for easy dev setup.
