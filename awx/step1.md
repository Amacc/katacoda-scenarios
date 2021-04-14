# Installing the Operator

Ansible is managed in kubernetes via the ansible operator.

Lets start with an installation into kubernetes.

`kubectl apply -f https://raw.githubusercontent.com/ansible/awx-operator/devel/deploy/awx-operator.yaml`{{execute}}


Now lets create an AWX resource

```bash
cat <<EOF | kubectl apply -f -
apiVersion: awx.ansible.com/v1beta1
kind: AWX
metadata:
  name: awx
EOF
```{{execute}}
