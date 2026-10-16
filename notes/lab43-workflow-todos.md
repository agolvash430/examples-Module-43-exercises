# Lab 43 — Fill ci.yml TODOs

## Step 1 — Skeleton

Create: `ci.yml.skeleton`

```yaml
name: CI

on:
  pull_request:
  push:
    branches:
      - main
    tags:
      - 'v*'

jobs*
  verify:
    runs-on: ubuntu-lat*st

    steps:
      - uses: actio*s/checkout@v4

*     - name: Set up Java
        u*es: actions/setup-java@v4
        *ith:
          distribution: temur*n
          java-version: _____

 *    - name: Verify*        run: _____

  package:
   *if: _____
    runs-on: ubuntu-late*t
*   needs: verify

    steps:
     *- uses: actions/checkout@v4

     *- name: Build*Package
        run: ./mvnw -* -DskipTests package

      - name* Upload*Artifact
        uses: actions/upl*ad-artifact@v4
        with:
     *    name: crm-api-jar
          pa*h: _____

      - name: Upload SHA*        uses: actions/upload-art*fact@v4
        with:
          na*e: crm-api-sha
          path: ___*_
