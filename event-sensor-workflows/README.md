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
### Debugging:
Each eventsource and sensor has its own pod for handling the events and processing them. Tail the logs of the eventsource and sensor pods to see the actions being taken

URL: https://argo.srini-striks.opsmx.co/event-flow/argo-events

## Webhook demo: Objective: A workflow can be trigged via a workflow
1. webhook eventsource is set up for receving a trigger
2. Webhook trigger :
```curl -vvv -d '{"message":"test"}' https://webhook-events.srini-striks.opsmx.co/webhook -H "content-type: application/json"```
3. we should see a new webhook-pod getting created in argo-events namespace

## github demo:  Objective: A workflow can be trigged via a git push in any repo in an organization
1. opsmxgitpush eventsource is set up for receving a trigger for a push to main branch of cnoe and ssdgate repos
2. Make a change in opsms/cnoe repo 
3. See the workflow triggered
4. Click on the workflow pod (green circle), click on it again, go to "input/outputs" tab
5. We should see message: cnoe which is the repo name. If we do the same with ssdgate, we can see that repo name.

TODO: pod-logs are not showing up in sensor-created workflow pods. Looks like authentication is the issue?
