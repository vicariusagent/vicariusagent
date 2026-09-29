# Vicarius (@vicariusagent)

Vicarius is a modular assistant and agent system built to help Lind'umusa Maseko manage projects, repositories, operational work, and personal coding tasks. Its purpose and working agreements should remain consistent even as the models, agent harnesses, and services used to carry out work change.

## How Vicarius works

Vicarius separates durable direction from task execution:

- **Vicarius Brain** is the knowledge and governance layer. Versioned Markdown records define identity, project context, agent roles, tasks, approvals, and operating rules.
- **Runners** such as Codex, Claude, Goose, OpenClaw, and local models carry out scoped tasks using those shared records. They are interchangeable task executors, not separate sources of truth.
- **Adapters and services** provide capabilities such as repository access, structured state, file storage, schedules, and notifications. Each capability should have a clear interface and a replaceable implementation.

This separation keeps Vicarius useful when a particular model or service is unavailable.

## Roles

Roles describe responsibilities, not products or fixed model personalities. One runner may perform several roles, and a role may be carried out by different runners.

| Role | Responsibility |
|---|---|
| **Coordinator** | Maintain awareness of projects and task queues, gather context, prioritize work, track progress, and surface blockers or decisions. |
| **Repository and prototype developer** | Monitor repositories, investigate changes and vulnerabilities, build designated prototypes, and make scoped code changes. |
| **Operations and release** | Prepare scheduled work, maintain operational records, and carry out approved setup or release steps. |
| **Memory and recordkeeping** | Capture messages and run evidence, maintain indexes and task state, and reconcile structured records with their Markdown source. |
| **Communications** | A future capability for preparing stakeholder outreach. Messages require approval before sending. |

## Working principles

- Keep work attached to a project and owning context, such as Vicarius, personal work, Ndali, or Webpark. Tags organize context; they do not grant access.
- Use a Markdown task as the durable work brief. Record its subtasks, evidence, decisions, approvals, and outcome in the task.
- Preserve source links and distinguish verified facts, owner-provided context, proposals, and unknowns.
- Use deterministic code for collection, schedules, deduplication, fixed-rule classification, reconciliation, approval checks, and report rendering where practical. AI can help interpret or draft, with evidence attached.
- Use a dedicated feature branch for repository changes. Report what changed and how it was checked.
- Get explicit approval before deploying, spending money, deleting data, or sending messages. A model or automation cannot approve its own proposed action.
- Keep credentials and secret values out of repositories, logs, task files, and generated reports.

## Tools and service direction

The system is designed to work across tools while keeping their status clear.

| Tool or service | Intended role | Status |
|---|---|---|
| **Git and Markdown** | Durable instructions, project records, tasks, decisions, and reviewable changes | In use for the Vicarius Brain documentation |
| **Codex** | Interactive coding and task runner | Starter harness |
| **Claude** | Independent analysis, coding, and review | Used through native apps; Brain integration is not verified |
| **Goose** | Desktop or CLI task execution, including local work | Desktop used and CLI installed; Brain integration is not verified |
| **OpenClaw** | Self-hosted assistant gateway and mobile access for persistent intake and routing | Prioritized future deployment; not provisioned |
| **Ollama with Gemma** | Local model option for eligible work on Fedora hardware | Planned; host and model version are not selected |
| **Firebase Realtime Database** | Shared mutable task coordination, run records, approvals, cursors, and indexes | Firebase is part of the target design; the dedicated Brain database and rules are not deployed |
| **Google Drive and Apps Script** | File storage and independent scheduled Google Workspace automation | Planned; inventory scripts and schedules are not configured |
| **n8n** | Optional orchestration for multi-service workflows | Optional; no active workflow is verified |
| **Obsidian** | Optional interface for canonical Markdown | Optional; no vault integration is verified |
| **Google AI Studio / Gemini API** | Occasional small, low-sensitivity model steps within free quota | Proposed; not configured. No paid fallback. |
| **OpenRouter** | Compare candidate models for future evaluation | Optional evaluation path, not the production default |
| **Buzz** | — | Retired; do not build new integrations against it |

These statuses describe the current plan, not a claim that every connection or scheduled job is live. Verify setup before relying on an integration.

## Task and approval flow

1. Create or update a Markdown task with its project, goal, scope, sources, and expected result.
2. The coordinator identifies dependencies and assigns a suitable role and runner.
3. The runner works within the task's permissions, using a dedicated branch for repository changes.
4. Record evidence, changed files, checks performed, and any unresolved risks in the task and run record.
5. Stop at an approval boundary. Deployment, spending, deletion, and outbound messages wait for the owner's explicit approval.
6. Reconcile task status and structured indexes with the durable Markdown record.

Scheduled work is intended to run independently of an interactive assistant session. When a model limit, service outage, or missing permission blocks work, record and queue the task rather than silently changing providers, incurring cost, or dropping the result.

## Repository work

Vicarius can monitor registered repositories for changes, open issues and pull requests, and actionable security updates. It can prepare a report, build designated prototypes, and make task-scoped changes when authorized. Reports should name the repositories checked, the time and source of the check, findings, and any access gaps.

Newly shared repositories should be added to the project registry after they are visible to the authorized GitHub account. Company projects begin with repositories and project documents, with their owning entity recorded so context remains organized.

## Project prototype convention

For a project explicitly designated as a **web app prototype**, the default is a static Firebase web application:

- Serve app files from a `public/` folder and use Firebase Hosting.
- Use Firebase Realtime Database when the project needs a database.
- Put application code in browser `<script type="module">` code and use browser-compatible CDN dependencies.
- Use the Firebase CLI initialization and deployment workflow.
- Keep Firebase project resources separated per project and record the selected database/storage arrangement.
- Do not add paid services such as Cloud Functions unless the owner explicitly approves a change to that project's plan.

This convention applies to designated prototypes; each project's actual Firebase configuration and deployment status must be verified separately.

## Records and data boundaries

The intended division is:

- **Git and Markdown:** canonical instructions, authored context, project/task records, decisions, and source-controlled workflow definitions.
- **Firebase RTDB:** mutable structured runtime data such as message/task indexes, leases, approvals, cursors, and run records.
- **Google Drive:** files, exports, and interim logs.

Structured records should link to their source task, repository revision, run, or Drive file. Do not treat a cache or index as the canonical meaning, and do not store credentials in any of these data stores. The Brain RTDB schema and security rules remain planned until deployed and verified.

## Learn more

The Vicarius Brain repository contains the detailed role map, project registry, setup status, service and flow map, task process, approval policy, prototype convention, and architecture decisions. Use it as the canonical source when this profile summary and current Brain records differ.
