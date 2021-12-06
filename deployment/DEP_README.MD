# Deployment strategies

## Rollback deployment ( Default approach )

To try out the deployment
- change the replicas & image from the hrui_dep_rolling.yaml
- kubectl apply -f hrui_dep_rolling.yaml --record

### To set the image:
kubectl set image deployment.apps/hr-deployment hruicontainer=mtahaelmaghrabi/hrmvc:v8.0

### Check the rollout status
kubectl rollout status deployment.apps/hr-deployment --record

### Check the history
kubectl rollout history deployment.apps/hr-deployment --revision=2

### rolling back to a specific deployment
kubectl rollout undo deployment.apps/hr-deployment
" keep repeating this command will switch between the current version and the previous one"

### to roll back for a specific version use:
kubectl rollout undo deployment.apps/hr-deployment --to-revision=1

****************************************************

## Canary deployment ( 2 versions on the same time )

1. Just create 2 deployment yaml files (stable / canary) with the same label
2. (optional) Add another lable to differentiate between them
3. add the Service with the [selector = the common label]
4. the percentage of the canary deployment is controlled by the replicas of each deployment (stable / canary)
    - 25% canary = (3 stable : 1 canary) replicas
5. hit the load balancer external IP and you will get a random response either from the stable or the canary pods
6. after testing we can just delete the stable version and scale up the canary to be the new stable version

****************************************************

## Blue-Green deployment ( Not for the End-Users / for Internal QA )

- Is to run two identical environments at the same time (Duplicate)
- (blue)  one environment is active and service end users
- (green) the other environment remains idle
- Traffic routed from blue to green when checks pass


### Change the Service's selector to green (imperative)
kubectl set selector svc [service-name] 'role=green'

### using selector
kubectl get all --selector role=green
kubectl get pods --selector role=green
