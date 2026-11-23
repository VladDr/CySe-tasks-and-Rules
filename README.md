# CySe-tasks-and-Rules
this is my Python-based detection rules repo (rules in YAML, a small engine that checks log events against them, and tests).
Cyber Security Rules (Python)

A small, defensive starter project: write detection rules in YAML and
check log events against them with Python.

## How it works

- `rules.yml` – your detection rules (one entry per rule)
- `engine.py` – loads the rules and matches them against events
- `test_engine.py` – tests so you can trust your rules

## Quick start

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python engine.py                 # runs the built-in demo events
pytest                           # runs the tests
```

## Rule format

```yaml
- id: R001
  title: Failed SSH login
  severity: medium
  field: message
  match: contains        # contains | equals | regex
  value: "Failed password"
```

## Adding a rule

1. Add a new entry to `rules.yml` with a unique `id`.
2. Add a test in `test_engine.py` with one event that should match and one that should not.
3. Run `pytest`.

## Ideas for next steps

- Read real log files (auth.log, Windows event exports as JSON)
- Support several conditions per rule (AND / OR)
- Map rules to MITRE ATT&CK technique IDs
- Add a CLI: `python engine.py --rules rules.yml --logs auth.json`

## License

MIT
