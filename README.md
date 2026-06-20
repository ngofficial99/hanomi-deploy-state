# hanomi-deploy-state

GitOps **desired state** for the Hanomi deploy pipeline. The VM reconcilers clone
this repo and converge to the image digests pinned in `state/<svc>/desired.yaml`.

- `state/<svc>/desired.yaml` — the pinned image digest per service (CI is the only writer).
- `deploy/` — the reconciler scripts + Quadlet templates the VMs run (mirrored from the main repo).

CI (GitHub Actions in the main repo) commits a new digest here on each deploy;
that commit IS the deploy. Rollback = `git revert`.
