# AWS System Design — Full Self-Study Plan (100% Free Resources)

**Target audience:** Mid-to-senior engineers who already know AWS basics (EC2, VPC, S3, IAM, Docker, Kubernetes, Terraform) and want to master **designing systems on AWS** — not just passing SAA-C03.

**Goal:** Be able to walk into any design meeting or senior/staff interview and design a production-grade system on AWS from scratch, justifying every component choice.

**Total duration:** ~12 weeks at ~6–8 hrs/week (compressible to 8 weeks if focused).

**Philosophy:** Official AWS docs/whitepapers + curated GitHub archives + real-world case studies + hands-on labs. No paid courses. No certification prep fluff.

---

## How to Use This Plan

Each phase has three layers:

1. **Read** — whitepapers, blog posts, GitHub notes
2. **Watch** — free YouTube / re:Invent talks
3. **Build** — hands-on workshops or your own mini-project

Do not skip the Build layer. Design sticks when you've actually wired it up in an AWS account (Free Tier covers ~90% of what's below).

At the end of each phase, write a short "design note" (one page) explaining a system you'd design using that phase's concepts. Keep these in a private Notion/GitHub repo — they become your personal design-interview cheat sheet.

---

## Phase 0 — Foundations You Must Have First (Week 0, skip if solid)

These are prerequisites. If any of these feel fuzzy, spend a few days here first.

| Topic | Resource | Why |
|---|---|---|
| General system design primer | https://github.com/donnemartin/system-design-primer | The canonical free reference. Read the "scaling AWS" section end-to-end: https://github.com/donnemartin/system-design-primer/tree/master/solutions/system_design/scaling_aws |
| System design step-by-step | https://github.com/bregman-arie/system-design-notebook | Walks you through scaling a system using AWS specifically |
| 30 core concepts | https://github.com/ashishps1/awesome-system-design-resources | Ashish Pratap Singh's curated list — start with "30 concepts" |
| Latency numbers | https://colin-scott.github.io/personal_website/research/interactive_latency.html | Memorize the orders of magnitude |
| CAP / PACELC, ACID / BASE | https://github.com/donnemartin/system-design-primer#consistency-patterns | Non-negotiable vocabulary |

---

## Phase 1 — The AWS Mental Model & Well-Architected Framework (Week 1)

Before designing systems, internalize how AWS itself thinks about architecture. The Well-Architected Framework is **the** reference — every AWS architect uses these six pillars as mental checklists.

### Read
- **AWS Well-Architected Framework (full whitepaper)** — https://docs.aws.amazon.com/wellarchitected/latest/framework/welcome.html
- The six pillar deep-dives (each has its own doc):
  - Operational Excellence — https://docs.aws.amazon.com/wellarchitected/latest/operational-excellence-pillar/welcome.html
  - Security — https://docs.aws.amazon.com/wellarchitected/latest/security-pillar/welcome.html
  - Reliability — https://docs.aws.amazon.com/wellarchitected/latest/reliability-pillar/welcome.html
  - Performance Efficiency — https://docs.aws.amazon.com/wellarchitected/latest/performance-efficiency-pillar/welcome.html
  - Cost Optimization — https://docs.aws.amazon.com/wellarchitected/latest/cost-optimization-pillar/welcome.html
  - Sustainability — https://docs.aws.amazon.com/wellarchitected/latest/sustainability-pillar/sustainability-pillar.html
- **AWS Well-Architected Lenses** (industry/domain-specific extensions) — https://aws.amazon.com/architecture/well-architected/#Well-Architected_Lenses
  - Read at minimum: Serverless Lens, SaaS Lens, and Reliability Lens
- **AWS Architecture Center home** — https://aws.amazon.com/architecture/ (bookmark this; you'll return constantly)

### Watch
- "AWS Well-Architected Best Practices" (re:Invent 2023) — search YouTube "ARC201" and "ARC301"
- AWS Events YouTube channel — https://www.youtube.com/@AWSEventsChannel

### Build
- **AWS Well-Architected Labs** (free, hands-on, official) — https://www.wellarchitectedlabs.com/
  - Do: Level 100 labs for all six pillars (about 6 hours total)
- Run the **AWS Well-Architected Tool** against a dummy workload in your own account — https://aws.amazon.com/well-architected-tool/

### Deliverable
Pick an old project of yours (e.g., ManageIT or ShieldIT) and write a one-page review applying the six pillars. List 3 gaps per pillar.

---

## Phase 2 — The Amazon Builders' Library (Weeks 2–3)

**This is the single most valuable free resource on the internet for learning how AWS designs real distributed systems.** Written by Amazon principal engineers. Nothing on a paid course comes close.

