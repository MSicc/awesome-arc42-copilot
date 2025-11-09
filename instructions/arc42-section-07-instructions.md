# arc42 Section 7: Deployment View - Specific Instructions

## Section Purpose

**Why this section exists:**
Section 7 documents the technical infrastructure and how software building blocks are mapped to hardware/infrastructure elements. It shows where components run and how they're deployed.

**Value for stakeholders:**
- Shows physical/virtual infrastructure
- Documents deployment strategy
- Maps software to hardware/cloud resources
- Explains runtime environment configuration
- Critical for operations and DevOps teams
- Answers: Where do components run? How are they deployed? What's the infrastructure?

**Key insight:** Focus on technically relevant deployment aspects. Skip if deployment is trivial or obvious.

## Mandatory Content (ESSENTIAL)

### What MUST be included:

#### Infrastructure Overview
- **Infrastructure elements** (servers, containers, networks, storage)
- **Mapping** of building blocks (Section 5) to infrastructure
- **Communication channels** between infrastructure elements
- **Technology/protocols** used for deployment

**Note:** For cloud deployments: regions, availability zones, services used.

### When Section 7 Can Be Empty:
- Desktop applications with standard installation
- Simple web applications (standard 3-tier)
- No special infrastructure requirements
- Deployment is obvious from technology stack

## Lean Variant (Minimum Viable Documentation)

### Format:
Simple deployment diagram + table

### Minimum Content:
- One deployment diagram showing main infrastructure nodes
- Simple table mapping components to infrastructure

### Example:

```
[Load Balancer] --> [App Server 1] --> [Database]
                --> [App Server 2] ──┘
```

| Infrastructure Node | Hosted Components | Technology |
|--------------------|------------------|-----------|
| Load Balancer | Traffic distribution | AWS ELB |
| App Server 1/2 | UI Layer, Search Engine | Kubernetes pods |
| Database | Product Catalog data | AWS RDS PostgreSQL |

## Thorough Variant (Complete Version)

### Structure:

#### Infrastructure Level 1
[Highest abstraction - data centers, cloud regions, networks]

**Diagram:** Physical/cloud infrastructure overview
**Description:** Regions, zones, networks, security boundaries

#### Infrastructure Level 2
[Refinement - servers, containers, services within Level 1]

**For each infrastructure node:**

##### Node: <n>

**Technical Description:**
- Hardware specifications (CPU, RAM, storage)
- Operating system
- Virtualization/containerization technology
- Network configuration

**Hosted Building Blocks:**
[Which software components from Section 5 run here]

**Quality Attributes:**
- Performance characteristics
- Availability/redundancy
- Scalability approach
- Security measures

**Deployment Process:**
- How software is deployed to this node
- Deployment tools/automation
- Configuration management

**Communication Channels:**
[How this node communicates with others]

### Multiple Environments:
Document differences between:
- Development
- Testing/Staging
- Production

## Output Format

```markdown
# 7. Deployment View

## Overview
[1-2 paragraphs explaining infrastructure approach and deployment strategy]

## Infrastructure Level 1: Overall Infrastructure

### Deployment Diagram
![Infrastructure Overview](./diagrams/deployment-overview.png)

**Legend:**
- [Server] = Physical/virtual server
- <Container> = Container/pod
- {Database} = Database instance
- === = Network connection

### Infrastructure Description
[Describe cloud regions, data centers, network zones, security boundaries]

## Infrastructure Level 2: Detailed Nodes

### Node: <n>

**Description:**
[What this node is - server, container cluster, database, etc.]

**Technical Specifications:**
- **Type:** [Physical server / VM / Container / Cloud service]
- **Compute:** [CPU, RAM specifications]
- **Storage:** [Type and capacity]
- **OS:** [Operating system and version]
- **Location:** [Data center, region, availability zone]

**Hosted Components:**
| Building Block | Version | Configuration |
|---------------|---------|---------------|
| <Component from Section 5> | <Version> | <Key config> |

**Quality Attributes:**
- **Performance:** <Capacity, response time>
- **Availability:** <Redundancy, failover>
- **Scalability:** <Horizontal/vertical scaling approach>
- **Security:** <Firewall, access control, encryption>

**Deployment:**
- **Method:** [CI/CD pipeline, manual, automated scripts]
- **Tools:** [Kubernetes, Ansible, Terraform, etc.]
- **Frequency:** [Continuous, daily, weekly]

**Communication Channels:**
| Target Node | Protocol | Port | Purpose |
|------------|----------|------|---------|
| <Other node> | HTTPS | 443 | API calls |
| <Database> | PostgreSQL | 5432 | Data access |

---

### Node: <n>
[Repeat structure for each node]

## Multiple Environments

### Production
[Specific configuration for production]
- Nodes: 3x App Servers, 1x Database (with standby)
- Scaling: Auto-scaling 3-10 instances
- Monitoring: Prometheus + Grafana

### Staging
[Differences from production]
- Nodes: 1x App Server, 1x Database
- Reduced capacity for cost savings

### Development
[Local development setup]
- Docker Compose with all services
- Local database
```

