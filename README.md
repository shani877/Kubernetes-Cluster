# Kubernetes Dashboard Setup


---

## 📦 Step 1: Deploy Kubernetes Dashboard

Apply the recommended deployment YAML to set up the Kubernetes Dashboard:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.7.0/aio/deploy/recommended.yaml
```

---

## 👤 Step 2: Create Admin User and Service Account

Apply a custom YAML (`dashboard-adminuser.yaml`) to create a ClusterRoleBinding and a ServiceAccount for administrative access:

```bash
kubectl apply -f dashboard-adminuser.yaml
```

## 🔌 Step 3: Expose the Dashboard

To make the dashboard accessible locally, use port forwarding:

```bash
kubectl port-forward svc/kubernetes-dashboard -n kubernetes-dashboard 8080:443 --address=0.0.0.0 &
```

---

## 🔐 Step 4: Generate Access Token

Create a token for the `admin-user`:

```bash
kubectl -n kubernetes-dashboard create token admin-user
```

> Copy and save this token securely. It is used to authenticate on the Dashboard UI.

---

## 🌐 Step 5: Access the Dashboard

Open the following URL in your browser:

```
https://<NODE_IP>:8080
```

> Accept the browser security warning (self-signed cert) and use the previously generated token for login.

---

## 📌 Notes

- Ensure port `8080` is open in your firewall or security group.
- Consider enabling RBAC with least privilege for production environments.
- For persistent exposure, configure an Ingress or a NodePort (not recommended for production without proper security).

---
