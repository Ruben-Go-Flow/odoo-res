# Running Odoo

```bash
(venv) python odoo-bin --addons-path=addons,../<module>/ -d $USER -u <module>
```

- Open http://localhost:8069 in a web browser and login with admin:admin

## Configuration file

```bash
(venv) python odoo-bin -c ../flowcars/flowcars.conf
```

flowcars.conf
```
[options]
db_user=ruben
addons_path=addons,../flowcars/
update=flowcars
```
