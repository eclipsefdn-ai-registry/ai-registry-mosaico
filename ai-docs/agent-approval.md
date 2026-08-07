# MOSAICO — Agent Approval Config Guide

Instructions for AI agents generating A2A agent approval files for the `mosaico` tool.

## Tools

| Tool id | Distribution |
|:--------|:-------------|
| `mosaico` | MOSAICO agent runtime (Docker container) |

MOSAICO distributes its A2A agents as Docker containers. There is no live public deployment yet, so the `config` shape below is **provisional** — see "Status" below.

## Config Format

The `config` object in an `installConfig` entry for the `mosaico` tool is intended to describe how to pull and run the agent's Docker container.

```json
{
  "image": "TODO-registry.example.org/mosaico/<agent-name>",
  "tag": "TODO",
  "port": 0,
  "env": {
    "TODO_ENV_VAR": "<placeholder>"
  }
}
```

| Field | Type | Description |
|:------|:-----|:------------|
| `image` | string | Container image reference (registry/repository), e.g. `ghcr.io/eclipse-research-labs/mosaico/ip-solution-agent`. Use a `TODO`-prefixed placeholder until MOSAICO publishes a real registry location. |
| `tag` | string | Image tag/version to pull. Use `TODO` until a real published tag is known. |
| `port` | number | Port the agent listens on inside the container. Use `0` as a placeholder until confirmed. |
| `env` | object | Optional. Environment variables required to run the container (e.g. API keys, service endpoints). Use `<placeholder>` values for secrets, mirroring the Theia MCP convention. |

### Fields to omit

None known at this time — this list should be revisited once a real container reference exists and the actual runtime's requirements are known (there may turn out to be fields, such as a `name` or `autostart` preference, that a specific tool's install mechanism manages itself and that should not be duplicated here).

## Status: provisional

MOSAICO has not yet published a container registry location for the IP Solution Agent (or any other agent). The field names above (`image`, `tag`, `port`, `env`) are a reasonable, defensible guess at what a Docker-based install config needs, **not** a confirmed contract — no MOSAICO documentation or runtime currently defines this shape.

Whoever next updates an approval under the `mosaico` tool — once MOSAICO publishes real image coordinates and/or a documented install mechanism — should also revise this file to match reality (including removing this notice, filling in any fields that turn out to be wrong or missing, and adding an `installUrl` scheme if MOSAICO ever supports one-click install links).

## Guidelines

- Use `TODO`-prefixed placeholder values (e.g. `TODO`, `TODO-registry.example.org/...`) for any Docker coordinate that is not yet known, so it's unambiguous that the value is a stand-in rather than a real, working reference.
- Use `<placeholder>` syntax for secrets/tokens under `env`, mirroring the Theia MCP approval convention.
- Always include an `instructions` field on the `installConfig` explaining that the config is a placeholder and what the user should replace once real values are published.
