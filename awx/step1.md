
# Prereqs

First lets start with the quick prereqs, we will need a default stoarge class
for the stateful sets to store their data.

```bash
cat <<EOF | kubectl apply -f -
apiVersion: storage.k8s.io/v1
kind: StorageClass
metadata:
  name: local-storage
  annotations:
    "storageclass.kubernetes.io/is-default-class":"true"
provisioner: kubernetes.io/no-provisioner
volumeBindingMode: WaitForFirstConsumer
EOF
```
{{execute}}
