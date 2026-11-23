# Security policy

## Reporting a vulnerability

**Please do not open a public issue for a security problem.**

Use GitHub's private vulnerability reporting:

> [**Report a vulnerability**](https://github.com/agileHRI/arise_poc_coraine/security/advisories/new)

That opens a private advisory visible only to the maintainers.

If you cannot use GitHub advisories, open a regular issue saying only that you have a security report
and asking for a contact - no details - and a maintainer will reply with a private channel.

A problem in coraine itself (the broker or its bridges) belongs to coraine:
[report it there](https://github.com/SEAMWARE/coraine/security/advisories/new).

## Scope

This repository is a **local demo**. Its defaults are not meant for a network you do not trust:
coraine runs without authentication, and the database and Grafana use default passwords.
These defaults are documented, not vulnerabilities. Anything else that would put a user of the
demo at risk is in scope.
