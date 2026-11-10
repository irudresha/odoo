# Source Tree (annotated)

```
odoo/                      repo root
├── odoo-bin               entry point (python odoo-bin ...)
├── requirements.txt       Python dependencies
├── ruff.toml, setup.cfg   lint / packaging config
├── setup/                 packaging: debian, rpm, docker, win32, iot_box_builder
├── debian/                Debian packaging
├── skills/                Odoo-provided agent skills (see skills/README.md)
├── odoo/                  FRAMEWORK
│   ├── orm/               models.py (~6.6k lines), fields_*.py, environments.py,
│   │                      registry.py, domains.py, query.py, cache.py
│   ├── models/, fields/, api/   public facades over the ORM
│   ├── http/              router, dispatcher, session, stream, response
│   ├── service/           server.py (threaded/gevent/prefork), model RPC
│   ├── modules/           module_graph, loading, migration, db, registry
│   ├── cli/               odoo-bin subcommands
│   ├── tools/             config, convert (XML loader), mail, pdf, translate, ...
│   ├── tests/             test framework (form, case classes, runners)
│   ├── upgrade/, upgrade_code/   upgrade tooling
│   └── addons/
│       ├── base/          mandatory core: res.partner, res.users, ir.* models,
│       │                  ir.ui.view, ir.cron, ir.attachment, ir.qweb, ...
│       └── test_*/        framework test modules
└── addons/                ~648 business addons
    ├── web/               web client (OWL), static/src: core, views, webclient, search, ...
    ├── account, sale, stock, crm, hr*, project*, mrp*, purchase*, ...
    ├── website*, pos_*, payment_*, mail, bus, portal, ...
    └── l10n_*             234 country localizations
```

## `odoo/addons/base/models` (selected)

`res_partner`, `res_users`, `res_company`, `res_currency`, `res_lang`, `ir_model`, `ir_ui_view`,
`ir_ui_menu`, `ir_actions*`, `ir_cron`, `ir_attachment`, `ir_config_parameter`, `ir_sequence`,
`ir_mail_server`, `ir_qweb`, `ir_asset`, `ir_http`, `ir_access`, `res_groups`.

## `addons/account/models` (selected)

`account_move`, `account_move_line`, `account_journal`, `account_tax`, `account_payment`,
`account_bank_statement(_line)`, `account_reconcile_model`, `account_partial_reconcile`,
`account_analytic_*`, `chart_template`, `account_move_send`.

## Web client (`addons/web/static/src`)

`core`, `env.js`, `main.js`, `start.js`, `module_loader.js`, `libs`, `model`, `search`, `views`,
`webclient` (actions, navbar, menus, burger_menu, debug), `public`, `scss`, `owl2`, `service_worker.js`.
