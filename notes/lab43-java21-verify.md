# Lab 43 — Plan JDK 21 Verify Job

## Step 1 — Setup

Planned GitHub Actions verify job:

1. Checkout source code
   - uses: actions/checkout@v4

2. Set up Java
   - uses: actions/setup-java@v4
   - distribution: temurin
   - java-version: '21'
   - cache: maven

3. Verify build
   - run: ./mvnw -B clean verify

4. Upload test reports
   - Surefire reports
   - Failsafe reports

5. Archive verification evidence
   - Build logs
   - Test reports
   - Verification artifacts

Job Goals:

- Confirm code compiles.
- Run unit tests.
- Run integration tests.
- Produce repeatable verification results.
- Provide fast feedback to developers.

## Step 2 — Check the reference

Report upload requirements:

```yaml
if: always()
