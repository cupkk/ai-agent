# Security Policy

## Supported scope

Security reports are accepted for the current `main` branch.

## Reporting a vulnerability

Please do not open public issues for vulnerabilities, leaked secrets, user files, OAuth tokens, meeting recordings, calendar data, or cloud credentials. Contact the maintainer through the GitHub profile or use GitHub's private vulnerability reporting flow if it is enabled for this repository.

When reporting, include:

- Affected route, integration, service, or workflow
- Reproduction steps
- Expected and actual behavior
- Whether user data or credentials may be exposed

## Data and secret handling

Secrets must stay in environment variables or provider-specific secret stores. User uploads, meeting recordings, calendar data, and local databases must not be committed.
