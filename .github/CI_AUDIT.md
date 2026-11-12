# CI verification notes

The repository already contains `.github/workflows/ci.yml`. Its pull-request job:

1. Checks out the repository.
2. Installs the locked npm dependencies with `npm ci`.
3. Runs the AVA test suite with `npx ava tests/*.test.js --timeout=1m`.
4. Installs DNSControl and runs `dnscontrol check` when a pull request changes `dnsconfig.js`.

The workflow also supports manual dispatch. Push validation is limited to the `main` branch and selected paths; pull requests trigger the test job.

This document records the existing checks; it does not change the upstream domain-registration rules or the validation logic. A passing CI run confirms the test suite in this checkout, not the correctness of every domain registration or external DNS configuration.
