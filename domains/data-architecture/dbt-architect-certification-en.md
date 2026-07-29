# dbt Architect Certification — Consolidated Study Notes

> Compiled from the [dbt Certified Architect Path (learn.getdbt.com)](https://learn.getdbt.com/learn/learning-path/dbt-certified-cloud-architect), the [official exam page](https://www.getdbt.com/certifications/dbt-architect-certification-exam), the [dbt Labs Study Guide PDF v6.3](https://www.getdbt.com/dbt-assets/dbt-certificate-study-guide-for-cloud-architect), and docs.getdbt.com.
> Source material has been paraphrased and summarized to comply with content licensing restrictions.
> Vietnamese version: [dbt-architect-certification.md](./dbt-architect-certification.md)
> Last updated: 2026-07.

---

## Table of contents

1. [Exam overview](#1-exam-overview)
2. [Blueprint — the 8 assessed topics](#2-blueprint--the-8-assessed-topics)
3. [Official learning path (6 milestones) — with video links](#3-official-learning-path-6-milestones)
4. [Detailed study notes by topic](#4-detailed-study-notes)
5. [The 10 official sample questions + answers + rationale](#5-the-10-official-sample-questions)
6. [Where people lose the most points](#6-where-people-lose-the-most-points)
7. [4–6 week study plan + final-week checklist](#7-46-week-study-plan)
8. [References](#8-references)

---

## 1. Exam overview

| Item | Detail |
|---|---|
| Name | dbt Architect Certification Exam (launched as "dbt Cloud Architect") |
| Duration | 2 hours |
| Questions | 65, plus an **undisclosed number of unscored items** that are indistinguishable from scored ones |
| Passing score | 65% (~43 correct) |
| Scoring | 1 point per correct answer, 0 for incorrect, **all questions weighted equally**, no negative marking |
| Format | Online proctored, registration via [Talview](https://pages.talview.com/dbtlabs/certifications/) |
| Browser | Caveon Web browser |
| Price | USD 200 per attempt (no extra fee for Coalesce premium attendees; discounts for dbt Labs SI Partners) |
| Languages | The study guide PDF still says "English only"; the current exam page lists **English / Japanese / French** |
| Results | Score shown immediately after submission |
| Validity | **2 years** from the award date |
| Retakes | Allowed, fee payable each time. Free reschedule/cancel up to 24 hours before the slot. No refunds for no-shows |

### Who it's for and assumed background

- dbt Labs recommends SQL proficiency plus **at least six months administering an Enterprise dbt account**.
- Practical prerequisite for the learning path: finish **dbt Fundamentals**, ideally hold the **dbt Analytics Engineering Certification** first.
- Be familiar with the **ADLC (Analytics Development Lifecycle)** — the framework dbt Labs uses as an implementation lens for dbt architecture.
- This is an **admin/platform** exam, not a model-development exam. It deliberately avoids warehouse-specific or Git-provider-specific trivia and tests broadly applicable best practices instead.

### Question types (it is not just multiple choice)

| Type | Tactical note |
|---|---|
| Multiple choice (single or multiple answer) | Multi-answer items state it explicitly, e.g. "2 possible solutions" |
| Fill-in-the-blank | You must recall exact setting names, prefixes, commands |
| Matching | Permission set ↔ capability, job type ↔ trigger |
| Hotspot | Click the correct region of a UI screenshot or diagram |
| Build list | Put steps or job commands in the **correct order** |
| **DOMC** (Discrete Option Multiple Choice) | Options appear one at a time; you answer yes/no to each and **cannot revisit**. Elimination doesn't work, so you need real recall |

DOMC costs the most points. With DOMC, answer the question in your head **before** reading the first option.

Time budget: 65 questions in 120 minutes ≈ **1 minute 50 seconds per question**. Flag and skip anything that stalls you — except DOMC items, which you cannot return to.

---

## 2. Blueprint — the 8 assessed topics

This is the official topic outline dbt Labs' SMEs used to write and review every exam item. dbt Labs does **not** publish per-topic weightings (all questions are weighted equally).

### Topic 1 — Configuring dbt data warehouse connections
- Understanding how to connect the warehouse
- Configuring IP whitelist
- Creating and testing a connection for the project
- Authenticating through OAuth to access data in dbt
- Adding Client ID and Secret for OAuth

### Topic 2 — Configuring dbt git connections
- Connecting the git repo to dbt
- Setting up integrations with git providers

### Topic 3 — Creating and maintaining dbt environments
- Access control across different environments
- Determining when to use a service account
- Rotating key pair authentication via the API
- Environment variables
- Creating a new deployment environment
- Setting a default schema/dataset per environment
- Custom branches and how to attach them to environments
- Configuring deferral to other environments

### Topic 4 — Creating and maintaining job definitions
- Setting up a CI job with deferral
- Understanding the steps within a dbt job
- Scheduling a job
- Implementing run commands in the correct order
- Creating a new job
- Optional settings: environment variable overrides, threads, deferral, target name, dbt version override
- Generating documentation in a job so it populates dbt Catalog
- Job chaining (trigger a job after another job completes)
- Configuring Advanced CI
- Configuring self-deferral
- Knowing **which type of deferral** fits which situation

### Topic 5 — Configuring dbt security and licenses
- Creating service tokens for API access
- Assigning permission sets
- Creating license mappings
- Adding and removing users
- Adding an SSO application for dbt Enterprise
- Creating and assigning RBAC

### Topic 6 — Setting up monitoring and alerting for jobs
- Email notifications
- Webhooks for event-driven integrations with other systems

### Topic 7 — Setting up a dbt mesh and leveraging cross-project references
- Setting up additional dbt projects
- How environment types relate to cross-project references
- Model governance

### Topic 8 — Configuring and using dbt Catalog
- Using Catalog to understand lineage, troubleshoot, and optimize cost/performance
- Using Catalog to find public models and cross-project references

---

## 3. Official learning path (6 milestones)

Source: [dbt Certified Architect Path](https://learn.getdbt.com/learn/learning-path/dbt-certified-cloud-architect) — the path page itself opens with a 3:23 intro video.

Legend: 🎥 = **contains video** (Video / Course / MicroCourse on dbt Learn are all video + quiz) · 📄 = reading (doc or article) · **[R]** Required · **[E]** Elective

### Milestone #1 — Setting up dbt Connections

| | Item | Type | Link |
|---|---|---|---|
| **[R]** | dbt Architect Certification Learning Path Overview | 🎥 Video | [open](https://learn.getdbt.com/courses/dbt-architect-certification-learning-path-overview) |
| **[R]** | dbt and Data Platforms (~2h) | 🎥 Course | [open](https://learn.getdbt.com/courses/dbt-cloud-and-data-platforms) |
| **[R]** | Configuring public IP restrictions | 📄 Resource | [open](https://learn.getdbt.com/courses/configuring-public-ip-restrictions) · [docs](https://docs.getdbt.com/docs/cloud/secure/ip-restrictions) |
| **[R]** | About data platform connections | 📄 Resource | [open](https://learn.getdbt.com/courses/about-data-platform-connections) |
| **[R]** | Single sign-on (SSO) overview | 📄 Resource | [open](https://learn.getdbt.com/courses/single-sign-on-sso-overview) · [docs](https://docs.getdbt.com/docs/cloud/manage-access/sso-overview) |
| **[E]** | Git Fundamentals | 🎥 Course | [open](https://learn.getdbt.com/courses/git-fundamentals) |
| **[R]** | Connect to GitHub | 📄 Resource | [open](https://learn.getdbt.com/courses/connect-to-github) |
| **[R]** | Connect to GitLab | 📄 Resource | [open](https://learn.getdbt.com/courses/connect-to-gitlab) |
| **[R]** | Connect to Azure DevOps | 📄 Resource | [open](https://learn.getdbt.com/courses/connect-to-azure-devops) |
| **[R]** | Connect with Git clone | 📄 Resource | [open](https://learn.getdbt.com/courses/connect-with-git-clone) |
| **[E]** | dbt and Snowflake for Admins (~1h) | 🎥 Course | [open](https://learn.getdbt.com/courses/dbt-cloud-and-snowflake-for-admins) |

The study guide PDF also lists the other platform admin courses — pick the one matching your warehouse:
🎥 [Databricks for Admins](https://learn.getdbt.com/courses/dbt-cloud-and-databricks-for-admins) · 🎥 [BigQuery for Admins](https://learn.getdbt.com/courses/dbt-cloud-and-bigquery-for-admins) · 🎥 [Redshift for Admins](https://learn.getdbt.com/courses/dbt-cloud-and-redshift-for-admins)

### Milestone #2 — Configuring and Managing Projects

| | Item | Type | Link |
|---|---|---|---|
| **[R]** | dbt Environments (~1h) | 🎥 Course | [open](https://learn.getdbt.com/courses/dbt-environments) |
| **[R]** | Getting Started with git branching strategies in dbt | 📄 Article | [open](https://learn.getdbt.com/courses/getting-started-with-git-branching-strategies-in-dbt) |
| **[R]** | dbt deferral | 🎥 MicroCourse | [open](https://learn.getdbt.com/courses/dbt-deferral) |
| **[E]** | Using defer in dbt | 📄 Resource | [open](https://learn.getdbt.com/courses/using-defer-in-dbt) |
| **[R]** | **Advanced Deployment (4h)** — the single most important course on the path | 🎥 Course | [open](https://learn.getdbt.com/courses/advanced-deployment) |
| **[R]** | Using threads | 📄 Resource | [open](https://learn.getdbt.com/courses/using-threads) |
| **[R]** | dbt metadata | 📄 Resource | [open](https://learn.getdbt.com/courses/generating-dbt-metadata) |
| **[R]** | Deploy jobs | 📄 Resource | [open](https://learn.getdbt.com/courses/deploy-jobs) · [docs](https://docs.getdbt.com/docs/deploy/deploy-jobs) |
| **[R]** | Advanced Continuous Integration (CI) | 📄 Resource | [open](https://learn.getdbt.com/courses/advanced-continuous-integration-ci) · [docs](https://docs.getdbt.com/docs/deploy/advanced-ci) |

### Milestone #3 — Security and Monitoring

| | Item | Type | Link |
|---|---|---|---|
| **[R]** | dbt Authentication Fundamentals (SSO, groups, inviting users, MFA) | 🎥 Video | [open](https://learn.getdbt.com/courses/dbt-authentication-fundamentals) |
| **[R]** | Service account tokens | 📄 Resource | [open](https://learn.getdbt.com/courses/service-account-tokens) · [docs](https://docs.getdbt.com/docs/dbt-cloud-apis/service-tokens) |
| **[R]** | dbt Licenses and Permissions | 🎥 Course | [open](https://learn.getdbt.com/courses/dbt-licenses-permissions) |
| **[R]** | Enterprise permissions | 📄 Resource | [open](https://learn.getdbt.com/courses/enterprise-permissions) · [docs](https://docs.getdbt.com/docs/cloud/manage-access/enterprise-permissions) |
| **[E]** | Self-service Starter account permissions | 📄 Resource | [open](https://learn.getdbt.com/courses/self-service-starter-account-permissions) |
| **[R]** | Securing your account through SSO & RBAC | 📄 Article | [open](https://learn.getdbt.com/courses/establishing-dbt-cloud-securing-your-account-through-sso-rbac) |
| **[R]** | Job Notifications | 📄 Resource | [open](https://learn.getdbt.com/courses/job-notifications) · [docs](https://docs.getdbt.com/docs/deploy/job-notifications) |
| **[R]** | Webhooks (~1h) | 🎥 Course | [open](https://learn.getdbt.com/courses/webhooks) |

The study guide PDF adds per-IdP SSO/RBAC courses (all 🎥 on dbt Learn): RBAC with **dbt & Okta**, SSO with **Entra ID**, SSO with **Google Workspace**, SSO with **Okta** — find them in the [Course Catalog](https://learn.getdbt.com/catalog).

### Milestone #4 — Governance and Discovery

| | Item | Type | Link |
|---|---|---|---|
| **[R]** | dbt Mesh | 🎥 Course | [open](https://learn.getdbt.com/courses/dbt-mesh) |
| **[R]** | Project dependencies | 📄 Resource | [open](https://learn.getdbt.com/courses/project-dependencies) · [docs](https://docs.getdbt.com/docs/collaborate/govern/project-dependencies) |
| **[R]** | dbt Catalog | 🎥 Course | [open](https://learn.getdbt.com/courses/dbt-catalog) |

### Milestone #5 — Exam Preparation

| | Item | Type | Link |
|---|---|---|---|
| **[R]** | dbt Cloud Architect Exam Study Guide | 📄 Resource | [open](https://learn.getdbt.com/courses/dbt-cloud-architect-exam-study-guide) · [direct PDF](https://www.getdbt.com/dbt-assets/dbt-certificate-study-guide-for-cloud-architect) |
| **[E]** | **Pro Tips for dbt Certifications** — Hope Watson (dbt Labs Resident Architect) on exam strategy | 🎥 Video | [open](https://learn.getdbt.com/courses/pro-tips-for-dbt-certifications) |

### Milestone #6 — Exam Registration

| | Item | Link |
|---|---|---|
| **[E]** | Register for dbt Cloud Architect Exam | [open](https://learn.getdbt.com/courses/register-for-dbt-cloud-architect-exam) · [Talview](https://pages.talview.com/dbtlabs/certifications/) |
| **[E]** | Learning Path Survey (5 min) | [open](https://learn.getdbt.com/courses/learning-path-survey) |

### Foundational videos worth doing first

- 🎥 [dbt Fundamentals (~5h)](https://learn.getdbt.com/courses/dbt-fundamentals) — the knowledge prerequisite.
- 🎥 [dbt Certified Developer Path](https://learn.getdbt.com/learning-paths/dbt-certified-developer) — if you don't hold the Analytics Engineering cert yet.

---

## 4. Detailed study notes

### 4.1 Data platform connections & authentication (Topic 1)

**Connection architecture**
- Connections are configured at the **account level** and are **reusable** across projects and environments. One project can use multiple connections of the same warehouse type.
- Key design consequence: you do **not** duplicate projects for dev vs prod. Use *environment-level isolation* — each environment points at its own connection/credentials.
- `extended_attributes` lets you override profile attributes per environment that the UI doesn't expose.
- Credentials are split into two layers: the **connection** (host, account, warehouse, database) at account level, and **credentials** (user, role, schema, key) per environment and per user.

**Authentication mechanisms — the most heavily tested area**

| Mechanism | Where it applies | Notes |
|---|---|---|
| Username + password | Dev & Deployment | Simplest, least secure |
| **Key pair** (Snowflake) | Deployment (service account) | Should be **rotated regularly**; rotation can be driven via the **Admin API** |
| **OAuth / SSO OAuth** | **Development environments only** | Token lifetime is dictated by the data platform; users must re-authorize when it expires |
| Service account / service principal | Deployment (staging, prod) | **Best practice for every deployment environment** |

> Rule to memorize: **never use SSO/OAuth for staging or production**, because expiring sessions/tokens cause automated jobs to fail. Deployment always uses a **service account**.

- Setting up OAuth: Snowflake OAuth, Databricks OAuth, BigQuery OAuth, external OAuth (Okta/Entra) — each requires a **Client ID + Client Secret** entered in dbt, plus dbt's redirect URI.
- Warehouse grants by persona: developers get **read** on production schemas plus **read/write** on their own dev schema; the production service account gets **read/write** on production schemas including snapshot schemas.

**Network security**
- **IP restrictions**: available on **Enterprise+ / Virtual Private** only. Configured at `Account Settings → IP Restrictions` using an **allowlist** and a **blocklist**. It blocks service tokens, API requests using personal tokens, and the UI alike. You **must allowlist your Git provider's IPs** (inbound webhooks from GitHub/GitLab/ADO) or CI breaks.
- **dbt egress IPs**: must be allowlisted on the warehouse side (Access, Regions & IP addresses).
- **PrivateLink**: requires **Business Critical (Enterprise+ / Virtual Private)**. This is the answer for *data residency* / GDPR / multi-region scenarios: stand up a **separate PrivateLink endpoint per region** and point separate projects at the respective endpoints — you do **not** buy another account, and you do **not** use cross-platform Mesh to bridge the regions (the goal is data isolation).

### 4.2 Git connections (Topic 2)

| Provider | Native integration | Automated CI job | Git clone | Plans |
|---|---|---|---|---|
| GitHub | ✅ (dbt GitHub App) | ✅ | ✅ | All plans |
| GitLab | ✅ (OAuth app) | ✅ | ✅ | All plans |
| Azure DevOps | ✅ (service principal recommended; OAuth 2.0) | ✅ | ✅ | **Enterprise / Enterprise+** (Starter/Developer can only use a deploy key, no automated CI) |
| BitBucket, AWS CodeCommit, others | ❌ | ❌ | ✅ | Use custom pipelines + Administrative API |

- **GitLab Free**: merge requests still trigger CI jobs, but **CI job status is not reported back** to GitLab.
- **Git clone**: uses an SSH URL plus a **deploy key** generated by dbt (needs write access on the repo). No webhooks means **dbt won't auto-drop the temporary CI schema**; you trigger CI via the Administrative API and clean up yourself.
- The project-level repo connection is separate from each developer's **personal git credentials** (used by the IDE/CLI) — developers authorize their own GitHub profile.
- **Branching strategies**:
  - *Direct promotion*: a single `main` branch; developer branches merge straight into it.
  - *Indirect promotion*: an intermediate branch (`qa`/`staging`); developer branches → `staging` → `main`. Requires a **custom branch** on the matching environment, branch protection rules, and a distinct **hotfix** process.
- **Custom branch** on an environment: required whenever an environment must check out something other than `main` (e.g. a staging environment on the `staging` branch, or a CI environment bound to a specific target branch so it only runs for PRs against that branch).

### 4.3 Environments (Topic 3)

**Types**
- **Development environment**: exactly **one** per project; powers Studio IDE / CLI; OAuth allowed here.
- **Deployment environment**, with **three types**:
  - **Production** — builds production data. Only **one environment can be marked production** per project; it is the *source of truth* and a hard requirement for **dbt Catalog** and **cross-project references**.
  - **Staging** — gives developers access to deployment workflows while limiting access to production data; typically tied to a long-lived `staging` branch.
  - **General** — general-purpose deployment; **not recommended** as the final production environment.

**What an environment determines at run time**: the dbt version / release track, the connection plus target database and schema, and the version of the code (branch) that executes.

**Environment variables — exact details matter**
- Valid prefixes: **`DBT_`**, **`DBT_ENV_SECRET_`**, **`DBT_ENV_CUSTOM_ENV_`**.
- Keys are **uppercased** and **case sensitive** — `{{ env_var('DBT_KEY') }}` must match exactly.
- `DBT_ENV_SECRET_*` values are **scrubbed from all logs and error messages**.
- dbt ships some pre-defined variables that **cannot be overwritten**.
- **Order of precedence (lowest → highest)**:
  1. The `default` argument in `{{ env_var('KEY', 'default') }}`
  2. **Project default**
  3. **Environment level**
  4. **Job override** or **personal override** in the Studio IDE
- Corollary: deleting a job-level override falls back to the **environment level** value, *not* the project default.
- Missing at every level → compilation error "Env var required but not provided".
- Environment variables are **not** the same thing as project variables (`vars:`).

**Schema / database / target**
- Each environment sets its own **target schema/dataset**, so the same job materializes into different schemas per environment. This is the primary mechanism.
- For more complex logic, **override the `generate_schema_name` macro** (and `generate_database_name`, `generate_alias_name`).
- A model-level `+schema:` config only adds a **custom schema suffix**; on its own it does not vary by environment.
- **Custom target name** (`{{ target.name }}`) lets project code branch on context (e.g. CI processes only a subset of data).

**Deferral (defer)**
- Defer builds **only changed models**, resolving unchanged parents from **another environment's manifest** instead of rebuilding them.
- It requires a **manifest from a previous invocation** (`--state`, optionally a separate `--defer-state`). Combined with the `state:modified+` selector this gives you "Slim CI".
- In the dbt platform: enable *defer to another environment* on the environment (for IDE/CLI development) or on the job (*Compare changes against an environment*).
- **Resolution order**: dbt prefers objects that already exist in the current run's target schema; only nodes not found there are resolved from the deferred environment.
- **Self-deferral**: a job defers to **its own** most recent successful artifacts — useful when there is no suitable production environment to compare against.
- **defer vs `dbt clone`**: clone creates copies (zero-copy where the platform supports it) of production objects into a dev schema — use it when objects must physically exist; defer only redirects references and is cheaper.
- **Threads**: control connection parallelism. More threads run faster but consume warehouse concurrency. Platform jobs default to **4**.

### 4.4 Jobs (Topic 4)

**Job types and triggers**

| Type | Triggers |
|---|---|
| **Deploy job** | Schedule (days/times) · **custom cron** · **trigger on job completion** (job chaining) · API · Run now |
| **CI job** | Pull request opened or new commit pushed (with an optional *Run on draft PR* setting) |
| **Merge job** | When a PR is merged into a branch (continuous deployment) |

- The scheduler runs on **UTC** and does **not** adjust for local timezone or daylight saving.
- **Job chaining**: run a job after an upstream job completes (Starter and above); used to separate staging → production and to coordinate jobs across projects in a Mesh.

**Inside a job**
- **Commands**: `dbt deps` runs automatically at the start of a run. Best practice is one purpose per step — `dbt build --select ...` first, with tests, snapshots, seeds, and full-refresh as separate steps so failures are easy to isolate.
- The **Run source freshness** checkbox runs `dbt source freshness` **before** the other commands.
- The **Generate docs on run** checkbox produces docs artifacts that **populate dbt Catalog**. Enable it on production jobs; do **not** enable it on CI jobs.
- Advanced settings: **environment variable overrides**, **target name**, **dbt version override** (only for version upgrades), **threads**, **run timeout**.
- Key artifacts: `manifest.json` (logical state), `run_results.json`, `catalog.json`.

**CI jobs — the standard configuration**
- Default command: `dbt build --select state:modified+`.
- **State comparison only works when a deferred environment is selected**, so deferral defaults to **Production**.
- Builds land in a **temporary schema unique to each PR**; dbt drops it automatically when the PR is closed or merged, but **only with a native git integration** (webhook driven). API-triggered CI requires manual cleanup.
- Put the CI job in a **dedicated deployment environment** pointing at a staging database to isolate it from production.
- Related features: **concurrent CI checks**, **smart cancellation of stale builds** (Starter/Enterprise tiers), and **SQL linting via SQLFluff** as a first step, configurable to *stop* or *continue on error*.
- Triggering CI via the API: `job_type: ci`, and the payload needs `github_pull_request_id` / `gitlab_merge_request_id` / `azure_devops_pull_request_id` / `non_native_pull_request_id`, plus `git_sha` or `git_branch`.
- **Semantic validation in CI**: `dbt sl validate --select state:modified+`.

**Advanced CI — compare changes**
- Requires an **Enterprise-tier** account with the feature enabled by an admin, which surfaces the **`dbt compare`** checkbox in CI job settings.
- Supported platforms: BigQuery, Databricks, Postgres, Redshift, Snowflake.
- Compares the **last applied state of the production environment** against the **latest commit on the PR**, on every PR open or push.
- Reports differences in **primary keys, rows, and columns**; visible in the **Compare tab** of the job run details and summarized as a **comment on the PR** in your Git provider.
- Record-level analysis needs a **primary key constraint** or a **uniqueness test**; otherwise you get a "Primary key missing" message.
- Configuring `event_time` on models/seeds/snapshots/sources limits comparison to the **overlapping timeframe**, which avoids false "deleted rows" when CI builds only a subset, and false "new rows" when CI data is fresher than production.
- Caching: up to **100 sample records per modified model**, retained for up to **30 days**, encrypted and stored in the account's region. Runs older than 30 days show an expired-data message instead of results.
- Default timeout when `dbt compare` is on: **3600 seconds**.
- Limitation: CI and production models must live on the **same database host/connection**. Deferring to an environment on a different host breaks compare changes.

**Hooks (not in the study guide, but the exam asks)**
- `pre-hook` / `post-hook` at model level; `on-run-start` / `on-run-end` at project level.
- The trap: hooks do **not** solve write-permission problems, because deployment credentials need write access **before** they can create or alter a table. Granting via a hook only helps *after* the object exists.

**Source freshness (tested deeper than expected)**
- Declare `loaded_at_field` plus `freshness: {warn_after, error_after}` on sources, or use warehouse metadata-based freshness.
- `dbt source freshness` produces `sources.json`; results show up in Catalog and can trigger a **Warns** notification.

### 4.5 Security, licenses & RBAC (Topic 5)

**License types (purchased per seat)** — `Developer`, `Read-only`, `IT`.
> **Licenses always override group permission sets.** A user with a Read-only license inside an Account Admin group still **cannot** perform admin actions.

**Groups + permission sets = RBAC**
- Permission sets are assigned to **groups**; groups are assigned to **users** (or mapped from an IdP). A group can carry multiple permission sets, and **the more permissive assignment wins**.
- Two categories: **account-level** (account administration: inviting users, SSO, creating groups, billing) and **project-level** (environments, IDE, jobs).

Permission sets (Enterprise / Enterprise+) — you need to distinguish these; matching questions are common:

| Permission set | Level | Distinguishing trait |
|---|---|---|
| **Account admin** | Account | Highest access, unrestricted. Default for whoever creates the account and for the Owner group |
| **Admin** | **Project** | Unrestricted on **existing** projects, cannot create new ones; can invite users but **cannot create groups**. Default for the Member group |
| **Project creator** | Account | The only set besides Account admin that can **create new projects**; can create/edit connections, invite users, create groups, assign licenses |
| **Account viewer** | Account | Read-only across the account **including audit logs** with sensitive content. No IDE |
| **Stakeholder / Read-Only** | Project | Like Account viewer but **without** account settings, billing, or sensitive audit log content |
| **Security admin** | Account | Users, groups, licenses, **authentication & SSO**, **IP restrictions**, can view service tokens. No jobs/runs/environments/IDE. Included by default with the **IT license** |
| **Billing admin** | Account | Billing section only |
| **Analyst** | Project | Full IDE access plus own personal credentials; **read-only** environment configs; can view but not edit jobs |
| **Developer** | Project | Create, edit, test code in the IDE; read-only on environments, jobs, runs, Git config. ⚠️ **Not** the same as the *Developer license* |
| **Database admin** | Project | Write access to **data platform configs inside environments** (credentials, warehouse, schema) plus environment variables and Semantic Layer; read-only on connections/repo/jobs |
| **Git admin** | Project | Create Git integrations and environment variables, edit project settings; **no IDE**; read-only account settings |
| **Job admin** | Project | Create/edit **jobs, runs, environment variables, data warehouse configs**; set up project integrations; read-only project configs |
| **Job creator** | Project | Create/edit/run jobs in assigned projects and environments; **cannot create/delete environments or edit env vars** |
| **Job runner** | Project | Run jobs and view outcomes only |
| **Job viewer** | Project | Read-only on job results, status, logs |
| **Team admin** | Project | Manage a team's project(s); read-only on many account settings (excluding billing, auth providers). Scope extendable via **environment-level permissions** |
| **Metadata** | Project | Read-only metadata via the **Discovery API** |
| **Notification Manager** | Account | Manage Slack/Teams/email notification rules **across all projects** without full Account admin; **cannot** connect/disconnect Slack or Teams (Account admin only) |
| **Semantic Layer** | Project | Query the Semantic Layer only (for service tokens) |
| **Cost Insights Admin / Viewer** | Both | Configure / view Cost Insights data |
| **Fusion admin** | — | Perform Fusion upgrades; **assignable to users only, not service tokens** |
| **Analyst read** (private beta) | Project | Read-only plus `user_credential_write` so users manage their own credentials without IDE access |
| **Manage marketplace apps** | Account | For marketplace apps (Snowflake Native App) |

> Frequently tested contrasts: **Git admin** (creates Git integrations and env vars, no IDE) vs **Team admin** (manages a team's projects, mostly read-only on account settings) vs **Job admin** (can edit env vars and warehouse configs) vs **Job creator** (cannot edit env vars or environments).

**SSO & provisioning**
- Supported: **SAML 2.0** (generic), **Okta**, **Google Workspace**, **Microsoft Entra ID**; there is also **Auth0** migration documentation.
- **JIT provisioning**: the user record is created in dbt on first IdP login; **IdP-initiated login** is supported; each account has its own **login slug** and SSO can be **enforced**.
- **SCIM** (Okta, Entra ID): automates user provisioning/deprovisioning and **license assignment** — this is the answer whenever a question asks how new hires automatically get a Developer license and land in the right group.
- **License mapping**: map IdP groups/attributes to dbt license types.
- **MFA** is configured on the IdP side.

**Tokens**
- **Service account tokens** belong to the **account**, not a user. On Enterprise they accept **any permission set**; scope is **all projects** or **specific projects**; multiple permission sets can be attached to one token.
  - Creating one requires a **Developer license** plus **Account admin** permissions.
  - The token value is **shown once** — save it immediately. Rotate periodically and verify jobs still run afterwards.
  - Starter/Developer plans can only apply Semantic Layer; legacy Team plans are limited to Account Admin, Member, Job Admin, Read-Only, Metadata, Semantic Layer.
- **Personal access tokens (PATs)** act on behalf of a user and inherit that user's permissions — not suitable for automation.
- **Audit log**: Enterprise, used to trace configuration changes.

### 4.6 Monitoring & alerting (Topic 6)

**Job notifications**
- Four outcomes: **Succeeds**, **Warns**, **Fails**, **Is canceled**.
  - **Warns** is triggered by **warning-level log lines from data tests or source freshness**, not by the overall run status — a job showing "success" in the UI can still fire a Warns notification.
- Channels: **Email**, **Slack (user-linked)**, **Slack (account-level)**, **Microsoft Teams**. If the native Teams integration isn't usable, send to the **channel's email address** as an external email.
- Permissions: developer users configure notifications for themselves; broader configuration requires **Account Admin / Owner / Member** or the **Notification Manager** permission set.

**Webhooks (outbound, event driven)**
- Three events: **`job.run.started`**, **`job.run.completed`** (covers both success and failure), **`job.run.errored`**.
- Created via the **UI** or the **API**. dbt sends a **JSON payload** to your endpoint URL.
- dbt **retries five times**; delivery logs are kept for **7 days** (the *Recent Deliveries* section); the **timeout is 10 seconds** — an endpoint that replies after 10s is treated as a failure even if the client considers it a success.
- Verify payloads using the **HMAC signature** in the request header.
- Write access to webhooks (Enterprise): **Account Admin, Admin, or Developer** — the same sets apply to both the UI and service tokens.
- **Webhooks vs polling**: to kick off an external pipeline (Airflow and similar) the moment a job finishes, use a **`job.run.completed` webhook**, not scheduled polling of the Admin API. Job chaining works **inside dbt only** and cannot trigger an external DAG.
- Common uses: open a PagerDuty incident, push to Slack/Teams, start a downstream DAG.
- Deeper observability: the **Discovery API** (metadata, freshness, test results) plus the **Administrative API** (run history, triggering).
- Operational best practices: route production and staging alerts differently; watch run-duration trends; add a delayed backup job for critical pipelines.

### 4.7 dbt Mesh & model governance (Topic 7)

**Model governance rests on three pillars**

1. **`access`** — the access modifier on a model:

| access | Referenceable from |
|---|---|
| `private` | The same **group** |
| `protected` | The same **project** (or a project that installed it as a package) — **default** |
| `public` | Any group, package, or project. After changing it, **rerun a production job** to apply |

2. **`groups`** — cluster models by owner/domain. A model belongs to exactly **one** group and groups **cannot nest**; you can apply a group to a whole subdirectory in `dbt_project.yml`, and a model-level config overrides it.
3. **`contracts`** + **`versions`** — contracts (`enforced: true` with `data_type`/constraints) block breaking changes; versioning (`v1`, `v2`, `latest_version`, `deprecation_date`) enables controlled deprecation. Treat public models like **APIs**.

> Note: governance features apply to **models only** — not snapshots, seeds, or sources.

**Cross-project references**
- Declared in **`dependencies.yml`** (distinct from `packages.yml`):
  ```yaml
  projects:
    - name: jaffle_finance
  ```
  then a two-argument ref: `{{ ref('jaffle_finance', 'fct_orders') }}` (optionally with a version).
- A **package** pulls the entire source code into your project. A **project dependency** has dbt resolve the reference **on the fly** through a metadata service; you never parse or run the upstream models, you consume them as a dataset API.

**Prerequisites for cross-project refs (heavily tested)**
- Enterprise / Enterprise+.
- The upstream model has **`access: public`** and has had **at least one successful job run after** the access change.
- The upstream project has a **Production deployment environment** with **at least one successful deploy job** there to generate **`manifest.json`**.
- If the upstream project also has a **Staging environment**, it needs at least one successful deploy job there too for references to resolve correctly.
- **Project names must be unique in the account** and are **case sensitive** — `dbt_project.yml` must match `dependencies.yml` exactly (`jaffle_marketing` ≠ `JAFFLE_MARKETING`).
- Do not split projects by environment (avoid `X - Dev` and `X - Prod`); use **environment-level isolation** plus **Connections**.

**Other**
- **Bidirectional dependencies at the project level** are valid as long as no cycle exists at the model level.
- **Cross-platform Mesh**: references between projects on different data platforms. But if the requirement is **regional data isolation**, cross-platform Mesh is the **wrong** answer.
- **Hybrid Mesh**: combines self-hosted dbt Core projects with the dbt platform.

### 4.8 dbt Catalog (Topic 8) — formerly dbt Explorer

**Prerequisites**
- Starter / Enterprise / Enterprise+ plan.
- A **production or staging deployment environment** per project.
- **At least one successful job run** in that environment. **CI jobs do not update Catalog.**
- For complete docs, enable **Generate docs on run** on the production job.

**What it's for**
- View all **resources** (models, tests, sources, metrics, exposures) at the **latest production state**.
- Model-level **lineage** and **column-level lineage**; **project-level lineage** when using Mesh.
- Find **public models** and **cross-project references** — where downstream teams shop for the "API" they will consume.
- **Model performance** and **recommendations** for cost/performance tuning.
- **Test** status, **source freshness**, **owners/groups**, contracts and versions.
- Troubleshoot by walking up and down lineage instead of guessing.
- Metadata is surfaced through the **Discovery API**; you can **ingest external warehouse metadata** to see assets not defined in dbt. Auto-exposures for Tableau.

---

## 5. The 10 official sample questions

Source: the [dbt Labs exam page](https://www.getdbt.com/certifications/dbt-architect-certification-exam#sample-questions) and the study guide PDF (first four). ✅ = correct answer.

### Question 1 — Connections & authentication
**Why should you avoid SSO-based connections for staging and production deployment environments in dbt?**

- ✅ **A.** They depend on authentication sessions that can expire or need re-authentication, causing unexpected job failures in automated deployments.
- B. They cannot connect to cloud warehouses because the authentication protocols are incompatible.
- C. They prevent you from managing environment variables needed for production.
- D. They can only be used by users with the Account Admin role.

**Rationale**: dbt supports OAuth in **Development environments only**. Once a user authorizes dbt through their identity provider, dbt receives an access token used to open the connection and run queries in Studio. The **token lifetime is dictated by the data platform**; when it expires the user must re-authorize. That's why deployment credentials should be a **service account**. B is wrong because it's technically possible to connect that way, just not advisable. C is wrong because the authentication method doesn't restrict env var usage. D is wrong because any user with a **Developer license** can use SSO OAuth regardless of permissions.

### Question 2 — Environment-scoped permissions
**A snapshot's `target_schema` is `prod_snapshot`. You want developers to read `prod_schema` in dev but give the production job read and write. How?**

- A. Use a `post-hook` to grant read and write in the snapshot config.
- ✅ **B.** Use a **service account with read and write** in the deployment environment settings.
- C. Use `on-run-end` to grant read and write in the snapshot config.
- D. Assign the developer the **Job Admin** role.

**Rationale**: The point is that different users and service accounts need different permissions on different database objects. Developers need read on `prod_schema` but not write on `prod_snapshot`. Production deployment credentials need read and write on both. The clean solution is **separate credentials per environment** with the right grants in the data platform. A and C fail because production credentials need write access **before** they can create or alter the table in `prod_snapshot`; granting afterwards doesn't address the requirement. D is wrong because **Job Admin** lets a developer create and edit jobs, runs, environment variables, and warehouse configs, but doesn't change their personal access to database objects.

### Question 3 — Environment variable precedence

| Key | Project Default | Production | Development |
|---|---|---|---|
| `DBT_ENV_VALUE` | `not_set` | `prod` | `dev` |

A job overrides this variable with `finance`. **Which value is used if that job-level configuration is removed?**

- A. The project default `not_set`
- B. The `default` argument passed to the `env_var` Jinja function in code
- ✅ **C.** The value assigned to the **environment** the job runs in
- D. The job-level environment variable is required and cannot be removed

**Rationale**: Project Default is for catch-all defaults or project-wide tokens/secrets. Values set at the **environment level take priority over the project default**. A job **inherits** the environment value, and a job-level override takes precedence while it exists; remove it and the value falls back to the environment (here, `prod`). A is wrong because Project Default sits below the environment. B is wrong because the Jinja `default` argument sits below both Project Default and the environment. D is wrong because job-level overrides are optional and removable.

### Question 4 — Environment variables (choose 2)
**Which statements about environment variables are true?**

- ✅ Environment variables must be prefixed with **`DBT_`**, **`DBT_ENV_SECRET_`**, or **`DBT_ENV_CUSTOM_ENV_`**.
- ✗ Prefixes are `DBT_`, `DBT_SECRET_ENV`, or `DBT_CUSTOM_ENV_`.
- ✗ Environment variable keys are **case insensitive**.
- ✗ dbt has pre-defined variables that **can** be overwritten.
- ✅ dbt has pre-defined variables that **cannot** be overwritten.
- ✗ Environment variables and project variables are synonymous.

**Rationale**: dbt enforces these prefixes to separate concerns and make usage intentional. It can't inspect every env var on the system, so namespacing tells it which ones are opt-in for redaction, metadata capture, or general use. Keys are uppercased by convention to avoid ambiguity.

### Question 5 — Per-environment schemas (choose 2)
**You want objects to materialize into a different schema for each deployment environment. How?**

- ✗ Define `custom_schema` in each model's config block.
- ✅ **Define a target schema when setting up the environments.**
- ✅ **Use/override the `generate_schema_name` macro.**
- ✗ Define a target schema in the job settings.
- ✗ Use the `handle_existing_table` macro.

**Rationale**: dbt resolves a schema by combining the **target schema** with any custom schema logic. A per-environment target schema is the primary mechanism (dev/staging/prod each get their own). Overriding `generate_schema_name` lets you customize the resolution logic entirely. A model-level `custom_schema` only sets a suffix and doesn't vary by environment on its own. A job-level target schema overrides the environment setting but is a job concern, not an environment one. `handle_existing_table` is **not a real dbt macro** — it's a distractor.

### Question 6 — Deferral
**A team has a production deployment environment and wants developers to run `dbt build --select state:modified+` against production state, building only changed models without recomputing unmodified upstream dependencies. What should the architect configure?**

- ✗ Clone the production schema into a developer-specific schema using a post-hook.
- ✅ **Enable deferral on the development environment, pointing to production as the deferred environment.**
- ✗ Set a custom branch on the production environment for developers to target.
- ✗ Use environment variable overrides on each developer's job to point at the prod schema.

**Rationale**: Deferral lets dbt resolve unmodified models from the **production environment's manifest**, so developers build only their changed models and downstream dependents.

### Question 7 — CI jobs
**When a pull request is opened, dbt should run only changed models and their downstream dependencies, comparing against production state instead of rebuilding everything. Which job configuration achieves this?**

- ✗ A scheduled job with `dbt build --select state:modified+` and self-deferral enabled.
- ✅ **A CI job with deferral pointing to the production environment and the command `dbt build --select state:modified+`.**
- ✗ A merge job running `dbt run --full-refresh` on every PR.
- ✗ A triggered job via webhook that runs `dbt test` only.

**Rationale**: **CI jobs** are the job type designed for pull request triggers; deferring to production ensures the job only builds modified models by comparing against the production manifest.

### Question 8 — SSO / SCIM / RBAC
**Your organization uses Okta as its IdP. New employees who authenticate via SSO should **automatically** receive the "Developer" license and join the "Analytics" group, with no manual intervention. What should you configure?**

- ✗ Create a service token with the Developer role and share it with new employees.
- ✅ **Set up SCIM provisioning and configure license mappings and RBAC group assignments tied to Okta attributes.**
- ✗ Have each user self-register and request a license.
- ✗ Set the account default license to Developer so all SSO users inherit it, without RBAC.

**Rationale**: **SCIM** handles automated provisioning and deprovisioning; combined with **license mappings** and **RBAC rules**, users get the right license and group membership based on their Okta attributes.

### Question 9 — dbt Mesh
**A downstream project needs to reference a model from an upstream project in a dbt Mesh setup. The upstream model is currently `access: protected`. What must the upstream project owner change?**

- ✗ Set `access: public` and define it in the upstream project's `sources.yml`.
- ✅ **Set `access: public` and ensure the upstream environment is configured as a production environment type.**
- ✗ Set `access: private` and add the downstream project to an allowlist.
- ✗ No change needed — any model can be referenced across projects regardless of access level.

**Rationale**: Cross-project references in Mesh require **`access: public`**. The upstream environment must also be a **production environment type** so dbt can resolve the cross-project ref at run time.

### Question 10 — Webhooks vs polling
**You want to trigger a downstream pipeline in an external orchestrator (for example Airflow) the moment a dbt job succeeds, without polling the dbt API on a schedule. What's the recommended approach?**

- ✗ Set up email notifications and have Airflow parse the inbox.
- ✗ Poll job status from Airflow via the dbt API every 60 seconds.
- ✅ **Configure a webhook on the dbt job to send a `job.completed` event to Airflow's REST API endpoint.**
- ✗ Use job chaining in dbt to trigger the Airflow DAG as a final job step.

**Rationale**: Webhooks are dbt's event-driven integration mechanism. A webhook on the job-completed event **pushes** a notification to an external endpoint the instant the job finishes, eliminating polling.

---

## 6. Where people lose the most points

Synthesized from write-ups by people who passed ([Nikita Volynets](https://nikitavolynets.substack.com/p/how-to-pass-dbt-cloud-architect-exam), [Daniel Bostrom](https://www.thedataschool.co.uk/daniel-bostrom/dbt-architect-certification)) — paraphrased:

1. **Permissions.** Numerous and very detailed questions. You must separate **Git Admin vs Team Admin vs Job Admin vs Job Creator**, and know which sets are **account-level** vs **project-level**. Study [Enterprise permissions](https://docs.getdbt.com/docs/cloud/manage-access/enterprise-permissions) closely.
2. **Job configuration & source freshness.** Tested deeper than the learning path teaches — especially how **source freshness** and **docs on run** behave when enabled, and the differences between **CI jobs and production jobs**.
3. **Environments & defer.** Which environment defer uses, how dev/staging/prod differ and interact. Know **self-deferral** and when to choose which.
4. **Advanced CI.** What "compare changes" compares against what, where output lands, and its limitations.
5. **dbt Mesh.** Bidirectional dependencies, setup steps, cross-project job configuration, how environments in different projects interact. Hard without hands-on practice.
6. **Hooks.** Not in the study guide, yet present in an official sample question (Q2) — read up on `pre-hook`/`post-hook`/`on-run-start`/`on-run-end`.
7. The learning path teaches **core concepts**; the exam probes at **documentation depth**. Example: the path teaches RBAC best practices, but the exam asks for the **exact names of permission sets**. Reading the docs pages linked in the study guide is not optional.

---

## 7. 4–6 week study plan

| Week | Focus | Deliverable |
|---|---|---|
| 0 | Finish **dbt Fundamentals**. Read the study guide PDF end to end. Stand up a sandbox dbt account you can break freely | A written list of your weak spots |
| 1 | Milestone #1: connections, OAuth, IP restrictions, connecting all three Git providers. Docs: About data platform connections, Access/Regions/IP, Snowflake/Databricks/BigQuery/external OAuth | A connected project; you can explain the auth pattern per environment |
| 2 | Milestone #2, environments half: create dev/staging/prod, custom branches, the four-tier env var precedence, custom schemas/targets. Course **dbt Environments** | Three working environments plus a documented branching strategy |
| 3 | Milestone #2, jobs half: **Advanced Deployment (4h)**, deploy jobs, cron, job chaining, CI jobs, deferral, self-deferral, Advanced CI, threads | A runbook describing your job chaining and how deferral works |
| 4 | Milestone #3: licenses and permission sets (memorize the table), SSO, SCIM, license mappings, service tokens and rotation, notifications, webhooks | An RBAC and token audit checklist; one webhook firing on job failure |
| 5 | Milestone #4: build a two-project Mesh (producer/consumer), `access: public`, `dependencies.yml`, contracts and versions; enable docs generation and explore Catalog with column-level lineage | Lineage spanning both projects in Catalog |
| 6 | Review all eight topics, do the 10 sample questions under time pressure, watch 🎥 [Pro Tips for dbt Certifications](https://learn.getdbt.com/courses/pro-tips-for-dbt-certifications). Run a mock incident: rotate a token or break an environment and recover within 15 minutes. Book the exam in Talview and complete the system check | A booked exam slot |

**Active-recall tip**: load the study guide's links into NotebookLM (or similar) and have it quiz you. The questions will be easier than the real exam but they expose gaps fast. Alternative: read each docs page, then **rewrite it in your own words** — far more effective than rereading.

### Final-week checklist

- [ ] I can distinguish **defer** from **self-deferral** and know when to use each
- [ ] I can explain what **Advanced CI** compares and what it requires (Enterprise, `dbt compare`, primary key or uniqueness test)
- [ ] I know the three env var prefixes and the **four-tier precedence order** exactly
- [ ] I know the three webhook events, five retries, 7-day logs, 10-second timeout
- [ ] I know the four notification outcomes and what actually triggers Warns
- [ ] I know the permission set table and which sets are account- vs project-level
- [ ] I know that **licenses override group permissions**
- [ ] I can create and rotate a service token and verify jobs still run afterwards
- [ ] I can configure RBAC for a new team and map SSO groups to roles via SCIM
- [ ] I can publish a model for cross-project use and confirm lineage in Catalog (three conditions: `access: public`, production environment, at least one successful job run)
- [ ] I remember that **CI jobs do not update Catalog**
- [ ] I remember that **OAuth is development-only** and deployment uses service accounts
- [ ] I remember **PrivateLink = Business Critical**, IP restrictions = Enterprise+
- [ ] I can explain my branching strategy and branch protection rules
- [ ] I've done the 10 sample questions timed (under 2 minutes each)
- [ ] I've booked Talview, run the system check, and arranged a quiet room with backup power/internet

---

## 8. References

**Official dbt Labs**
- [dbt Certified Architect Path (full learning path)](https://learn.getdbt.com/learn/learning-path/dbt-certified-cloud-architect)
- [Exam page with the 10 sample questions](https://www.getdbt.com/certifications/dbt-architect-certification-exam)
- [Study Guide PDF (v6.3)](https://www.getdbt.com/dbt-assets/dbt-certificate-study-guide-for-cloud-architect)
- [Certification launch blog post](https://www.getdbt.com/blog/introducing-the-new-cloud-architect-certification)
- [Register via Talview](https://pages.talview.com/dbtlabs/certifications/) · Email: `certification@dbtlabs.com`
- [dbt Learn course catalog](https://learn.getdbt.com/catalog)

**Docs to read (per the study guide)**
- Connections: [About data platform connections](https://docs.getdbt.com/docs/cloud/connect-data-platform/about-connections) · [Access, Regions & IP addresses](https://docs.getdbt.com/docs/cloud/about-cloud/access-regions-ip-addresses) · [IP restrictions](https://docs.getdbt.com/docs/cloud/secure/ip-restrictions)
- Git: [Connect to GitHub](https://docs.getdbt.com/docs/cloud/git/connect-github) · [GitLab](https://docs.getdbt.com/docs/cloud/git/connect-gitlab) · [Azure DevOps](https://docs.getdbt.com/docs/cloud/git/connect-azure-devops) · [Git clone](https://docs.getdbt.com/docs/cloud/git/import-a-project-by-git-url)
- Environments: [Deployment environments](https://docs.getdbt.com/docs/deploy/deploy-environments) · [Environment variables](https://docs.getdbt.com/docs/build/environment-variables) · [Custom schemas](https://docs.getdbt.com/docs/build/custom-schemas) · [Defer](https://docs.getdbt.com/reference/node-selection/defer) · [Using threads](https://docs.getdbt.com/docs/running-a-dbt-project/using-threads)
- Jobs & CI: [Deploy jobs](https://docs.getdbt.com/docs/deploy/deploy-jobs) · [CI jobs](https://docs.getdbt.com/docs/deploy/ci-jobs) · [Advanced CI](https://docs.getdbt.com/docs/deploy/advanced-ci) · [Job scheduler](https://docs.getdbt.com/docs/deploy/job-scheduler) · [Merge jobs](https://docs.getdbt.com/docs/deploy/merge-jobs) · [Source freshness](https://docs.getdbt.com/docs/deploy/source-freshness) · [Hooks](https://docs.getdbt.com/docs/build/hooks-operations)
- Security: [Enterprise permissions](https://docs.getdbt.com/docs/cloud/manage-access/enterprise-permissions) · [About user access](https://docs.getdbt.com/docs/cloud/manage-access/about-user-access) · [Users and licenses](https://docs.getdbt.com/docs/cloud/manage-access/seats-and-users) · [Service account tokens](https://docs.getdbt.com/docs/dbt-cloud-apis/service-tokens) · [SSO overview](https://docs.getdbt.com/docs/cloud/manage-access/sso-overview) · [SCIM](https://docs.getdbt.com/docs/platform/manage-access/scim) ([Okta](https://docs.getdbt.com/docs/platform/manage-access/scim-okta) · [Entra ID](https://docs.getdbt.com/docs/platform/manage-access/scim-entra-id) · [managing licenses via SCIM](https://docs.getdbt.com/docs/platform/manage-access/scim-manage-user-licenses))
- Monitoring: [Job notifications](https://docs.getdbt.com/docs/deploy/job-notifications) · [Webhooks](https://docs.getdbt.com/docs/deploy/webhooks)
- Governance: [Intro to dbt Mesh](https://docs.getdbt.com/best-practices/how-we-mesh/mesh-1-intro) · [Project dependencies](https://docs.getdbt.com/docs/collaborate/govern/project-dependencies) · [Model access](https://docs.getdbt.com/docs/collaborate/govern/model-access) · [Model contracts](https://docs.getdbt.com/docs/collaborate/govern/model-contracts) · [Model versions](https://docs.getdbt.com/docs/collaborate/govern/model-versions) · [Discover data with Catalog](https://docs.getdbt.com/docs/collaborate/explore-projects) · [Quickstart with dbt Mesh](https://docs.getdbt.com/guides/mesh-qs)

**Community write-ups**
- [How to pass dbt Cloud Architect exam — Nikita Volynets](https://nikitavolynets.substack.com/p/how-to-pass-dbt-cloud-architect-exam)
- [dbt Architect Certification — Daniel Bostrom, The Data School](https://www.thedataschool.co.uk/daniel-bostrom/dbt-architect-certification)
- [dbt Architect Certification: The Complete 2025 Study Guide — FlashGenius](https://flashgenius.net/blog-article/dbt-architect-certification-the-complete-2025-study-guide)
- dbt Slack: `#dbt-certification`, `#learn-on-demand`, `#advice-dbt-for-power-users`, `#dbt-deployment-and-orchestration`

> *Content was rephrased for compliance with licensing restrictions.*
