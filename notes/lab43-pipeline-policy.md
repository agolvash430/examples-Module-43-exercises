# Lab 43 — Define Pipeline Triggers

## Reference

| Event | Verify | Package JAR+SHA |
| --- | --- | --- |
| pull_request | Yes | No (typical) |
| push main | Yes | Yes |
| tag v* | Yes | Yes |

## Step 1 — Matrix

| Event | Verify | Package JAR + SHA | Deploy |
| --- | --- | --- | --- |
| pull_request | Yes | No | No (not yet) |
| push main | Yes | Yes | No (later lab) |
| tag v* | Yes | Yes | No (later lab) |

Job Plan:

### pull_request

- Compile application
- Run tests
- Run verification checks
- Report results to the PR
- Fast feedback only

### push main

- Compile application
- Run tests
- Run verification checks
- Package application JAR
- Generate SHA checksum
- Store build artifacts

### tag v*

- Compile application
- Run tests
- Run verification checks
- Package application JAR
- Generate SHA checksum
- Prepare release artifacts

Deployment Activities:

- Not included in this pre-lab.
- Deployment stages will be introduced in later labs.

## Step 2 — Check the reference

Leadership Expectations:

- Pull requests receive fast feedback.
- Main branch and release tags receive stronger validation gates.
- Artifact generation occurs on main and tagged releases.
- Deployment credentials must never be stored in Git.
- Secrets must be injected through approved secret-management methods.
- Pipeline decisions should be based on verification results, not assumptions.
- Release workflows should be auditable and repeatable.

## Step 3 — CRM identity

CRM test evidence may contain synthetic fixture references such as:

```text
CUS-1001
CUS-1002
lab-request-001