Home: https://aws.amazon.com/builders-library/

### Must-read articles (in order)
1. **Challenges with distributed systems** — https://aws.amazon.com/builders-library/challenges-with-distributed-systems/
2. **Timeouts, retries, and backoff with jitter** — https://aws.amazon.com/builders-library/timeouts-retries-and-backoff-with-jitter/
3. **Avoiding fallback in distributed systems** — https://aws.amazon.com/builders-library/avoiding-fallback-in-distributed-systems/
4. **Using load shedding to avoid overload** — https://aws.amazon.com/builders-library/using-load-shedding-to-avoid-overload/
5. **Avoiding insurmountable queue backlogs** — https://aws.amazon.com/builders-library/avoiding-insurmountable-queue-backlogs/
6. **Workload isolation using shuffle sharding** — https://aws.amazon.com/builders-library/workload-isolation-using-shuffle-sharding/
7. **Static stability using Availability Zones** — https://aws.amazon.com/builders-library/static-stability-using-availability-zones/
8. **Caching challenges and strategies** — https://aws.amazon.com/builders-library/caching-challenges-and-strategies/
9. **Leader election in distributed systems** — https://aws.amazon.com/builders-library/leader-election-in-distributed-systems/
10. **Avoiding overload in distributed systems by putting the smaller service in control** — https://aws.amazon.com/builders-library/avoiding-overload-in-distributed-systems-by-putting-the-smaller-service-in-control/
11. **Reliability, constant work, and a good cup of coffee** — https://aws.amazon.com/builders-library/reliability-and-constant-work/
12. **Making retries safe with idempotent APIs** — https://aws.amazon.com/builders-library/making-retries-safe-with-idempotent-APIs/
13. **Beyond five 9s: Lessons from our highest available data planes** — https://aws.amazon.com/builders-library/beyond-five-9s-lessons-from-our-highest-available-data-planes/

### Community summaries (great supplements)
- Shekhar Gulati's condensed notes — https://shekhargulati.com/2021/12/03/key-insights-from-amazon-builder-library/
- Lumigo's "Builders Library in Focus" series — https://lumigo.io/blog/amazon-builders-library-in-focus-3-avoiding-fallback-in-distributed-systems/

### Deliverable
For each article, write 3–5 bullet points of "what I'd actually do differently." By the end of Phase 2 you'll have a 40-bullet personal playbook of distributed systems patterns.

---

## Phase 3 — AWS Reference Architectures & Design Patterns (Weeks 4–5)

Now that you understand the principles, study how AWS actually combines services into real reference architectures.

### Core references
- **AWS Reference Architecture Diagrams library** — https://aws.amazon.com/architecture/reference-architecture-diagrams/ (filter by category: databases, ML, serverless, etc.)
- **AWS Prescriptive Guidance — Cloud Design Patterns** — https://docs.aws.amazon.com/prescriptive-guidance/latest/cloud-design-patterns/introduction.html (covers: Circuit Breaker, CQRS, Event Sourcing, Saga, Strangler Fig, Sidecar, Anti-Corruption Layer, Outbox, Retry with Backoff, etc. — each mapped to AWS services)
- **AWS Security Reference Architecture (SRA)** — https://docs.aws.amazon.com/prescriptive-guidance/latest/security-reference-architecture/architecture.html
  - Companion code repo: https://github.com/aws-samples/aws-security-reference-architecture-examples
- **AWS Solutions Library** (pre-built solutions with full architecture) — https://aws.amazon.com/solutions/
- **Cloud Design Patterns (CDP) from AWS community** — https://en.clouddesignpattern.org/ (older but great catalog of named patterns)

### Key pattern categories to master
| Category | Patterns to understand |
|---|---|
| Availability | Multi-AZ, Multi-Region Active-Active, Active-Passive, Pilot Light, Warm Standby |
| Data | Read replicas, Sharding, CQRS, Event Sourcing, Materialized Views, Outbox |
| Messaging | Fan-out (SNS→SQS), Point-to-point (SQS), Event streaming (Kinesis/MSK), DLQ, Saga |
| Resilience | Circuit Breaker, Bulkhead, Retry w/ jitter, Timeout, Shuffle Sharding, Cell-based |
| Compute | Blue/Green, Canary, Rolling, Feature flags |
| Network | Edge caching, VPC peering, Transit Gateway, PrivateLink, Service mesh |

### Hands-on
- **AWS Architecture Blog** — https://aws.amazon.com/blogs/architecture/ (read 1 post/day — this is where new reference architectures land)
- **"This Is My Architecture"** video series — https://aws.amazon.com/architecture/this-is-my-architecture/ (5-min real customer architectures; watch 2/day)

