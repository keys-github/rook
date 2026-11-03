# Rook CLI plugin

The `rook` skill as a plugin, from Rook CLI by TestMu AI (Agent Assurance). It drives the `rook` CLI to test, evaluate and red-team an AI agent you own, and to read saved results: setup, target permissions, credit budgets, profiles, CI, and verdicts graded from evidence, with Pass, Fail and Unable to Verify reported separately.

The skill is a guide for your coding agent. It is not the `rook` executable and not an MCP server.

## Requirements

- The `rook` CLI: `npm install -g @testmuai/rook@latest` (Node.js 20 or newer), `brew install lambdatest/rook/rook`, or the [shell installer](https://github.com/LambdaTest/rook#install).
- A TestMu AI account with an Agent Assurance plan, or the 14-day free trial with 4,000 credits and the Pro features: [Start Free Trial](https://www.testmuai.com/register/?redirectTo=https://rook.lambdatest.com/projects&utm_source=rook-plugin&utm_medium=plugin&utm_campaign=rook-cli&utm_content=readme).

## Install

Claude Code:

```text
/plugin marketplace add LambdaTest/rook
/plugin install rook-cli@rook
```

The skill answers to `/rook-cli:rook`, and to `/rook` unless another command already uses that name.

Then open the repository that contains your agent and ask: _"Use rook to test my agent against its refund policy."_

## What leaves the machine

The plugin itself sends nothing: it is instructions for your coding agent. The `rook` commands it runs do:

- Model-backed commands (explore, generate, profile add and fix, run, ask, report with `--rca`) send the source excerpts and evidence they need to the TestMu AI controller, where the models run.
- `rook sync` records agents, scenarios and profiles to your hosted project, and a synced `rook run` uploads its evidence, artifacts and report there. `rook run --test` keeps the result local.
- Each session and job is registered with the TestMu AI service. Session registration sends a small terminal report: schema version, terminal name, whether output is a terminal, size, color level, and user or root on macOS and Linux.
- Telemetry records operational events, with no prompts, no code and no arguments. `ROOK_TELEMETRY=off` keeps telemetry and the terminal report on your machine. The one-time notice appears only in an interactive terminal, so set it in CI too.

See [Telemetry](https://github.com/LambdaTest/rook#telemetry) in the rook README.

## Safety

The agent you point `rook` at is yours, and its writes are real. Point it at staging, and approve the target's real actions and the credit spend before a run. See [A note on safety](https://github.com/LambdaTest/rook#a-note-on-safety).

## License

The files in this folder are licensed under Apache 2.0 (see LICENSE). The `rook` CLI is distributed separately.
