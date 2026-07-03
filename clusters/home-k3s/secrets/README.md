# home-k3s secrets

This directory only accepts encrypted SOPS YAML and non-secret templates.

Allowed:

- `*.sops.yaml` encrypted with SOPS.
- Non-secret README files.
- Non-secret templates with placeholders only.
- The age public recipient.

Forbidden:

- age private key material.
- SSH private keys.
- plaintext Kubernetes Secret values.
- admin passwords.
- Harbor robot tokens.
- Woodpecker agent secrets.

Current state:

- `agePublicRecipient`: `pending-user-provided`
- `fullyConsumableSecrets`: `false`
- Secrets child Application live sync: blocked until recipient and manual bootstrap secret evidence exist.
