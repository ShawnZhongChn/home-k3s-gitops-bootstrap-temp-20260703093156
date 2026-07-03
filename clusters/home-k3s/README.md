# home-k3s GitOps source bundle

This bundle is the clean GitOps source layout for the home k3s platform.

Current readiness:

- Source bundle: ready for review.
- Live Argo CD bootstrap: blocked until `gitops_repo_url` is provided.
- Fully consumable SOPS secrets: blocked until an age public recipient and manual bootstrap secret evidence exist.

Do not store credentials, private keys, tokens, or plaintext Secret values in this tree.
