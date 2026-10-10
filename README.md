# fareops-gitops

Declarative state of the FareOps cluster. Flux (in the `fareops` k3d cluster)
reconciles this repository; nothing here is applied with `kubectl apply` by hand.

- `clusters/local/` — Flux `GitRepository` + root `Kustomization`, plus the
  `infrastructure` and `apps` Kustomizations
- `infrastructure/` — namespaces, vendored Argo Rollouts, the monitoring stack
  (Prometheus, Alertmanager, Grafana) with memory caps for an 8 GB laptop
- `apps/` — storage, MLflow, fare-api (Argo Rollouts canary), loop-controller,
  trainer Jobs

Writers: the FareOps CI deploy job (image tags), the trainer (MODEL_VERSION on
model registration) and loop-controller (revert on failed canary). Everyone else
should open a pull request.
