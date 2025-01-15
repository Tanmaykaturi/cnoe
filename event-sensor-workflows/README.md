# Artifacts for github/webhook-triggered pipelines/workflows use-cases

The working set-up is in srini-strix. Argo-events is setup in argo-events, argo-workflows in argo and argocd in argocd namespaces.

Document link: https://docs.google.com/document/d/1BVMmq7AV0MPmIREjYv2_gIyJaapM2ransW9EszBxw1w/edit?tab=t.0
```
alias k="kubectl -n argo-events"
k get eventsources
k get ing
k get sensors
k -n argo get workflowtemplates
```

Webhook-triggers a workflow
1. Webhook trigger :
```curl -vvv -d '{"message":"test"}' https://webhook-events.srini-striks.opsmx.co/webhook -H "content-type: application/json"```
2. URL: https://argo.srini-striks.opsmx.co/event-flow/argo-events
3. we should see a new webhook-pod getting created in argo-events namespace
4. Debugging: tail the logs of the eventsource and sensor pods to see the actions being taken

TODO: pod-logs are not showing up in sensor-created workflow pods. Looks like authentication is the issue?
