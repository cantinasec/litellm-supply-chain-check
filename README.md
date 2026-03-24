# litellm-supply-chain-check

A Claude Code skill that checks whether your project or system was affected by the LiteLLM PyPI supply-chain compromise (malicious versions 1.82.7 and 1.82.8, published 2026-03-24).

Built by [Cantina](https://cantina.security/).

## What it does

Runs a six-part diagnostic across your environment:

1. **Version detection** — checks system Python, virtualenvs, pipx, conda, and uv
2. **Malicious `.pth` file search** — looks for `litellm_init.pth` in site-packages
3. **Manifest scanning** — searches dependency files, CI configs, Dockerfiles, and source code
4. **IOC domain check** — searches logs and history for the exfiltration endpoint `models.litellm.cloud`
5. **Pip cache inspection** — checks for cached compromised wheels
6. **Shell history review** — finds past install commands

Outputs a structured report with an exposure level (HIGH / MEDIUM / LOW / NONE) and remediation steps.

## Usage

Add `SKILL.md` to your Claude Code skills directory and invoke it with:

```
/litellm-supply-chain-check
```
