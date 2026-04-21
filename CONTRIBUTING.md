# Contributing
 
Thanks for wanting to improve this plan. This repo is a curated reading list, so most contributions are small and focused. The goal is to keep quality high and the plan tight — not to be exhaustive.
 
## What we accept
 
- **Fixes to broken or moved links.**
- **Replacements for dead resources** with equivalent or better free alternatives.
- **Typo and grammar fixes.**
- **Additions of high-quality free resources** that clearly improve a phase (see bar below).
- **Clarifications or rewrites** that make a section easier to follow.
- **New phases or sub-sections** — only after opening an issue to discuss first.
- **Translations** of the README into other languages (as `README.<lang>.md`).
## What we do not accept
 
- **Paid courses, books, or bootcamps.** The plan is free-only. Do not open PRs linking to Udemy, A Cloud Guru, O'Reilly, Coursera paid tracks, etc. Community editions and free tiers are fine if they offer real value without a paywall for the core content.
- **Affiliate links or self-promotion** disguised as resource suggestions. Disclose any personal or commercial affiliation in your PR.
- **AWS-competitor content** unless it directly teaches a concept AWS reuses (e.g. the original Dynamo paper, Raft, Google's Spanner paper). This repo is specifically about AWS.
- **Marketing blog posts** from vendors that do not teach something substantive.
- **Exam-dump style content.** This is a design plan, not certification cramming.
- **Resources behind a login wall** (LinkedIn Learning gated, Medium paywalled, etc.) unless a free alternative is provided alongside.
## The bar for a new resource
 
Before suggesting a resource, check that it:
 
1. Is free (no paywall, no trial expiration, no account wall for core content).
2. Teaches a concept that is not already covered by something in the plan.
3. Comes from a credible source — AWS itself, a principal engineer at a well-known company, a widely cited paper, a well-maintained open-source project, or an engineering blog with a track record.
4. Will still be useful in 2 years. Avoid linking to news articles or conference announcements.
5. Is not a mirror or summary of another resource already in the plan.
If a resource passes all five, it probably belongs.
 
## How to contribute
 
### Reporting a broken link or small issue
 
Open an issue with:
 
- The exact link that is broken.
- The phase and section it appears in.
- A suggested replacement, if you have one.
### Submitting a pull request
 
1. **Fork** the repo and create a branch: `git checkout -b fix/broken-dynamodb-link` or `feat/add-serverless-workshop`.
2. **Make one logical change per PR.** Do not batch a dozen unrelated edits.
3. **Keep the style consistent** with the rest of the README:
   - Tone is neutral and practical. No hype, no superlatives, no emoji.
   - Links use `[text](url)` markdown, not raw URLs, except inside tables.
   - Resource entries are terse — one line where possible.
   - Headings follow the existing hierarchy.
4. **Test all links** in your PR locally. A simple way:
   ```bash
   # Install markdown-link-check (requires Node.js)
   npm install -g markdown-link-check
   markdown-link-check README.md
   ```
 
5. **Write a clear PR description** covering:
   - What you changed.
   - Why it is better than what was there.
   - If adding a resource, which of the five bar criteria it meets.
6. **Reference any related issue** with `Fixes #123` or `Refs #123`.
### Commit messages
 
Use imperative, present-tense, lowercase subjects:
 
- `fix: correct broken link to dynamodb guide`
- `feat: add eks workshop to phase 5`
- `docs: rewrite phase 3 intro for clarity`
## Style guide
 
- **No first-person language in the README.** Write "you" or use imperative mood, not "I recommend" or "my favorite." CONTRIBUTING.md can be slightly more conversational.
- **No personal anecdotes or identifying details.** Keep the plan generic so any reader can use it.
- **AWS service names** follow AWS's own capitalization: `Amazon S3`, `AWS Lambda`, `DynamoDB`, `CloudFront`, etc.
- **Tables** for lists of resources with 2+ columns of metadata. Bullets for simple lists.
- **Hyphens** in markdown bullets, not asterisks: `-` not `*`.
- **Line length** is not enforced — let Markdown wrap naturally.
## Review process
 
- A maintainer will review within roughly a week.
- Expect feedback. Most PRs need at least one round of revision.
- PRs that change the structure of the plan (new phases, reordering) will usually be asked to start as a discussion issue first.
- Small, well-scoped PRs get merged fastest.
## Code of conduct
 
Be respectful. Disagree with ideas, not people. No harassment, personal attacks, or dismissive behavior toward anyone's experience level. Maintainers reserve the right to close PRs or issues from contributors who repeatedly violate this.
 
## License
 
By contributing, you agree that your contributions will be licensed under the same [MIT License](LICENSE) that covers the rest of the project.
