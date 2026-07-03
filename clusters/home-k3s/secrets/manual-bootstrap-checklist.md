# Manual Bootstrap Credential Checklist

This file contains only non-secret instructions. Do not paste real passwords, tokens, private keys, or Secret data into this repository or into assistant chat.

## Rules

- Create real values outside Codex, using a password manager or local secure tooling.
- Store only SOPS-encrypted files, non-secret templates, public recipients, and evidence without values in Git.
- Keep `recipient_pending` active until an age public recipient and manual bootstrap evidence exist.
- Do not live-sync a secrets child Application while `recipient_pending` blocks `secrets_child_app_live_sync`.

## Handles

- `gitea-admin-credentials` in namespace `gitea`; keys `username`, `password`; owner `gitea-service-baseline`.
- `harbor-admin-credentials` in namespace `harbor`; keys `username`, `password`; owner `harbor-registry-baseline`.
- `harbor-robot-woodpecker` in namespace `harbor`; keys `username`, `token`; owner `harbor-registry-baseline`.
- `woodpecker-registry-harbor` in namespace `woodpecker`; keys `username`, `password`; owner `woodpecker-ci-baseline`.
- `woodpecker-agent-secret` in namespace `woodpecker`; key `WOODPECKER_AGENT_SECRET`; owner `woodpecker-ci-baseline`.
- `gitea-woodpecker-webhook` in namespace `woodpecker`; key `shared-secret`; owner `woodpecker-ci-baseline`.
- `gitops-write-credentials` in namespace `woodpecker`; keys `username`, `token`; owner `woodpecker-ci-baseline`.

## Source And Projection Rules

- `harbor-robot-woodpecker` is the Harbor source identity for CI registry access.
- `woodpecker-registry-harbor` is the Woodpecker consumer projection of that Harbor robot identity.
- The Woodpecker projection must reuse the Harbor robot username and store the Harbor robot token in the consumer `password` key expected by registry clients.
- Do not create an unrelated registry credential for `woodpecker-registry-harbor`.
- A Woodpecker registry smoke must prove the projected credential can authenticate to Harbor before retiring the previous robot value.

## Evidence Without Values

For each manually created or rotated credential, record only:

- handle name
- namespace
- creation or rotation timestamp
- verification command or smoke result
- operator initials or local evidence reference
- no secret value, token, password, private key, or Secret data
