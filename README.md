# Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions and scripts that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

## Available Skills

### js-malware-audit

```bash
npx skills add kometolabs/agent-skills --skill js-malware-audit
```

Audit JS/TS project code for signs of infection, malware, backdoors, or supply-chain attacks. Designed for evaluating untrusted code, onboarding to new projects, or vetting open-source dependencies.

> **Disclaimer:** This skill does **not** guarantee 100% safety. It provides a best-effort analysis based on observable source code patterns. Sophisticated or novel obfuscation techniques may evade detection. Use it as one layer in a broader security review, not a replacement for professional audits, sandboxed execution, or runtime monitoring.

**Prerequisites:**
- **[Depguard MCP](https://github.com/mopanc/depguard)** - dependency security auditing. Without it, the skill will rely on package manager audits only.
- **[Trivy CLI](https://github.com/aquasecurity/trivy)** - Docker image vulnerability scanning. Without it, the skill will skip container image scans if Dockerfiles are present.

**Use when:**
- Taking over a JS/TS project from a non-trusted source
- Evaluating open-source code before running it
- Onboarding to a new codebase
- Vetting dependencies for supply-chain risks

**Categories covered:**
- Package/build script attacks (Critical)
- Code execution and obfuscation (Critical)
- Network exfiltration (High)
- Filesystem and environment access (High)
- Environment variable injection (High)
- Symlinks and git submodules (Medium)
- Git hooks and IDE config (Medium)
- Dependency supply chain (Critical)
- CI/CD pipeline poisoning (High)
- LLM audit evasion (High)
- Binary and media files (Medium)
- Docker and container risks (Medium)

**Output:**
Generates `_js_malware_audit_report.md` with findings, severity ratings, dependency audit summary, and an overall safety assessment.

> **Caveat:** No system prompt is 100% injection-proof. A sophisticated attacker could still potentially influence an LLM-based audit. The mitigations in this skill make it significantly harder and turn injection attempts themselves into auditable findings - but this should not be treated as a guarantee. Use it as one layer in a broader security review, not a replacement for human analysis.

**Usage examples:**
```
Audit this project for malware
```
```
Check this codebase for backdoors before I run it
```
```
Vet the dependencies in this JS project
```

### ai-slop-detection

```bash
npx skills add kometolabs/agent-skills --skill ai-slop-detection
```

Check the project for AI slop across language, code, UI, and configuration. Useful for spotting vibe-coded projects or AI-generated PRs that were merged without review.

**Use when:**
- Evaluating a project you didn't write
- Reviewing code from AI coding tools (Lovable, Bolt.new, v0, etc.)
- Auditing a codebase for low-effort AI output

**Categories covered:**
- Language slop (buzzwords, filler phrases, em dashes, emojis)
- Code slop (obvious comments, generic names, unused imports, phantom dependencies, vibe-coding platform artifacts)
- Test slop (vacuous assertions, mock-heavy suites, empty test files)
- UI/style slop (purple gradients, blob backgrounds, generic section names)

**Output:**
Findings grouped by category with file:line references and a conclusion: likely AI-generated / mixed / likely human.

**Usage examples:**
```
Check this project for AI slop
```
```
Is this codebase vibe-coded?
```
```
Audit this PR for low-effort AI output
```

## Skill Structure

Each skill contains:
- `SKILL.md` - Instructions for the agent
- `scripts/` - Helper scripts for automation (optional)
- `references/` - Supporting documentation (optional)

## License

Apache-2.0
