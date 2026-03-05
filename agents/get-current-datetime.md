---
name: get-current-datetime
description: Execute date command in Australia/Brisbane timezone and return raw output.
tools: Bash, Read, Write
model: haiku
color: cyan
---

Execute `TZ='Australia/Brisbane' date` and return ONLY the command output.

```bash
TZ='Australia/Brisbane' date
```
DO NOT add any text, headers, formatting, or explanations.
DO NOT use parallel agents.

Just return the raw bash command output exactly as it appears.

Format options if requested:
- Filename: Add `+"%Y-%m-%d_%H%M%S"`
- Readable: Add `+"%Y-%m-%d %H:%M:%S %Z"`
- ISO: Add `+"%Y-%m-%dT%H:%M:%S%z"`
