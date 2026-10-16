# Lab 43 — Package-Once Identity

## Step 1 — Steps

Package-Once Workflow:

1. Run a successful verify stage.
2. Package the application JAR exactly once in CI.
3. Generate a SHA-256 checksum for the packaged JAR.
4. Write checksum output to a file named `SHA256SUMS`.
5. Record the associated Git commit using `GITHUB_SHA`.
6. Store build metadata alongside the artifact.
7. Upload the JAR as a CI artifact.
8. Upload `SHA256SUMS` as a CI artifact.
9. Reference the same packaged artifact in later deployment activities.
10. Do not rebuild the application during promotion or deployment.

Artifact Identity Components:

- JAR file
- SHA256 checksum
- GITHUB_SHA commit identifier
- CI build record

## Step 2 — Check the reference

Promotion Rule:

- Lab 44 promotes the artifact identity created by CI.
- The deployed artifact should be the same artifact packaged during CI.
- Rebuilding the application during deployment creates a different artifact and breaks traceability.
- Checksum verification helps prove artifact integrity across environments.
- Commit-to-artifact linkage should remain intact from build through deployment.

## Step 3 — Example lines

Example `SHA256SUMS` file (synthetic values):

```text
9a8b7c6d5e4f3a2109876543210abcdef1234567890abcdef1234567890abcd  crm-api-1.0.0.jar
``
