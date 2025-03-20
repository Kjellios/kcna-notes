# **Best Practices**

Cloud Native Architecture evolved from addressing the shortcomings of traditional **monolithic applications**. Adopting best practices built on these lessons leads to improved availability, scalability, efficiency, and reliability.

## **Problems with Monolithic Architecture**

**Characteristics:**
- **Tightly Coupled**  
  - A single change can break unrelated parts.
- **Hard to Manage & Scale**  
  - Complexity increases rapidly with growth.

**Example:**
- **Web server (Apache/Nginx)** installed directly onto the OS using **apt/yum**.
- **Business logic (PHP/Java)** tightly integrated within the web server itself.
- **Data layers (ODBC)** with shared libraries and dependencies.

**Resulting Issues:**
- **Dependency Hell**: Shared resources/libraries cause widespread impact from minor changes.
- **Downtime Risk**: Extensive manual testing required before updates.
- **Limited Scalability**: Manual configurations limit rapid scaling.

---

## **Cloud Native Approach: Microservices**

**Key Benefits:**
- **Decoupling**: Individual components are isolated, reducing risk.
- **Independent Scalability**: Each microservice scales according to its own demand.
- **Simplified Management**: Teams manage independent services separately.

**Practical Example:**
- **Frontend Services:**  
  - Main webpage → one microservice (Apache, port 443).  
  - Online store → separate microservice (Nginx, port 443), isolated via networking.
- **Networking Isolation:**  
  - Each microservice independently manages network settings (ports, DNS).
- **Flexible Data Layer:**  
  - Dedicated or shared databases per service (e.g., etcd for Kubernetes).

---

## **Core Attributes of Cloud Native Design**

*(Mnemonic: RAOO – "Racoons Are Often Observant")*

| Attribute      | Definition & Examples                                                     |
|----------------|---------------------------------------------------------------------------|
| **Resiliency** | System withstands failures (e.g., Kubernetes replica sets).               |
| **Agility**    | Rapid development via microservices, automation, CI/CD pipelines.         |
| **Operability**| Easy deployment and management using IaC (Terraform, Ansible).            |
| **Observability**| Visibility through logging/metrics/tracing (Prometheus, Grafana, Jaeger).|

---

## **Essential Cloud Native Practices**

### **1. Self-Healing & Resilience**
- Designed for failure recovery.
- **Kubernetes:** Automatically maintains desired replica counts.

### **2. Automation**
- Eliminates manual tasks; speeds deployments.
- Tools: **Ansible** (KubeSpray), **Terraform** (IaC).

### **3. CI/CD (Continuous Integration & Continuous Delivery)**
- **CI:** Frequent merges, automated testing (unit/integration tests).
- **CD:** Automated readiness for deployment (manual trigger to deploy).
- **Continuous Deployment** *(less common)*: Automated deployment without manual triggers.
- **Exam Tip:** CI/CD usually means **Continuous Delivery**.

### **4. Secure by Default (Zero Trust Model)**
- Security integrated from the start.
- **Zero Trust:** "Never trust, always verify."
- **Least Privilege** reduces potential attack surface.
- Kubernetes communication secured by default (via `kubeadm`).

### **5. Speed, Efficiency, & Cost Savings**
- Automatic scaling for temporary demand spikes (e.g., Interflora on holidays).
- **Serverless architecture** scales dynamically, including down to zero, reducing cost.

### **6. Cloud Native Service Discovery**
- Automatic discovery without manual configuration.
- **Kubernetes** built-in DNS (CoreDNS), environment variables for automated discovery.

---

## **Four Key Pillars of Cloud Native Architecture**

*(Mnemonic: "Morning Coffee Delivers Caffeine Delight")*

| Pillar                 | Explanation & Benefits                                           |
|------------------------|------------------------------------------------------------------|
| **Microservices**      | Independent, scalable components                                 |
| **Containerization**   | Application + dependencies encapsulated                          |
| **DevOps Culture**     | Collaborative integration of development & operations teams      |
| **Continuous Delivery**| Automated build/test/release processes                           |

---

## **Autoscaling Overview**

### **Scaling Types:**
- **Horizontal:** Adding/removing resources (HPA in Kubernetes).
- **Vertical:** Adjusting resource allocation (VPA).

### **Autoscaling Methods:**
- **Reactive:** Triggered by real-time metrics.
- **Scheduled:** Planned spikes in demand.
- **Predictive:** ML-based proactive scaling.

### **Kubernetes Autoscaling Tools:**
- **Horizontal Pod Autoscaler (HPA)**: Adjust pod replicas.
- **Vertical Pod Autoscaler (VPA)**: Adjust pod resources.
- **Cluster Autoscaler:** Add/remove Kubernetes nodes based on workloads.
- **KEDA (Kubernetes Event-Driven Autoscaler)**: Event-driven scaling, includes scale-to-zero.

---

## **Importance of Following Best Practices**
Adopting these practices ensures:
- **Resiliency:** Minimizes downtime, automatic recovery.
- **Agility:** Quick response to changes.
- **Operability:** Simplified management through automation.
- **Observability:** Quick diagnostics and visibility.
- **Cost-effectiveness:** Efficient resource use reduces expenses.