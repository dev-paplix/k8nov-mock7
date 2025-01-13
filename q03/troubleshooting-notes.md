1. kubectl set image deployment frontend-deployment nginx=nginx:1.23 -n test
2. kubectl scale --current-replica=2 --replica=4 deployment frontend-deployment -n test
3. kubectl edit service frontend-service -n test # modify the target port to 80
4. kubectl exec deployment frontend-deployment -n test -- curl localhost:80