# Cloud Native Core Principles

Cloud Native isn’t only about tools—it’s guided by core principles to ensure systems are flexible, scalable, resilient, and maintainable.

---

## 1. Design for Automation
Minimizes human intervention and reduces error rates.

- **Infrastructure as Code (IaC):** Versioned infrastructure (Terraform, CloudFormation).
- **CI/CD Pipelines:** Automated testing/deployment (Jenkins, GitHub Actions, ArgoCD).
- **Automated Deployments:** Frequent and predictable updates.

**KCNA Reminder:** CI/CD typically refers to **Continuous Delivery**.

---

## 2. Loosely Coupled Architecture (Microservices)
Components have clearly defined interfaces, minimizing dependencies.

- Independent evolution and safer updates.
- Fault isolation—one failure doesn't crash everything.
- Practical: Frontend (React) → API Gateway → Independent backend services.

---

## 3. Resilience & Fault Tolerance (Self-Healing)
Systems assume failures happen and handle them gracefully.

- **Redundancy:** Multiple instances in multiple locations.
- **Self-Healing:** Automatic recovery.
- **Graceful Degradation:** Reduced performance vs. complete outage.
- **Example:** Kubernetes auto-recovers crashed pods.

---

## 4. Observability (Logging, Metrics, Tracing)
Ensures internal system states are clearly visible.

- **Logging:** Fluentd, Elastic Stack, Loki.
- **Metrics:** Prometheus, Grafana.
- **Tracing:** Jaeger, OpenTelemetry.
- Crucial for rapid troubleshooting and performance optimization.

---

## 5. Scalability
Easy adjustment of resources to changing demands.

- **Horizontal Scaling:** Adding/removing instances (HPA).
- **Vertical Scaling:** Adjusting resources in existing instances (VPA).
- **Advanced Scaling:** Predictive (ML-driven) or scheduled (planned spikes).

---

## 6. Security by Default (Zero Trust Model)
Integrated security; "never trust, always verify."

- **Least Privilege:** Minimal permissions.
- **Mutual Authentication:** Verify all internal/external entities.
- **Secure Channels:** TLS encryption internally and externally (default in Kubernetes via `kubeadm`).

---

## 7. Declarative Configuration
Desired states defined clearly and maintained automatically.

| Imperative (Old)        | Declarative (Cloud Native)           |
|-------------------------|--------------------------------------|
| Manual provisioning     | Automated, defined infrastructure (IaC) |
| Manual updates/patches  | Automated updates                    |
| Manual deployment steps | GitOps/CD pipelines                  |

- Kubernetes constantly reconciles state from manifests.

---

## 8. Service Discovery
Automatic rather than manual service configuration.

| Traditional                          | Cloud Native (Automated Discovery) |
|--------------------------------------|------------------------------------|
| Manual/hard-coded addresses          | Automatic discovery via DNS/env variables |
| Frequent manual updates              | Auto-update on changes             |

- Kubernetes built-in service discovery (CoreDNS).

---

## 9. Portability & Open Standards
Avoid vendor lock-in through open standards.

- **OCI (Open Container Initiative):** Standardized container formats (runC, containerd).
- **CNI (Container Network Interface):** Standard networking plugins.
- **CRI (Container Runtime Interface):** Standard container runtimes (containerd, cri-o).
- **CSI (Container Storage Interface):** Standard storage solutions (Rook, Portworx).

---

## Key Takeaways (Summary):
Cloud Native principles promote architectures that are:

- Automated & manageable.
- Loosely coupled for safer evolution.
- Resilient & fault-tolerant.
- Observable for rapid troubleshooting.
- Easily scalable.
- Secure by design.
- Declarative for consistency.
- Self-discovering services.
- Portable & vendor-neutral.
