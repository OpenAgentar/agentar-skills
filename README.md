# Agentar Skill

Agentar Skill helps OpenClaw-compatible agents install, validate, and use the Agentar CLI. Use it when you want an agent to run Agentar commands, start Playground chat sessions, manage sessions, or work with supported attachment and scenario-agent workflows.

## Install

Install from the GitHub skill repository with `skills`:

```bash
npx skills add OpenAgentar/agentar-skills
```

Install from ClawHub with OpenClaw:

```bash
openclaw skills install @openagentar/agentar
```

You can also inspect or install the ClawHub listing directly:

```bash
npx clawhub inspect @openagentar/agentar
npx clawhub install @openagentar/agentar
```

## What This Skill Does

- Installs Agentar CLI through the configured Agentar distribution workflow.
- Verifies that the `agentar` binary is available and runnable.
- Guides agents through Agentar authentication and Playground chat commands.
- Documents session continuation, output modes, file attachments, and built-in scenario agents.
- Encourages isolated temporary state for repeatable validation and safer credential handling.

## Example Request

After installing this skill, ask your agent:

```text
Install Agentar CLI into an isolated prefix and verify that it works.
```

The skill guides the agent toward a flow like:

```text
Check the local Node.js/npm runtime, install Agentar CLI through the configured distribution workflow, then verify the agentar binary with --version and --help.
```

For chat workflows, provide your own credentials through environment variables or the Agentar auth command:

```bash
AGENTAR_API_KEY=<YOUR_API_KEY> agentar "hello"
agentar auth login --api-key <YOUR_API_KEY>
agentar "hello" --output json
```

## Repository Layout

```text
skills/
  agentar/
    SKILL.md
    references/
      agentar-cli-quick-reference.md
skills.sh.json
.clawhubignore
LICENSE
```

## Maintainer Notes

Validate the skill package before publishing:

```bash
python3 ~/.config/opencode/skills/skill-creator/scripts/package_skill.py \
  ./skills/agentar \
  ./dist
```

Publish to ClawHub under the OpenAgentar owner:

```bash
npx clawhub skill publish ./skills/agentar \
  --slug agentar \
  --name "Agentar" \
  --owner openagentar \
  --source-repo OpenAgentar/agentar-skills \
  --source-commit <commit-sha> \
  --source-ref master \
  --source-path skills/agentar \
  --topics agentar,agentar-cli,cli,playground,automation
```

Trigger skills.sh discovery from the GitHub repository:

```bash
npx skills add OpenAgentar/agentar-skills
```

## Safety Notes

- Do not commit secrets, API keys, `.env` files, credentials, or private configuration.
- Use placeholders such as `<YOUR_API_KEY>` in examples and documentation.
- Review generated archives before publishing to any public marketplace.
- Keep skill files text-based for ClawHub compatibility.

## License

This repository is licensed under the MIT License. See [LICENSE](LICENSE) for details.
