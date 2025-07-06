# k8s-ansible

Deze repository bevat Ansible playbooks om een k3s-cluster op te zetten op drie Ubuntu-nodes.

## Bestandsoverzicht

- `inventory.ini` – definieert de `controlplane` en `workers`
- `install-k3s.yaml` – installeert k3s op alle nodes
- `addons.yaml` – installeert Cert-Manager, Longhorn en NGINX Ingress via Helm (Helm wordt via de officiële apt-repository geïnstalleerd)
- `roles/k3s` – rol voor installatie van k3s
- `roles/addons` – rol voor installatie van de helm-addons

## Gebruik

1. Installeer benodigde collections:

```bash
ansible-galaxy collection install kubernetes.core community.kubernetes
```

2. Installeer k3s op de nodes:

```bash
ansible-playbook -i inventory.ini install-k3s.yaml
```

De kubeconfig van de controlplane wordt in de map `kubeconfig` op de controller geplaatst.

3. Installeer de addons:

```bash
ansible-playbook -i inventory.ini addons.yaml
```
