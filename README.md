# The framework in one sentence
Discover every machine identity, map its lineage and owner, measure its real access and behavior, remove unnecessary privilege and long-lived secrets, then continuously govern and detect risk—including for AI agents.

# Lineage graph
Clutch Security's Identity Lineage® Graph is a powerful tool that connects every non-human identity, AI agent, and secret to their origin, providing complete visibility and governance. It records every credential's origin, human owner, storage locations, consumers, and observed call patterns across over 100 integrations. This graph enables security teams to understand the context of each identity, ensuring that risks are actionable and governance is possible at scale.


# 1. NHI attack surfaces
Cloud IAM roles and service principals
API keys, tokens, SSH keys, and certificates
CI/CD pipeline identities
Kubernetes service accounts
SaaS integrations and OAuth grants
Secrets stored in vaults or code repositories
AI agents and their tool-access identities


# 2. Discover identities across the enterprise.
Clutch uses an agentless, API-based integration model to collect NHI-related metadata from connected environments such as cloud platforms, identity providers, source-control systems, Kubernetes, and secret-management tools. Public materials describe support for more than 100 platforms, including AWS, Azure, GCP, Okta, GitHub, and Kubernetes. 

Objective is to answer operational questions like: 

Which identities exist?
Where are their credentials stored?
Which workload or agent uses them?
What can they reach?
Who is accountable for them?
Are they actively used?


# 3. Build an identity lineage graph
The distinctive element of Clutch’s approach is Identity Lineage®: a graph intended to connect each machine identity to its full context rather than treating credentials as isolated records. This includes the identity’s origin, owning workforce identity, storage location, consuming workloads, permissions, reachable assets, and observed behavior. 6 7
Think of it as a chain of accountability:

Developer or deployment process → creates identity → stores secret → workload or AI agent consumes it → identity accesses resources → activity creates risk or business value.

This lineage is the foundation for prioritization. A leaked API key matters far more if it can reach production data, is tied to no accountable owner, and is actively used by several workloads.


# 4. Establish workforce attribution and ownership

For every NHI, Clutch aims to assign a responsible human owner using signals from identity providers, infrastructure-as-code, deployment activity, and other connected systems. 6 5
This enables a practical governance model:

Business owner: accountable for why the identity exists.
Technical owner: accountable for how it is configured and maintained.
Security owner: accountable for policy, monitoring, and exceptions.
Platform owner: accountable for the underlying cloud, SaaS, or DevOps environment.

The important outcome is eliminating “ownerless” credentials. An identity without an accountable owner should be assumed to be higher risk until its purpose is confirmed.


# 5. Assess posture and prioritize risk

Once identities and relationships are visible, the framework evaluates posture: overprivileged access, risky configuration, unmanaged secrets, stale credentials, weak credential hygiene, and access paths to sensitive assets. The platform is described as prioritizing issues based on exposure and potential business impact rather than simply flagging every configuration deviation. 8 9
A useful prioritization lens is:

Privilege: What can the identity do?
Reachability: What sensitive systems or data can it access?
Exposure: Is the credential public, unmanaged, stale, or broadly distributed?
Usage: Is it active, dormant, or behaving unexpectedly?
Accountability: Does it have a valid owner and business purpose?

This prevents the security team from spending time rotating low-impact secrets while a production identity with broad administrative access remains ungoverned.

# 6. Enforce least privilege and improve credential hygiene
Clutch’s model compares permissions granted to permissions actually used, then supports right-sizing of access. The aim is to reduce excessive privilege without breaking critical workloads. 5
The strategic control shift is away from long-lived static credentials—such as API keys or tokens that persist for months or years—and toward short-lived, auto-expiring credentials where the target environment supports them. This reduces the value and usable life of a compromised secret. 10 11
In practice, sequence the remediation carefully:

First, remove unused and orphaned identities.
Next, constrain high-risk, overprivileged identities.
Then, migrate high-value workloads to short-lived or federated authentication.
Finally, automate lifecycle controls in CI/CD and identity processes.

# 7. Govern full identity lifecycle
The framework applies controls across the NHI lifecycle: creation, approval, usage, review, rotation, ownership transfer, and decommissioning. A key use case is orphan detection—identifying identities tied to people who have left or changed roles, then initiating deprovisioning across connected systems. 1 5
A mature operating model should require each NHI to have:

A documented purpose and environment classification
A named accountable owner
An approved access profile
A rotation or expiration expectation
A review cadence based on risk
A retirement trigger when the workload, integration, or owner changes


# 8. Detect anomalous NHI behavior in realtime
Clutch also positions behavior monitoring as a core control. It establishes normal patterns for an identity—such as expected API calls, regions, IP ranges, resources, and usage frequency—and detects deviations. An example would be a normally internal workload credential suddenly accessing systems from an unexpected geography or attempting unusual high-privilege operations. 6 10
When anomalous activity is identified, the objective is rapid containment: alert the security team, investigate the lineage and blast radius, revoke or constrain the identity where appropriate, and validate that dependent services remain operational. 


# 9. Extend the model to AI Agents
AI agents introduce a newer NHI challenge: an agent may use machine credentials while making autonomous calls to applications, data sources, tools, and external services. Clutch’s stated AI-security focus is to discover agent runtimes and shadow AI, map their identities and access paths, and apply purpose-specific guardrails. 

For AI agents, the governance question becomes more rigorous:

Which agent is acting, on whose behalf, using which identity, against which resource, under which policy, and with what approved scope?

That model is especially relevant as enterprises adopt MCP-connected tools and delegated OAuth-based access for agents. 15

# 10. Use zero knowledge architecture as a deployment principle.

Clutch describes its architecture as zero knowledge: the platform processes the metadata needed to understand identity relationships while credential material and secrets remain in the customer’s environment. 2 6
This is important for adoption because security teams often resist tools that centralize copies of secrets. Still, validate the exact data flows, API permissions, retention practices, encryption controls, and integration boundaries in a technical assessment before deployment.

