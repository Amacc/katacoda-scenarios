
# Installing the Operator


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
```
{{execute}}

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
```
{{execute}}


<!-- # `[[HOST_IP]]`{{execute}} -->

Render port 8500: https://[[HOST_SUBDOMAIN]]-8500-[[KATACODA_HOST]].environments.katacoda.com/

Display page allowing user to select port: https://[[HOST_SUBDOMAIN]]-[[KATACODA_HOST]].environments.katacoda.com/


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
