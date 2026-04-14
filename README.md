# gito-poc

Replica of Nayjest/Gito's CI workflow.

Demonstrates fork checkout + pytest secret exposure:
- `pull_request_target` triggers on any fork PR
- No workflow-level gate (relies on repo-level approval setting)
- Checks out fork code (`ref: github.event.pull_request.head.sha`)
- Runs `pytest` with `LLM_API_KEY` in env
- Attacker adds a test file that exfiltrates the secret
- `permissions: contents: write` makes GITHUB_TOKEN extra dangerous

Used for authorized security research only.
