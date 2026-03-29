# Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions and scripts that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

## Available Skills

### js-malware-audit

Audit JS/TS project code for signs of infection, malware, backdoors, or supply-chain attacks. Designed for evaluating untrusted code, onboarding to new projects, or vetting open-source dependencies.

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
- Binary and media files (Medium)
- Docker and container risks (Medium)

**Output:**
Generates `_js_malware_audit_report.md` with findings, severity ratings, dependency audit summary, and an overall safety assessment.

## Installation

```bash
npx skills add kometolabs/agent-skills
```

## Usage

Skills are automatically available once installed. The agent will use them when relevant tasks are detected.

**Examples:**
```
Audit this project for malware
```
```
Check this codebase for backdoors before I run it
```
```
Vet the dependencies in this JS project
```

## Skill Structure

Each skill contains:
- `SKILL.md` - Instructions for the agent
- `scripts/` - Helper scripts for automation (optional)
- `references/` - Supporting documentation (optional)

## License

Apache-2.0
