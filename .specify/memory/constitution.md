<!--
Sync Impact Report
- Version change: template -> 1.0.0
- Modified principles:
	- Template Principle 1 -> I. Code Quality Is a Product Requirement
	- Template Principle 2 -> II. Tests Are Mandatory Evidence
	- Template Principle 3 -> III. User Experience Consistency Is Non-Negotiable
	- Template Principle 4 -> IV. Performance Budgets Must Be Defined and Defended
	- Template Principle 5 -> V. Keep Systems Simple, Observable, and Reversible
- Added sections:
	- Engineering Standards
	- Delivery Workflow and Quality Gates
- Removed sections:
	- None
- Templates requiring updates:
	- .specify/templates/plan-template.md: ✅ updated
	- .specify/templates/spec-template.md: ✅ updated
	- .specify/templates/tasks-template.md: ✅ updated
	- .specify/templates/commands/*.md: ⚠ pending (directory not present)
- Runtime guidance docs:
	- README.md: ✅ no constitution reference drift found
- Deferred items:
	- None
-->

# Claude Code Source Snapshot Constitution

## Core Principles

### I. Code Quality Is a Product Requirement
All production code MUST be readable, intentionally structured, and easy to
maintain under the existing TypeScript and modular architecture. Changes MUST
preserve local style conventions (naming, file boundaries, import patterns,
feature-gating usage) unless refactoring is explicitly approved. Public behavior
changes MUST be documented in the associated feature spec and task list.

Rationale: this repository is large and subsystem-heavy; unmanaged code quality
creates compounding maintenance and security risks.

### II. Tests Are Mandatory Evidence
Every behavior change MUST include automated test evidence at the correct level:
unit tests for pure logic, integration tests for subsystem interactions, and
contract or end-to-end tests for user-visible command/tool behavior. A change is
not complete until tests fail before implementation and pass after implementation,
or a documented exception is approved.

Rationale: test evidence is the only scalable way to validate agentic workflows,
tool orchestration, and regression safety.

### III. User Experience Consistency Is Non-Negotiable
CLI, REPL, and structured output experiences MUST remain coherent across commands,
tools, and modes. New UX work MUST follow established interaction patterns for
error messages, progress states, permission prompts, and output formatting.
Any intentional deviation MUST be called out in the spec with migration notes.

Rationale: users rely on predictable behavior to safely operate automation flows.

### IV. Performance Budgets Must Be Defined and Defended
Every feature plan MUST define measurable performance expectations (latency,
startup impact, memory, or throughput as applicable). Changes that affect hot
paths (startup, query loop, tool execution, rendering) MUST include profiling or
benchmark evidence and MUST NOT regress agreed budgets without explicit approval.

Rationale: this system is interactive and orchestration-heavy; small regressions
can quickly degrade usability at scale.

### V. Keep Systems Simple, Observable, and Reversible
Designs MUST prefer the simplest solution that satisfies current requirements.
Complexity beyond MVP MUST be justified. Behavior MUST remain observable through
existing logs/metrics and safe to roll back when issues are detected.

Rationale: simplicity reduces defect density and makes incident response faster.

## Engineering Standards

- Language and runtime: TypeScript on Bun MUST remain the default unless a
	specific exception is approved.
- Architectural boundaries: changes MUST stay within established subsystem
	seams (commands, tools, services, bridge, UI) and avoid unnecessary coupling.
- Compatibility: user-facing commands, tool schemas, and structured output
	contracts MUST remain backward compatible unless explicitly versioned.
- Safety: permission boundaries and trust dialogs MUST NOT be bypassed by new
	features without approved security review.

## Delivery Workflow and Quality Gates

1. Spec gate: each spec MUST define acceptance scenarios, UX consistency impact,
	 and measurable performance criteria.
2. Plan gate: each plan MUST pass constitution checks for code quality strategy,
	 test strategy, UX consistency, and performance budgets.
3. Task gate: each task list MUST include explicit test tasks and validation
	 tasks for UX and performance where relevant.
4. Review gate: code review MUST verify constitution compliance before merge.
5. Verification gate: implementation MUST include evidence (test output,
	 benchmarks/profiling, screenshots/transcripts when UX is affected).

## Governance

This constitution takes precedence over local planning defaults and templates.
Amendments require:

1. A documented proposal describing the change and rationale.
2. Classification of version impact under semantic versioning:
	 - MAJOR: removes or redefines a principle in a backward-incompatible way.
	 - MINOR: adds a new principle or materially expands normative requirements.
	 - PATCH: clarifications, wording refinements, and non-semantic fixes.
3. Propagation of updates to impacted templates and workflow documents.
4. A compliance check in the next planning cycle confirming adoption.

Compliance reviews MUST occur for every feature plan and every merge request.
Any exceptions MUST be time-bound, explicitly approved, and tracked in the
feature documentation.

**Version**: 1.0.0 | **Ratified**: 2026-04-06 | **Last Amended**: 2026-04-06
