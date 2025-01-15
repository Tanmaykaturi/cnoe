# This folder contains artifacts and instructions for spinnaker-type pipelines such as github-triggered and webhook-triggered deployments

The set-up is in srini-strix. Argo-events is setup in argo-events, argo-workflows in argo and argocd in argocd namespaces.

Document link: https://docs.google.com/document/d/1BVMmq7AV0MPmIREjYv2_gIyJaapM2ransW9EszBxw1w/edit?tab=t.0

Webhook strigger command:
```curl -vvv -d '{"message":"test"}' https://webhook-events.srini-striks.opsmx.co/webhook -H "content-type: application/json"```


TODO: pod-logs are not showing up in sensor-created workflow pods. Looks like authentication is the issue?
