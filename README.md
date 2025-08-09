# K8S Infra Assignment

This repo deploys the SigNoz **k8s-infra** agent to a Kubernetes (k3s) cluster using **Ansible + Helm**, forwarding telemetry to SigNoz running in Docker on TrueNAS.

## Layout
\`\`\`
k8s-infra-ansible/
├─ playbooks/
│  ├─ up.yaml
│  └─ down.yaml
├─ values/
│  ├─ k8s-infra-values.yaml
│  └─ rolldice-values.yaml
├─ inventory/
│  └─ hosts.ini
├─ docs/
│  ├─ screenshots/
│  └─ results.md
└─ README.md
\`\`\`

## Prereqs
- Helm, kubectl, Ansible installed on control host
- \`kubectl\` already points at your cluster
- SigNoz reachable at your OTLP endpoint (edit \`values/k8s-infra-values.yaml\`)

## Deploy
\`\`\`bash
ansible-playbook -i inventory/hosts.ini playbooks/up.yaml
kubectl -n platform get pods
\`\`\`

## Remove
\`\`\`bash
ansible-playbook -i inventory/hosts.ini playbooks/down.yaml
\`\`\`

## Proof
Put screenshots in \`docs/screenshots/\` showing:
- \`helm list -n platform\`
- \`kubectl -n platform get pods\`
- SigNoz UI receiving data
