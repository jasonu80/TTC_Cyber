# Exploit Automation Framework

## Project Overview

The Exploit Automation Framework is an educational cybersecurity project for a first-year second-semester IT student. It teaches controlled penetration testing automation in Python using a concept-first, procedure-driven workflow.

This README is aligned with `AGENTS.md` and `procedures.md` in this folder. It focuses on safe lab execution, repeatable engineering standards, and clear evidence-based learning outcomes.

## Workflow Stages

The framework follows a 6-stage pipeline:

1. **Target Ingestion and Validation**  
   Validate IP format and target reachability before any exploit logic.
2. **Automated Reconnaissance**  
   Identify open ports, services, and versions.
3. **Vulnerability Correlation**  
   Map discovered services to known vulnerabilities and prioritise high-impact findings.
4. **Exploit Staging**  
   Prepare Metasploit modules with correct parameters (`RHOSTS`, `RPORT`, `LHOST`, payload).
5. **Execution and Verification**  
   Run controlled actions with timeout handling and explicit success/failure logging.
6. **Automated Reporting**  
   Produce clear output summarising tested targets, findings, outcomes, and remediation advice.

## Project Layout

Key project paths:

- `src/main.py` - CLI entry point
- `src/core/msf_wrapper.py` - Metasploit command wrapper
- `src/core/payload_gen.py` - msfvenom wrapper
- `src/core/session_manager.py` - session tracking and persistence
- `src/modules/` - scanner, exploitation, and integration modules
- `src/utils/` - config, logging, and reporting helpers
- `tests/test_framework.py` - core automated tests
- `procedures.md` - step-by-step implementation guide

## Environment and Setup

Minimum environment:

- Kali Linux (or equivalent lab system)
- Python 3.8+
- Metasploit Framework (`msfconsole`, `msfvenom`)
- 8 GB RAM recommended
- Isolated test lab network (no production target usage)

Bootstrap:

```bash
python3 -m venv venv && source venv/bin/activate
pip install -r requirements.txt
pip install pytest black flake8 mypy
```

Tool checks:

```bash
python3 --version
msfconsole --version
msfvenom --version
```

Run the framework:

```bash
python -m src.main
```

## Testing and Quality Gates

Run these before considering work complete:

```bash
black src/ tests/
flake8 src/ tests/
mypy src/
pytest -v
```

Optional checks:

```bash
pytest tests/test_framework.py -v
pytest --cov=src --cov-report=html
```

A task is not complete unless all required checks pass.

## Code Style Guidelines

- Follow PEP 8.
- Use type hints on all function signatures.
- Add concise docstrings (`Args`, `Returns`) for public functions.
- Naming: classes in CamelCase, functions/variables in snake_case, constants in SCREAMING_SNAKE_CASE.
- Import order: standard library, third-party, local modules.
- For subprocess usage, handle timeouts and non-zero return codes safely.

## Student Procedure Expectations

When implementing or documenting work, follow this response pattern:

1. Explain the concept and why it matters.
2. Provide small, ordered implementation steps.
3. Include self-check questions.
4. Capture evidence (screenshots, command output, commit history).

Use `procedures.md` as the primary source for weekly sequence and deliverables.

## Security and Legal Constraints

This framework is for authorised security testing only.

- Test only systems you own or have explicit written permission to test.
- Do not scan or exploit live/production systems without documented approval.
- Keep testing inside isolated lab environments.
- Do not commit sensitive artifacts (`.env`, real session data, generated payload binaries, private logs).
- Never bypass scope validation and reporting requirements.

Unauthorised access to computer systems is illegal and unethical. Follow Australian law and organisational policy at all times.

## Learning Outcome

This project develops practical foundations in secure automation, tool integration, testing discipline, and professional reporting expected in entry-level cybersecurity work.
