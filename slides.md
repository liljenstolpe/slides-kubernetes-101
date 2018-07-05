layout: true
background-image: url(photos/Tiger-Composite.jpg)
background-size: cover
background-position: 50% 25%

---
class: middle, center
background-image: url(photos/k8s-sticker.jpg)
background-position: 50% 25%
background-size: cover
image-credit: Photo "k8s Sticker" shared by Joe Beda under a [Creative Commons ( BY ) license](https://creativecommons.org/licenses/by/4.0/)

# Kubernetes 101

.cblock[
Christopher LILJENSTOLPE<br>
CTO, Solutions - [Tigera](https://tigera.io)
]

.image-credit[
{{image-credit}}
]

---

class: column-slide
background-image: url(photos/Tiger-Composite.jpg)
background-size: cover

.column-container[.left-column[
# Recap
## Containers
]
.right-column[
.center[
# "It's the next big thing!"
]
]
]

---

class: column-slide
background-image: url(photos/Tiger-Composite.jpg)
background-size: cover

.column-container[.left-column[
# Recap
## Linux Kernel Features

]
.right-column[
cgroups:

* Resource limiting, tracking, prioritization, and isolation
* CPU, RAM, IO, Networking, etc.
* Developed by Google for over ~10 years
* "nice++"

namespaces:

* Resource visibility and naming isolation
* network, PID, users, mounts
* "chroot++"

cgroups + namespaces = "lightweight virtualization"
]
]

---
class: column-slide
background-image: url(photos/Tiger-Composite.jpg)
background-size: cover

.column-container[.left-column[
# Recap
## User Experience

]
.right-column[
Containers == Docker?

* *Image format:* Upload, download, share, build
* *API:* Automatable create, delete, start, stop
* *Networking*: Good defaults
]
]

---
class: column-slide
background-image: url(photos/Tiger-Composite.jpg)
background-size: cover

.column-container[.left-column[
# Recap
## Excitement

]
.right-column[
Users benefits:

1. Packaging, deployment and reuse
2. Efficiency and overcommit
3. Security

This list is in order

]
]


---
class: column-slide

.column-container[.left-column[
# Recap
## Gaps

]
.right-column[
Dev &rarr; Production

* Multi-machine
* Discovery and Naming
* Scaling
* Multiple users
* Failure tolerance and recovery
* Monitoring
* Logging
* High availability
* Deployment lifecycle
* Load balancing
* etc, etc

]
]


---
class: column-slide

.column-container[.left-column[
# Recap
## Micro-services?

]
.right-column[

 * Split your application into small services that can be reused, remixed and shared.
 * Enables smaller, nimble, decoupled teams and processes.
 * Better tooling enables and encourages microservices.

Not what I'm talking about today.

]
]

---
class: column-slide

.column-container[.left-column[
# Kubernetes
## Defined

]
.right-column[


Kubernetes is ancient Greek for "Helmsman".  Root of the word "Governor", "Cybernetics".

Kubernetes is a "Container Orchestrator" or "Cluster Manager".

* Places containers on nodes
* Recovers automatically from failure
* Basic monitoring, logging, health checking
* Enables containers to find each other.


Key component in *logical infrastructure*

]]

---
class: column-slide

.column-container[.left-column[
# Kubernetes
## Google Grown
]
.right-column[
Based on ideas proven at Google over 10 years

*Everything* at Google runs in a container.

Google launches 2 billion containers per week.

Part of a larger set of tools that make up the internal Google platform.
]]

---
class: column-slide


.column-container[.left-column[
# Kubernetes
## Open Source
]
.right-column[
https://github.com/kubernetes/kubernetes

*Very* active open source project

38k+ stars, 1700+ contributors

Apache 2 licensed

Written in Go

Hosted by the Cloud Native Computing Foundation (CNCF)
]]

???

stats with git shortlog -sn --no-merges | wc

---
class: column-slide

.column-container[.left-column[
# Kubernetes
## Benefits
]
.right-column[
Extend the container goodness across nodes.

Enable operations specialization. Cluster Ops vs. App Ops

Reduce cost to run many things in production.  Enables new ways of building applications.
]]


---
class: column-slide

.column-container[.left-column[
# Design Principles
]
.right-column[
* declarative > imperative
* control loops
* simple > complex
* modularity
* legacy compatible
* network-centric
* labels > hierarchy
* cattle > pets
* open > close
]]

---
class: column-slide

.column-container[.left-column[
# Core Concepts
## Cluster
]
.right-column[.center[
<object type="image/svg+xml" data="diagrams/cluster.svg">
</object>
]]]

---
class: column-slide

.column-container[.left-column[
# Core Concepts
## Pod
]
.right-column[.center[
<object type="image/svg+xml" data="diagrams/pod.svg">
</object>
]]]

---
class: column-slide

.column-container[.left-column[
# Core Concepts
## Labels
]
.right-column[.center[
<object type="image/svg+xml" data="diagrams/labels.svg">
</object>
]]]

---
class: column-slide

.column-container[.left-column[
# Core Concepts
## ReplicaSet
]
.right-column[.center[
<object type="image/svg+xml" data="diagrams/rc.svg">
</object>
]]]

---
class: column-slide

.column-container[.left-column[
# Core Concepts
## ReplicaSet
]
.right-column[.center[
<object type="image/svg+xml" data="diagrams/rc2.svg">
</object>
]]]

---
class: column-slide

.column-container[.left-column[
# Core Concepts
## Service
]
.right-column[.center[
<object type="image/svg+xml" data="diagrams/service.svg">
</object>
]]]

---
class: column-slide

.column-container[.left-column[
# Core Concepts
## Persistent Volumes
]
.right-column[.center[
<object type="image/svg+xml" data="diagrams/pvs.svg">
</object>
]]]

---
class: column-slide

.column-container[.left-column[
# So much more!
]
.right-column[
* **Namespaces**
  * Isolated workspaces for users/projects
* **Ingress**
  * L7 load balancing
* **Deployments**
  * Declarative version updates
* **Jobs**
  * Run to completion
* **Autoscaling**
  * Automatically adjust replica count
* **DaemonSets**
  * Run something on every node (or subset)
]]

---
class: column-slide

.column-container[.left-column[
# So much more!
]
.right-column[
* **Role Based Access Control (RBAC)**
  * Control what users have access to what objects
* **Multiple Schedulers**
* **Flexible Scheduling Constraints**
  * Affinity, anti-affinity, taints, tolerations
* **StatefulSet**
  * Support for long term stateful distributed systems
* **Automatic Cluster Scaling**
  * K8s publishes signals that allow external services to scale the cluster automatically.
* **Cloud Provider Integration**
  * GCP, AWS, Azure, OpenStack, vSphere
* **Network Policy**
  * Network ingress policy
]]

---
class: column-slide

.column-container[.left-column[
# Ecosystem
]
.right-column[
* **Platforms**
  * OpenStack, Deis Workflow
* **Operators**
  * Automatic management of systems via API
  * Integrates using k8s extensions
  * etcd, Prometheus, elasticsearch, memcahced, mongodb, rook, etc.
* **Authentication Providers**
  * Extended via webhook.  OpenID Connect, OAuth 2, LDAP, SAML, etc.
  * Already implemented on GKE and GCE.
* **Helm: Package Manager**
  * Super easy to install applications and systems.
* **Extended Network Policy**
]]

---
class: middle, left
background-image: url(photos/k8s-sticker.jpg)
background-position: 50% 25%
background-size: cover
image-credit: Photo "k8s Sticker" shared by Joe Beda under a [Creative Commons ( BY ) license](https://creativecommons.org/licenses/by/4.0/)

# Thank you!

.cblock[
Christopher LILJENSTOLPE<br>
[@liljenstolpe](https://twitter.com/liljenstolpe) |
[@liljenstolpe](https://github.com/liljenstolpe) | [cdl@tigera.io](mailto:cdl@tigera.io)<br>
https://www.tigera.io<br>
]

.ccblock[
[![Creative Commons License](img/cc-by.png)](http://creativecommons.org/licenses/by/4.0/)<br>
This presentation is a [fork](https://github.com/liljenstolpe/slides-kubernetes-101) by
[@liljenstolpe](https://github.com/liljenstolpe) of [Kubernetes
101](https://github.com/jbeda/k8s-slides) by Joe Beda, and maintains
his [Creative Commons Attribution 4.0 International
License](href="http://creativecommons.org/licenses/by/4.0/) license.
]

.image-credit[
{{image-credit}}
]
