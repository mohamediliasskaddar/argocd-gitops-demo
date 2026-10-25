## Argo CD GitOps Lab — Tests Performed
> more details, set up instructions etc u can find them here in the [quickstart file ](quickstart.md)

| Test | Action | Expected / Observed Result |
|---|---|---|
| Argo CD Setup | Installed Argo CD on local Minikube | All Argo CD components running |
| Application Deployment | Connected Argo CD to the GitHub repository | Kubernetes Deployment and Service created from `k8s/` manifests |
| Initial Sync | Manually synchronized the application | Flask application deployed successfully |
| Automated Sync | Changed replicas in GitHub and pushed the commit | Argo CD automatically applied the updated configuration |
| Horizontal Scaling | Increased replicas from 1 to 3, then 4 | Kubernetes created additional Pods |
| Kubernetes Self-Healing | Deleted an application Pod | Kubernetes automatically recreated the Pod |
| Argo CD Self-Healing | Manually scaled the Deployment from 4 replicas to 1 | Argo CD restored the desired replica count of 4 |
| Resource Status Monitoring | Inspected Pods, Deployments, Services, and Argo CD status | Verified running Pods and deployment health |

**Environment:** Ubuntu, Docker, Minikube, Kubernetes, Argo CD, GitHub, Python Flask.

**Key takeaway:** Git acts as the source of truth. Argo CD continuously compares Git with the live Kubernetes state and, with automated sync and self-healing enabled, reconciles differences automatically.