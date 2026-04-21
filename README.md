# AWS System Design — Self-Study Plan

A 12-week self-study plan for mid-to-senior engineers who already know AWS basics (EC2, VPC, S3, IAM, Docker, Kubernetes, Terraform) and want to get better at **designing systems on AWS** — not just passing SAA-C03.

Every resource linked here is free.

- **Goal:** Design a production-grade system on AWS from scratch and justify every component choice.
- **Duration:** ~12 weeks at ~6–8 hrs/week. Compressible to 8 weeks if focused.
- **Approach:** Official AWS docs and whitepapers, curated GitHub archives, real-world case studies, and hands-on labs.

## Table of Contents

- [How to Use This Plan](#how-to-use-this-plan)
- [Phase 0 — Foundations](#phase-0--foundations-week-0-skip-if-solid)
- [Phase 1 — AWS Mental Model & Well-Architected](#phase-1--the-aws-mental-model--well-architected-framework-week-1)
- [Phase 2 — Amazon Builders' Library](#phase-2--the-amazon-builders-library-weeks-23)
- [Phase 3 — Reference Architectures & Design Patterns](#phase-3--aws-reference-architectures--design-patterns-weeks-45)
- [Phase 4 — Service Deep-Dives](#phase-4--aws-service-deep-dives-that-matter-for-design-weeks-67)
- [Phase 5 — Hands-On Workshops](#phase-5--hands-on-workshops-weeks-89)
- [Phase 6 — Real-World Case Studies](#phase-6--real-world-case-studies-week-10)
- [Phase 7 — Interview-Style Design Drills](#phase-7--interview-style-design-drills-week-11)
- [Phase 8 — Capstone & Continuous Learning](#phase-8--capstone--continuous-learning-week-12)
- [Consolidated Resource Index](#consolidated-resource-index)
- [Time & Commitment Summary](#time--commitment-summary)
- [Ground Rules](#ground-rules)
- [Contributing](#contributing)
- [License](#license)

## How to Use This Plan

Each phase has three layers:

1. **Read** — whitepapers, blog posts, GitHub notes
2. **Watch** — free YouTube and re:Invent talks
3. **Build** — hands-on workshops or a small project of your own

Do not skip the Build layer. Design sticks when you have actually wired it up in an AWS account. Free Tier covers roughly 90% of what is below.

At the end of each phase, write a one-page design note explaining a system you would design using that phase's concepts. Keep these notes in a private repo — they become a personal design-interview reference.

## Phase 0 — Foundations (Week 0, skip if solid)

Prerequisites. If any of these feel fuzzy, spend a few days here first.

| Topic | Resource |
|---|---|
| General system design primer | https://github.com/donnemartin/system-design-primer — read the [scaling AWS](https://github.com/donnemartin/system-design-primer/tree/master/solutions/system_design/scaling_aws) section end-to-end |
| System design step-by-step | https://github.com/bregman-arie/system-design-notebook |
| 30 core concepts | https://github.com/ashishps1/awesome-system-design-resources |
| Latency numbers | https://colin-scott.github.io/personal_website/research/interactive_latency.html |
| CAP / PACELC, ACID / BASE | https://github.com/donnemartin/system-design-primer#consistency-patterns |

## Phase 1 — The AWS Mental Model & Well-Architected Framework (Week 1)

Before designing systems, internalize how AWS itself thinks about architecture. The Well-Architected Framework is the reference — every AWS architect uses these six pillars as mental checklists.

### Read

- [AWS Well-Architected Framework (full whitepaper)](https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html)
- The six pillar deep-dives:
  - [Operational Excellence](https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/welcome.html)
  - [Security](https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html)
  - [Reliability](https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/welcome.html)
  - [Performance Efficiency](https://docs.aws.amazon.com/wellarchitected/latest/performance-efficiency-pillar/welcome.html)
  - [Cost Optimization](https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html)
  - [Sustainability](https://docs.aws.amazon.com/wellarchitected/latest/sustainability-pillar/sustainability-pillar.html)
- [AWS Well-Architected Lenses](https://aws.amazon.com/architecture/well-architected/#Well-Architected_Lenses) — at minimum the Serverless, SaaS, and Reliability Lenses
- [AWS Architecture Center](https://aws.amazon.com/architecture/) — bookmark this

### Watch

- "AWS Well-Architected Best Practices" (re:Invent 2023) — search YouTube for `ARC201` and `ARC301`
- [AWS Events YouTube channel](https://www.youtube.com/@AWSEventsChannel)

### Build

- [AWS Well-Architected Labs](https://www.wellarchitectedlabs.com/) — complete the Level 100 labs for all six pillars (~6 hours total)
- Run the [AWS Well-Architected Tool](https://aws.amazon.com/well-architected-tool/) against a dummy workload in your own account

### Deliverable

Pick a project you have worked on and write a one-page review applying the six pillars. List three gaps per pillar.

## Phase 2 — The Amazon Builders' Library (Weeks 2–3)

The single most valuable free resource for learning how AWS designs real distributed systems. Written by Amazon principal engineers.

Home: https://aws.amazon.com/builders-library/

### Must-read articles (in order)

1. [Challenges with distributed systems](https://aws.amazon.com/builders-library/challenges-with-distributed-systems/)
2. [Timeouts, retries, and backoff with jitter](https://aws.amazon.com/builders-library/timeouts-retries-and-backoff-with-jitter/)
3. [Avoiding fallback in distributed systems](https://aws.amazon.com/builders-library/avoiding-fallback-in-distributed-systems/)
4. [Using load shedding to avoid overload](https://aws.amazon.com/builders-library/using-load-shedding-to-avoid-overload/)
5. [Avoiding insurmountable queue backlogs](https://aws.amazon.com/builders-library/avoiding-insurmountable-queue-backlogs/)
6. [Workload isolation using shuffle sharding](https://aws.amazon.com/builders-library/workload-isolation-using-shuffle-sharding/)
7. [Static stability using Availability Zones](https://aws.amazon.com/builders-library/static-stability-using-availability-zones/)
8. [Caching challenges and strategies](https://aws.amazon.com/builders-library/caching-challenges-and-strategies/)
9. [Leader election in distributed systems](https://aws.amazon.com/builders-library/leader-election-in-distributed-systems/)
10. [Avoiding overload by putting the smaller service in control](https://aws.amazon.com/builders-library/avoiding-overload-in-distributed-systems-by-putting-the-smaller-service-in-control/)
11. [Reliability, constant work, and a good cup of coffee](https://aws.amazon.com/builders-library/reliability-and-constant-work/)
12. [Making retries safe with idempotent APIs](https://aws.amazon.com/builders-library/making-retries-safe-with-idempotent-APIs/)
13. [Beyond five 9s: Lessons from our highest available data planes](https://aws.amazon.com/builders-library/beyond-five-9s-lessons-from-our-highest-available-data-planes/)

### Community summaries

- [Shekhar Gulati's condensed notes](https://shekhargulati.com/2021/12/03/key-insights-from-amazon-builder-library/)
- [Lumigo's "Builders Library in Focus" series](https://lumigo.io/blog/amazon-builders-library-in-focus-3-avoiding-fallback-in-distributed-systems/)

### Deliverable

For each article, write 3–5 bullets of "what I would actually do differently." By the end of Phase 2 you will have a 40-bullet personal playbook of distributed systems patterns.

## Phase 3 — AWS Reference Architectures & Design Patterns (Weeks 4–5)

### Core references

- [AWS Reference Architecture Diagrams](https://aws.amazon.com/architecture/reference-architecture-diagrams/)
- [AWS Prescriptive Guidance — Cloud Design Patterns](https://docs.aws.amazon.com/prescriptive-guidance/latest/cloud-design-patterns/introduction.html) — Circuit Breaker, CQRS, Event Sourcing, Saga, Strangler Fig, Sidecar, Anti-Corruption Layer, Outbox, Retry with Backoff
- [AWS Security Reference Architecture](https://docs.aws.amazon.com/prescriptive-guidance/latest/security-reference-architecture/architecture.html) and its [companion code repo](https://github.com/aws-samples/aws-security-reference-architecture-examples)
- [AWS Solutions Library](https://aws.amazon.com/solutions/)
- [Cloud Design Patterns catalog (community)](https://en.clouddesignpattern.org/)

### Key pattern categories

| Category | Patterns |
|---|---|
| Availability | Multi-AZ, Multi-Region Active-Active, Active-Passive, Pilot Light, Warm Standby |
| Data | Read replicas, Sharding, CQRS, Event Sourcing, Materialized Views, Outbox |
| Messaging | Fan-out (SNS→SQS), Point-to-point (SQS), Event streaming (Kinesis/MSK), DLQ, Saga |
| Resilience | Circuit Breaker, Bulkhead, Retry w/ jitter, Timeout, Shuffle Sharding, Cell-based |
| Compute | Blue/Green, Canary, Rolling, Feature flags |
| Network | Edge caching, VPC peering, Transit Gateway, PrivateLink, Service mesh |

### Hands-on

- [AWS Architecture Blog](https://aws.amazon.com/blogs/architecture/) — read one post a day
- ["This Is My Architecture"](https://aws.amazon.com/architecture/this-is-my-architecture/) — five-minute real customer architectures

### Deliverable

Pick five patterns from the table above. For each, draw an AWS architecture diagram (draw.io with [AWS icons](https://aws.amazon.com/architecture/icons/)) and write one paragraph on when **not** to use it.

## Phase 4 — AWS Service Deep-Dives That Matter for Design (Weeks 6–7)

Service selection tradeoffs — when to pick one over another, and why.

### Compute

- [Compute decision guide](https://docs.aws.amazon.com/decision-guides/latest/compute-on-aws-how-to-choose/choosing-aws-compute-service.html)
- [Containers decision guide](https://docs.aws.amazon.com/decision-guides/latest/containers-on-aws-how-to-choose/choosing-aws-container-service.html)

### Databases

- [Databases decision guide](https://docs.aws.amazon.com/decision-guides/latest/databases-on-aws-how-to-choose/choosing-aws-database-service.html)
- [DynamoDB best practices](https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html)
- [Alex DeBrie's DynamoDB Guide](https://www.dynamodbguide.com/)
- [Aurora architecture paper](https://media.amazonaws.com/blog/2017/aurora-design-considerations-paper.pdf) — short and worth reading in full
- [The DynamoDB Book (free chapters)](https://www.dynamodbbook.com/)
- [Dynamo: Amazon's Highly Available Key-value Store (2007 SOSP paper)](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)

### Storage

- [Storage decision guide](https://docs.aws.amazon.com/decision-guides/latest/storage-on-aws-how-to-choose/choosing-aws-storage-service.html)
- [S3 performance best practices](https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html)

### Networking

- [VPC documentation](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html)
- [AWS Networking Fundamentals workshop](https://catalog.workshops.aws/networking/en-US)
- [Networking and Content Delivery blog](https://aws.amazon.com/blogs/networking-and-content-delivery/)

### Messaging & Streaming

- [Messaging decision guide](https://docs.aws.amazon.com/decision-guides/latest/messaging-on-aws-how-to-choose/choosing-aws-messaging-service.html) — SQS vs SNS vs EventBridge vs Kinesis vs MSK
- [Kinesis scaling patterns](https://docs.aws.amazon.com/streams/latest/dev/kinesis-using-sdk-java-resharding.html)

### Deliverable

Create a decision table: given requirement X (e.g. "<10ms reads at 1M RPS globally"), which service fits and why. Aim for 25+ mappings.

## Phase 5 — Hands-On Workshops (Weeks 8–9)

AWS publishes hundreds of free self-paced workshops — same quality as paid classroom training, zero cost beyond small AWS usage charges.

### Catalogs

- [AWS Workshops](https://workshops.aws/)
- [12 Weeks of AWS Workshops](https://12weeksworkshops.com/)
- [AWS Samples GitHub org](https://github.com/aws-samples)

### Workshops (in order)

1. [AWS General Immersion Day](https://catalog.workshops.aws/general-immersionday/en-US)
2. [Serverless Workshops](https://catalog.workshops.aws/serverless-patterns/en-US)
3. [Serverless Land Patterns library](https://serverlessland.com/patterns)
4. [Microservices on AWS](https://catalog.workshops.aws/microservices-on-aws/en-US)
5. [Amazon EKS Workshop](https://www.eksworkshop.com/)
6. [DynamoDB Labs](https://amazon-dynamodb-labs.com/)
7. [Build a Modern Data Architecture](https://catalog.workshops.aws/modern-data-architecture/en-US)
8. [Observability Workshop](https://catalog.workshops.aws/observability/en-US)
9. [Chaos Engineering on AWS](https://catalog.workshops.aws/fis/en-US)
10. [Event-Driven Architectures with EventBridge](https://catalog.workshops.aws/eventbridge/en-US)

### Capstone project

Build this in your own AWS account over 1–2 weeks:

> A multi-region, event-driven URL shortener with ~100ms p99 read latency globally, costing under $5/month at low volume.

Required components:

- Route 53 latency-based routing
- CloudFront + Lambda@Edge for the read path
- DynamoDB Global Tables
- API Gateway + Lambda for the write path
- EventBridge for analytics events
- Kinesis Firehose → S3 → Athena for analytics
- CloudWatch + X-Ray for observability
- Terraform or CDK for all infrastructure

Publish the code on GitHub with a README explaining every design decision.

## Phase 6 — Real-World Case Studies (Week 10)

### Netflix

- [Netflix Tech Blog](https://netflixtechblog.com/) — read the 20 most-starred posts
- [Cloud architecture tag](https://netflixtechblog.com/tagged/cloud-architecture)
- [AWS case study](https://aws.amazon.com/solutions/case-studies/innovators/netflix/)
- Key concepts: Chaos Monkey / Simian Army, Hystrix (circuit breaker), Eureka (service discovery), Spinnaker, Open Connect CDN, regional failover

### Other engineering blogs

- [Uber Engineering](https://www.uber.com/blog/engineering/)
- [Airbnb Engineering](https://medium.com/airbnb-engineering)
- [Slack Engineering](https://slack.engineering/)
- [Dropbox Tech](https://dropbox.tech/)
- [Lyft Engineering](https://eng.lyft.com/)
- [Stripe Engineering](https://stripe.com/blog/engineering)

### Aggregators

- [High Scalability](http://highscalability.com/)
- [awesome-scalability](https://github.com/binhnguyennus/awesome-scalability)
- [InfoQ architecture track](https://www.infoq.com/architecture-design/)

### Deliverable

Write a two-page "Netflix on AWS" document in your own words — what they use, why, what alternatives existed, what tradeoffs they made.

## Phase 7 — Interview-Style Design Drills (Week 11)

### Design problem repositories

- [System Design Primer — case studies](https://github.com/donnemartin/system-design-primer#system-design-interview-questions-with-solutions)
- [awesome-system-design-resources](https://github.com/ashishps1/awesome-system-design-resources)
- [karanpratapsingh/system-design](https://github.com/karanpratapsingh/system-design)
- [InterviewReady system-design-resources](https://github.com/InterviewReady/system-design-resources)
- [arkapg211002/System-Design-Preparation](https://github.com/arkapg211002/System-Design-Preparation)

### Classic problems (solve two a day for a week, AWS services only)

1. URL shortener (Bitly) — DynamoDB, Lambda, CloudFront
2. Pastebin — S3, DynamoDB, CloudFront
3. Instagram feed — DynamoDB + SQS fan-out, S3 + CloudFront for media
4. Twitter timeline — hybrid push/pull, ElastiCache, DynamoDB
5. Rate limiter — DynamoDB atomic counters or ElastiCache + Lua
6. Notification system — SNS + SQS + Lambda
7. Distributed cache — ElastiCache (Redis) with cluster mode
8. Real-time chat (WhatsApp) — API Gateway WebSockets, DynamoDB, Kinesis
9. Ride-sharing dispatch (Uber) — Kinesis, geohash in DynamoDB, Lambda
10. Video streaming (YouTube/Netflix) — S3, MediaConvert, CloudFront
11. Distributed job scheduler — Step Functions / EventBridge Scheduler + SQS
12. Log aggregation (Datadog-like) — Kinesis Firehose → S3 → Athena / OpenSearch
13. Search engine — OpenSearch + S3 for source of truth
14. E-commerce checkout — Step Functions orchestration, Saga, DynamoDB transactions
15. Payment system — idempotency, outbox pattern, exactly-once processing

### YouTube channels

- [Gaurav Sen](https://www.youtube.com/@gkcs)
- [ByteByteGo](https://www.youtube.com/@ByteByteGo)
- [System Design Interview](https://www.youtube.com/@SystemDesignInterview)
- [Hussein Nasser](https://www.youtube.com/@hnasr)
- [Be A Better Dev](https://www.youtube.com/@BeABetterDev)
- [AWS Events](https://www.youtube.com/@AWSEventsChannel)

### Must-watch re:Invent talks

Search these titles on YouTube:

- "Amazon's approach to high-availability deployment" (ARC318)
- "Beyond five 9s: Lessons from our highest available data planes" (ARC334)
- "Building resilient services at Prime Video" (ARC303)
- "Scaling on AWS for the first 10 million users" (ARC203)
- "Dive deep on Amazon S3" (STG302)
- "Amazon DynamoDB deep dive: Advanced design patterns" (DAT404)
- "Design patterns for multi-tenant access control" (SEC310)

## Phase 8 — Capstone & Continuous Learning (Week 12+)

### Capstone deliverables

1. Public GitHub repo of the multi-region URL shortener from Phase 5.
2. A personal blog or Notion page with your 10 best design writeups.
3. One end-to-end PRFAQ-style design doc for a fictional product. [Working backwards template](https://www.productplan.com/glossary/working-backward-amazon-method/).

### Ongoing inputs

- [AWS Architecture Blog RSS](https://aws.amazon.com/blogs/architecture/feed/)
- [AWS News Blog](https://aws.amazon.com/blogs/aws/)
- [All Things Distributed (Werner Vogels)](https://www.allthingsdistributed.com/)
- [InfoQ Software Architecture newsletter](https://www.infoq.com/architecture-design/)
- [SystemDesign Weekly](https://systemdesign.one/)
- [ByteByteGo newsletter](https://blog.bytebytego.com/)

### Foundational papers (one a month)

- [Dynamo](https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf)
- [Amazon Aurora](https://web.stanford.edu/class/cs245/readings/aurora.pdf)
- [MillWheel / Dataflow (Google)](https://research.google/pubs/pub41378/)
- [The Google File System](https://research.google/pubs/pub51/)
- [MapReduce](https://research.google/pubs/pub62/)
- [Spanner](https://research.google/pubs/pub39966/)
- [Raft consensus](https://raft.github.io/raft.pdf)
- [CAP twelve years later (Eric Brewer)](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed/)

## Consolidated Resource Index

### Official AWS

| Resource | URL |
|---|---|
| Architecture Center | https://aws.amazon.com/architecture/ |
| Well-Architected Framework | https://aws.amazon.com/architecture/well-architected/ |
| Well-Architected Labs | https://www.wellarchitectedlabs.com/ |
| Amazon Builders' Library | https://aws.amazon.com/builders-library/ |
| Reference Architectures | https://aws.amazon.com/architecture/reference-architecture-diagrams/ |
| Prescriptive Guidance | https://docs.aws.amazon.com/prescriptive-guidance/ |
| Decision Guides | https://docs.aws.amazon.com/decision-guides/ |
| Workshops | https://workshops.aws/ |
| AWS Samples | https://github.com/aws-samples |
| AWS Skill Builder (free tier) | https://skillbuilder.aws |
| Architecture Blog | https://aws.amazon.com/blogs/architecture/ |
| Serverless Land | https://serverlessland.com/ |
| Architecture Icons | https://aws.amazon.com/architecture/icons/ |
| This Is My Architecture | https://aws.amazon.com/architecture/this-is-my-architecture/ |
| AWS Events YouTube | https://www.youtube.com/@AWSEventsChannel |

### Community GitHub archives

| Repo | URL |
|---|---|
| System Design Primer | https://github.com/donnemartin/system-design-primer |
| awesome-system-design-resources | https://github.com/ashishps1/awesome-system-design-resources |
| awesome-scalability | https://github.com/binhnguyennus/awesome-scalability |
| awesome-system-design | https://github.com/madd86/awesome-system-design |
| system-design-notebook | https://github.com/bregman-arie/system-design-notebook |
| System-Design-Preparation | https://github.com/arkapg211002/System-Design-Preparation |
| Karan Pratap Singh system-design | https://github.com/karanpratapsingh/system-design |
| InterviewReady system-design-resources | https://github.com/InterviewReady/system-design-resources |
| Developer-Y Scalable-Software-Architecture | https://github.com/Developer-Y/Scalable-Software-Architecture |

### Engineering blogs

| Blog | URL |
|---|---|
| Netflix Tech Blog | https://netflixtechblog.com/ |
| Uber Engineering | https://www.uber.com/blog/engineering/ |
| Airbnb Engineering | https://medium.com/airbnb-engineering |
| Slack Engineering | https://slack.engineering/ |
| Dropbox Tech | https://dropbox.tech/ |
| Lyft Engineering | https://eng.lyft.com/ |
| Stripe Engineering | https://stripe.com/blog/engineering |
| High Scalability | http://highscalability.com/ |
| All Things Distributed | https://www.allthingsdistributed.com/ |
| InfoQ Architecture | https://www.infoq.com/architecture-design/ |

### YouTube channels

| Channel | URL |
|---|---|
| AWS Events | https://www.youtube.com/@AWSEventsChannel |
| Be A Better Dev | https://www.youtube.com/@BeABetterDev |
| ByteByteGo | https://www.youtube.com/@ByteByteGo |
| Gaurav Sen | https://www.youtube.com/@gkcs |
| System Design Interview | https://www.youtube.com/@SystemDesignInterview |
| Hussein Nasser | https://www.youtube.com/@hnasr |

## Time & Commitment Summary

| Phase | Duration | Hours/week | Primary Output |
|---|---|---|---|
| 0 — Prereqs | Week 0 | 4 | Vocabulary solid |
| 1 — Well-Architected | Week 1 | 6 | Six-pillar review of an existing project |
| 2 — Builders' Library | Weeks 2–3 | 7 | 40-bullet personal pattern playbook |
| 3 — Reference architectures | Weeks 4–5 | 7 | 5 pattern diagrams + tradeoff notes |
| 4 — Service deep-dives | Weeks 6–7 | 8 | Decision table (25+ mappings) |
| 5 — Hands-on workshops | Weeks 8–9 | 10 | Capstone multi-region URL shortener |
| 6 — Case studies | Week 10 | 6 | Netflix-on-AWS writeup |
| 7 — Interview drills | Week 11 | 8 | 15 solved design problems |
| 8 — Capstone + ongoing | Week 12+ | ongoing | Public portfolio + PRFAQ doc |

**Total: ~75–90 hours across ~12 weeks.**

## Ground Rules

1. **Read actively, not passively.** After each article, close the tab and write three bullets in your own words.
2. **Always build.** Every week, spend at least two hours in an actual AWS console or Terraform file.
3. **Draw diagrams.** Use draw.io or Excalidraw with AWS icons. If you cannot draw it, you do not understand it.
4. **Teach it.** After each phase, post one writeup or record a 10-minute walkthrough. Forces clarity.
5. **Limit video to 20% of your time.** Docs and hands-on work beat videos. Videos are a supplement.
6. **Kill scope creep.** This plan has enough. Adding paid courses on top is death by abundance.

## Contributing

Contributions are welcome — broken links, better resources, corrections, new phases, and translations all help. See [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## License

This plan is released under the [MIT License](LICENSE). Linked external resources remain the property of their respective owners.
