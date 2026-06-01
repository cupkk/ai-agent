# Open Source Maintenance

This document summarizes the public maintenance model for `ai-agent`.

## Project scope

`ai-agent` is an intelligent work assistant project that brings together task planning, document analysis, meeting-audio processing, calendar synchronization, and WeChat public-account access. The repository includes a Node.js/Express backend, React frontend, integration services, authentication, and security-oriented workflow boundaries.

The repository is intended to be useful for:

- developers building practical assistant workflows around documents, meetings, schedules, and messaging
- maintainers studying integration boundaries between AI services, calendars, and messaging platforms
- contributors improving authentication, file handling, rate limiting, and workflow documentation

## Maintainer responsibilities

The primary maintainer is responsible for:

- reviewing changes to assistant workflows, authentication, uploads, integrations, prompts, and API routes
- triaging issues about implementation status, integration failures, privacy handling, and rate limits
- keeping API keys, OAuth secrets, user files, meeting recordings, calendar data, and local databases out of version control
- documenting implemented vs planned features clearly
- cutting releases when the public baseline, workflow behavior, or integration surface changes materially

## Current maintenance priorities

1. Separate implemented features from planned features in the README and issues.
2. Strengthen tests and examples for task planning, document analysis, and meeting-action extraction.
3. Document safe local configuration for OpenAI/Azure, calendar, and WeChat integrations.
4. Add small issues for frontend polish, backend robustness, and integration boundaries.
5. Keep all secrets in local environment variables or provider-specific secret stores.

## API-credit use boundary

If external AI/API credits are used, they should support open-source development and validation: prompt tests, workflow regression checks, document/action-list examples, issue triage, and documentation. They should not be resold, used for unrelated personal automation, or exposed through a public proxy.
