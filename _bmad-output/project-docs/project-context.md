# Project Context for AI Agents — Odoo 20.0

> Compact rules. Verify against the code before relying on them; this is a structural scan.

## Identity
- Odoo 20.0 (`odoo/release.py`), upstream `odoo/odoo` branch `20.0`.
- Framework in `odoo/`, apps in `addons/`, core module `odoo/addons/base`.

## Rules of thumb
1. **Never edit core to customize.** Create a new addon and extend with `_inherit` (models) and
   `inherit_id` view extensions (XML).
2. A module is a directory with `__manifest__.py` (not `__openerp__.py`). Declare every data file
   in the manifest `data`/`demo` keys and every web file under `assets`.
3. Every new model needs access rights (`security/ir.model.access.csv`) and, if multi-company or
   per-user data, record rules.
4. Dependencies come only from `depends`; avoid circular dependencies. Glue modules are named
   `<a>_<b>` (for example `sale_stock`, `crm_sms`).
5. Frontend is **OWL** under `static/src`; do not add legacy widget code.
6. Localization lives in `l10n_<cc>` modules; keep country logic out of generic apps.
7. Tests live in each module's `tests/`; framework helpers are in `odoo/tests/`.

## Before writing code, read
`skills/odoo-guidelines`, `skills/odoo-web-guidelines`, `skills/odoo-security`, `skills/odoo-review`,
`skills/odoo-git` (commit message conventions).

## Where things are
| Need | Look in |
|---|---|
| ORM behaviour | `odoo/orm/models.py`, `fields_*.py`, `environments.py` |
| Routing / sessions | `odoo/http/` |
| Module loading / migrations | `odoo/modules/` |
| Core models | `odoo/addons/base/models/` |
| Accounting | `addons/account/models/` |
| Web UI | `addons/web/static/src/` |
| CLI | `odoo/cli/` |

## Run (standard)
```bash
pip install -r requirements.txt
./odoo-bin -d <db> -i base --addons-path=addons,odoo/addons
```
(PostgreSQL required. Not executed in this scan.)
