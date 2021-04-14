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

With an ingress

```bash
cat <<EOF | kubectl apply -f -
apiVersion: awx.ansible.com/v1beta1
kind: AWX
metadata:
  name: awx-w-ingress
spec:
  tower_ingress_type: Ingress
  tower_hostname: awx.mycompany.com
EOF
```{{execute}}

`[[HOST_IP]]`{{execute}}

With a loadbalancer

```bash
cat <<EOF | kubectl apply -f -
apiVersion: awx.ansible.com/v1beta1
kind: AWX
metadata:
  name: awx-w-loadbalancer
spec:
  tower_ingress_type: LoadBalancer
  tower_loadbalancer_protocol: http
EOF
```{{execute}}
