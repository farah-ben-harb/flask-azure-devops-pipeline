# Security Policy

## Supported sources of security issues

This repository should never contain live credentials, API keys, or private tokens.

## Reporting a vulnerability

If you find a security problem:

1. Do not open a public issue with exploit details.
2. Describe the problem clearly.
3. Include the affected file or workflow if known.
4. Avoid posting secrets, screenshots of tokens, or full logs.

## Secret handling rules

- Use GitHub Secrets for sensitive CI/CD values
- Use repository variables for non-sensitive configuration
- Never commit real `.env` files
- Rotate any secret that may have been exposed

## Previously exposed SMTP credential

The Alertmanager configuration previously contained an SMTP credential. The
configuration now reads SMTP values from protected Terraform variables and
renders them only on the target VM. The owner of the SMTP account must still
revoke and replace the exposed credential; removing it from the current file
does not remove it from Git history.

