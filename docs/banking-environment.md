# Banking & Restricted Enterprise Compliance Guide

## 1. Why Banking Environments Restrict External Tools

Financial institutions and banks enforce strict information security policies:
- **No Unvetted Binaries**: Executables without code signing or security committee approval cannot run on workstations.
- **Strict Network Egress (Airgaps / Firewalls)**: Workstations cannot open arbitrary socket connections or talk to unauthorized external APIs.
- **Zero Third-Party Daemons**: Background daemons (like local MCP servers or unapproved telemetry listeners) trigger endpoint detection alarms (EDR).
- **Data Leakage Prevention (DLP)**: Source code, customer account numbers, and internal IP addresses must not leak outside authorized perimeter endpoints.

## 2. How Gentle AI Copilot Solves These Constraints

`gentle-ai-copilot` is designed from the ground up for strict zero-trust corporate environments:

1. **Zero Binaries / Zero Scripts Required**:
   Everything is expressed in standard Markdown, Git commits, and native `.github/` configuration files. There is no Go binary to compile, no npm daemon to run, and no Python virtual environment to maintain.
2. **Native to VS Code & GitHub Copilot**:
   GitHub Copilot is typically the officially vetted and contracted enterprise AI assistant in corporate IT. `gentle-ai-copilot` uses Copilot's built-in instruction and prompt engine (`.github/copilot-instructions.md` and `.github/prompts/`), requiring zero additional extensions.
3. **Data Stays in the Repository**:
   All architectural memory, task statuses, review ledgers, and test receipts live directly inside the repository (`odd/tasks/`, `odd/evidence/`). No data is sent to external second-brain databases or third-party servers.
4. **Enforced Financial Safety Invariants**:
   Built-in prompts and skills actively monitor against:
   - Floating-point arithmetic on currency values.
   - PII/PCI exposure in error messages or logs.
   - Missing authorization gates or missing idempotency keys on mutations.