## Common Mistakes to Avoid

### ❌ Not Allowed:
1. **Over-documenting trivial deployments** - Skip if obvious
2. **Missing mapping to building blocks** - Must link to Section 5
3. **No environment differences** - Document dev/test/prod variations
4. **Ignoring cloud services** - Document cloud provider services used
5. **Missing network/security aspects** - Firewall rules, VPNs, zones
6. **No deployment process** - How software gets deployed
7. **Outdated diagrams** - Keep synchronized with actual infrastructure
8. **Too much detail** - Stay at infrastructure level, not server config
9. **No scalability information** - How does system scale?
10. **Missing communication channels** - How nodes communicate

### ✅ Desired:
1. **Clear infrastructure diagram** - Shows all nodes
2. **Mapping to building blocks** - Links Section 5 to Section 7
3. **Environment differences documented** - Dev, test, production
4. **Cloud services explicit** - AWS/Azure/GCP services named
5. **Deployment automation described** - CI/CD, tools
6. **Network topology shown** - Security zones, VPNs
7. **Scalability approach clear** - Horizontal/vertical scaling
8. **Quality attributes per node** - Performance, availability
9. **Current and accurate** - Matches actual infrastructure
10. **Appropriate abstraction** - Not too detailed, not too vague

## Integration with Other Sections

### Input from Other Sections:
- **Section 5:** Building blocks that need deployment
- **Section 6:** Runtime scenarios may influence deployment
- **Section 10:** Quality requirements drive infrastructure decisions

### Output for Other Sections:
- **Section 11:** Infrastructure risks and limitations

### Critical Consistency:
- **Section 5 ↔ Section 7:** Every deployable building block must map to infrastructure
- Building blocks in Section 5 must run somewhere in Section 7

## Validation Criteria

- [ ] All deployable building blocks (Section 5) mapped to infrastructure
- [ ] Infrastructure diagram present and clear
- [ ] Technology specifications documented
- [ ] Communication channels described
- [ ] Deployment process explained
- [ ] Multiple environments documented (if applicable)
- [ ] Cloud services explicitly named (if applicable)
- [ ] Scalability approach described
- [ ] Security zones/boundaries shown
- [ ] Quality attributes per node documented

## Official arc42 Tips for Section 7

**Tip 7-1:** Show infrastructure and mapping
- Document technical infrastructure
- Map building blocks to infrastructure nodes
- Show communication channels

**Tip 7-2:** Document multiple environments
- Production, staging, development differ
- Explain key differences
- May use separate diagrams

**Tip 7-3:** Include deployment process
- How software gets deployed
- Automation tools used
- CI/CD pipeline overview

**Tip 7-4:** Consider cloud infrastructure
- Cloud services are infrastructure too
- AWS S3, Lambda, RDS are infrastructure nodes
- Document cloud-specific aspects

## Cloud Deployment Specifics

### AWS Example Elements:
- Regions and Availability Zones
- VPC, Subnets, Security Groups
- EC2 instances / ECS containers / Lambda functions
- RDS databases
- S3 storage
- CloudFront CDN
- Route53 DNS
- Load Balancers (ALB/NLB)

### Azure Example Elements:
- Regions and Availability Zones
- Resource Groups, Virtual Networks
- Virtual Machines / Container Instances / Functions
- SQL Database / Cosmos DB
- Blob Storage
- Application Gateway
- Traffic Manager

### Kubernetes Example:
- Clusters and Namespaces
- Nodes (worker nodes)
- Pods (containers)
- Services (load balancing)
- Ingress (external access)
- Persistent Volumes
- ConfigMaps and Secrets

---
*Based on docs.arc42.org/section-7/ and official arc42 sources*
