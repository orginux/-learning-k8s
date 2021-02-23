Terminal 1:
```bash
watch -t -d kubectl get horizontalpodautoscalers.autoscaling
```
Terminal 2:
```bash
kubectl run -it load-generator --rm --image=busybox --restart=Never -- /bin/sh -c "while sleep 0.01; do wget -q -O- http://hpa-deploy; done"
```