### Deliverable
Pick 5 patterns from the table above. For each, draw an AWS architecture diagram (use draw.io with AWS icons: https://aws.amazon.com/architecture/icons/) and write 1 paragraph on when *not* to use it.

---

## Phase 4 — AWS Service Deep-Dives That Matter for Design (Weeks 6–7)

You already know the services exist. This phase is about the **design tradeoffs** — when to pick one over another, and why.

### Compute decision guide
- https://aws.amazon.com/compute/ (EC2 vs Lambda vs Fargate vs EKS vs ECS vs Lightsail vs Batch)
- **Decision guide for containers** — https://docs.aws.amazon.com/decision-guides/latest/containers-on-aws-how-to-choose/choosing-aws-container-service.html
- **Decision guide for compute** — https://docs.aws.amazon.com/decision-guides/latest/compute-on-aws-how-to-choose/choosing-aws-compute-service.html

### Databases (the most interview-relevant category)
- **Decision guide for databases** — https://docs.aws.amazon.com/decision-guides/latest/databases-on-aws-how-to-choose/choosing-aws-database-service.html
- **DynamoDB Deep Dive** (official book, free) — https://docs.aws.amazon.com/amazondynamodb/latest/developerguide/best-practices.html
- **Alex DeBrie's DynamoDB Guide** (free) — https://www.dynamodbguide.com/
- **Aurora architecture paper** (read this one — it's short and brilliant) — https://media.amazonaws.com/blog/2017/aurora-design-considerations-paper.pdf
- **"The DynamoDB Book" free chapters** — https://www.dynamodbbook.com/
- **Dynamo: Amazon's Highly Available Key-value Store** (original 2007 SOSP paper, foundational) — https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf

### Storage
- **Decision guide for storage** — https://docs.aws.amazon.com/decision-guides/latest/storage-on-aws-how-to-choose/choosing-aws-storage-service.html
- S3 performance best practices — https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html

### Networking (underrated for design interviews)
- **VPC reference architectures** — https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html
- **AWS Networking Fundamentals** (free workshop) — https://catalog.workshops.aws/networking/en-US
- https://aws.amazon.com/blogs/networking-and-content-delivery/

### Messaging & Streaming
- SQS vs SNS vs EventBridge vs Kinesis vs MSK — https://docs.aws.amazon.com/decision-guides/latest/messaging-on-aws-how-to-choose/choosing-aws-messaging-service.html
- **Kinesis scaling patterns** — https://docs.aws.amazon.com/streams/latest/dev/kinesis-using-sdk-java-resharding.html

### Full-service catalog reference
- **w3schools AWS** (yes, really — it's a clean free service-by-service reference) — https://www.w3schools.com/aws/
- **Every AWS service, one-line summary** — https://adayinthelifeof.nl/2020/05/20/aws.html

### Deliverable
Create a "decision table" document: when given requirement X (e.g., "I need <10ms reads at 1M RPS globally"), what service do I pick and why? Aim for 25+ requirement → service mappings.

---

## Phase 5 — Hands-On Workshops: Build Real Architectures (Weeks 8–9)

AWS publishes ~500 free self-paced workshops. These are the gold standard — same quality as their paid classroom training, zero cost (you only pay AWS usage, usually pennies).

### Central catalogs
- **AWS Workshops main catalog** — https://workshops.aws/
- **12 Weeks of AWS Workshops** (curated learning path) — https://12weeksworkshops.com/
- **AWS Samples GitHub org** (code for thousands of architectures) — https://github.com/aws-samples

### Specific workshops to complete (in order)
1. **AWS General Immersion Day** — https://catalog.workshops.aws/general-immersionday/en-US (foundations with EC2/VPC)
2. **Serverless Workshops** — https://catalog.workshops.aws/serverless-patterns/en-US
3. **Serverless Land Patterns library** — https://serverlessland.com/patterns (hundreds of copy-paste IaC patterns)
4. **Microservices on AWS** — https://catalog.workshops.aws/microservices-on-aws/en-US
5. **Amazon EKS Workshop** — https://www.eksworkshop.com/
6. **DynamoDB Labs** — https://amazon-dynamodb-labs.com/
7. **Build a Modern Data Architecture** — https://catalog.workshops.aws/modern-data-architecture/en-US
8. **Observability Workshop** — https://catalog.workshops.aws/observability/en-US
9. **Chaos Engineering on AWS** — https://catalog.workshops.aws/fis/en-US
10. **Event-Driven Architectures with EventBridge** — https://catalog.workshops.aws/eventbridge/en-US

### Your own capstone project (the one that matters most)
Build this in your own account over 1–2 weeks. It will be your interview talking-point:

> A multi-region, event-driven URL shortener with ~100ms p99 read latency globally, costing <$5/month at low volume.

Required components:
- Route 53 latency-based routing
- CloudFront + Lambda@Edge for read path
- DynamoDB Global Tables
- API Gateway + Lambda for write path
- EventBridge for analytics events
- Kinesis Firehose → S3 → Athena for analytics
- CloudWatch + X-Ray for observability
- Terraform or CDK for all of it (leverage your existing Terraform skill)

Post it on GitHub. Write a README explaining every design decision.

---

## Phase 6 — Real-World Case Studies (Week 10)

Now that you know the "how," study how real companies combined these pieces.

### Netflix (the canonical AWS case study)
- **Netflix Tech Blog** — https://netflixtechblog.com/ (read the 20 most-starred posts)
- **How Netflix Thinks About Cloud Architecture** — https://netflixtechblog.com/tagged/cloud-architecture
- **AWS case study page** — https://aws.amazon.com/solutions/case-studies/innovators/netflix/
- Key concepts to extract: Chaos Monkey/Simian Army, Hystrix (circuit breaker), Eureka (service discovery), Spinnaker, Open Connect CDN, regional failover

### Other must-read engineering blogs
- **Uber Engineering** — https://www.uber.com/blog/engineering/
- **Airbnb Engineering** — https://medium.com/airbnb-engineering
- **Slack Engineering** — https://slack.engineering/
- **Dropbox Tech** — https://dropbox.tech/
- **Lyft Engineering** — https://eng.lyft.com/
- **Stripe Engineering** — https://stripe.com/blog/engineering

### Aggregators
- **High Scalability** (classic blog; search by company) — http://highscalability.com/
- **awesome-scalability** (massive curated index of case studies) — https://github.com/binhnguyennus/awesome-scalability
- **InfoQ architecture track** — https://www.infoq.com/architecture-design/

### Deliverable
Write a 2-page "Netflix on AWS" document in your own words — what they use, why, what alternatives existed, what tradeoffs they made. This exercise alone is worth a staff-level interview answer.

---

## Phase 7 — Interview-Style Design Drills (Week 11)

Practice designing on AWS under time pressure.

### Free repositories of design problems (with AWS-flavored solutions)
- **System Design Primer — case studies** — https://github.com/donnemartin/system-design-primer#system-design-interview-questions-with-solutions (design Pastebin, Twitter, web crawler, Uber, Mint, etc. — all walk through scaling with AWS)
- **ashishps1/awesome-system-design-resources** — https://github.com/ashishps1/awesome-system-design-resources
- **karanpratapsingh/system-design** (clean free book) — https://github.com/karanpratapsingh/system-design
- **InterviewReady System Design resources** — https://github.com/InterviewReady/system-design-resources
- **arkapg211002/System-Design-Preparation** — https://github.com/arkapg211002/System-Design-Preparation

### Classic problems to solve (do 2/day for a week, using only AWS services)
1. URL shortener (Bitly) — DynamoDB, Lambda, CloudFront
2. Pastebin — S3, DynamoDB, CloudFront
3. Instagram feed — DynamoDB + fan-out via SQS, S3 + CloudFront for media
4. Twitter timeline — hybrid push/pull, ElastiCache, DynamoDB
5. Rate limiter — DynamoDB atomic counters or ElastiCache + Lua
6. Notification system — SNS + SQS + Lambda
7. Distributed cache — ElastiCache (Redis) with cluster mode
8. Real-time chat (WhatsApp) — API Gateway WebSockets, DynamoDB, Kinesis
9. Ride-sharing dispatch (Uber) — Kinesis, geohash in DynamoDB, Lambda
10. Video streaming (YouTube/Netflix) — S3, MediaConvert, CloudFront, Open Connect idea
11. Distributed job scheduler — Step Functions / EventBridge Scheduler + SQS
12. Log aggregation (Datadog-like) — Kinesis Firehose → S3 → Athena / OpenSearch
13. Search engine — OpenSearch + S3 for source of truth
14. E-commerce checkout — Step Functions orchestration, Saga pattern, DynamoDB transactions
15. Payment system — idempotency, outbox pattern, exactly-once processing

### YouTube channels for worked solutions
- **Gaurav Sen** — https://www.youtube.com/@gkcs
- **ByteByteGo** — https://www.youtube.com/@ByteByteGo
- **System Design Interview (channel)** — https://www.youtube.com/@SystemDesignInterview
- **Hussein Nasser** (deep networking/DB) — https://www.youtube.com/@hnasr
- **Be A Better Dev** (very AWS-focused) — https://www.youtube.com/@BeABetterDev
- **AWS Events (re:Invent recordings)** — https://www.youtube.com/@AWSEventsChannel

### Must-watch re:Invent talks (search these titles on YouTube)
- "Amazon's approach to high-availability deployment" (ARC318)
- "Beyond five 9s: Lessons from our highest available data planes" (ARC334)
- "Building resilient services at Prime Video" (ARC303)
- "Scaling on AWS for the first 10 million users" (ARC203) — the *classic* intro talk
- "Dive deep on Amazon S3" (STG302)
- "Amazon DynamoDB deep dive: Advanced design patterns" (DAT404)
- "Design patterns for multi-tenant access control" (SEC310)

---

## Phase 8 — Capstone & Continuous Learning (Week 12+)

### Capstone deliverables (finalize portfolio)
1. Public GitHub repo of your multi-region URL shortener from Phase 5
2. A personal blog / Notion page with your 10 best design writeups
3. One end-to-end design doc (PRFAQ style, the way Amazon writes them) for a fictional product — e.g., "AI Tier-1 Helpdesk Agent for Canadian MSPs" (tie it to your ShieldIT/AI agent work)
   - Template for Amazon-style working backwards documents: https://www.productplan.com/glossary/working-backward-amazon-method/

### Ongoing inputs (subscribe once, learn forever)
- **AWS Architecture Blog RSS** — https://aws.amazon.com/blogs/architecture/feed/
- **AWS News Blog** — https://aws.amazon.com/blogs/aws/
- **All Things Distributed** (Werner Vogels) — https://www.allthingsdistributed.com/
- **InfoQ Software Architecture newsletter** — https://www.infoq.com/architecture-design/
- **SystemDesign Weekly** newsletter (free) — https://systemdesign.one/
- **ByteByteGo newsletter** (free tier) — https://blog.bytebytego.com/

### Foundational papers (read one a month — the classics behind AWS services)
- **Dynamo** — https://www.allthingsdistributed.com/files/amazon-dynamo-sosp2007.pdf
- **Amazon Aurora** — https://web.stanford.edu/class/cs245/readings/aurora.pdf
- **Millwheel / Dataflow (Google, but Kinesis was influenced)** — https://research.google/pubs/pub41378/
- **The Google File System** — https://research.google/pubs/pub51/
- **MapReduce** — https://research.google/pubs/pub62/
- **Spanner** — https://research.google/pubs/pub39966/
- **Raft consensus** — https://raft.github.io/raft.pdf
- **CAP twelve years later** (Eric Brewer) — https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed/

---

## Consolidated Resource Index (bookmark this)

### Official AWS (all free)
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
| AWS learning path | https://github.com/maronavenue/aws-learning-path |

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

---

## Time & Commitment Summary

| Phase | Duration | Hours/week | Primary Output |
|---|---|---|---|
| 0 — Prereqs | Week 0 | 4 | Vocabulary solid |
| 1 — Well-Architected | Week 1 | 6 | Six-pillar review of an old project |
| 2 — Builders' Library | Weeks 2–3 | 7 | 40-bullet personal pattern playbook |
| 3 — Reference architectures | Weeks 4–5 | 7 | 5 pattern diagrams + tradeoff notes |
| 4 — Service deep-dives | Weeks 6–7 | 8 | Decision table (25+ mappings) |
| 5 — Hands-on workshops | Weeks 8–9 | 10 | Capstone multi-region URL shortener |
| 6 — Case studies | Week 10 | 6 | Netflix-on-AWS writeup |
| 7 — Interview drills | Week 11 | 8 | 15 solved design problems |
| 8 — Capstone + ongoing | Week 12+ | ongoing | Public portfolio + PRFAQ doc |

**Total: ~75–90 hours of focused work across ~12 weeks.**

## Non-Negotiable Rules for This Plan to Work

1. **Read actively, not passively.** After each article, close the tab and write 3 bullets in your own words.
2. **Always build.** Every week spend at least 2 hours in an actual AWS console/Terraform file.
3. **Draw diagrams.** Use draw.io or Excalidraw with AWS icons. If you can't draw it, you don't understand it.
4. **Teach it.** After each phase, post one LinkedIn/blog post or record a 10-min Loom. Forces clarity.
5. **Limit YouTube to 20% of your time.** Docs + hands-on > videos. Videos are a supplement.
6. **Kill scope creep.** This plan has enough. Adding paid courses on top = death by abundance.

You already have more than enough free, battle-tested material above to reach a genuine senior/staff-level design competence on AWS. Good luck.
