# AI Agents

The common AI-agent vocabulary -- the agents a platform hosts, the threads of conversation with them, the runs that execute them and the tools they can call -- distilled from the APIs that already exist. Model inference belongs to the models standard in API Commons. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged AI Agents, Agents, Agentic AI, Agent Platform, Autonomous Agents, Agentic, Conversational AI in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| ai_agent | 156 | 121 | name 80%, id 79%, created_at 51% | agents 119, agent 40, bots 8, assistants 7 |
| agent_thread | 52 | 43 | id 72%, created_at 58% | conversations 34, threads 12, chats 7, conversation 4 |
| agent_run | 41 | 39 | status 80%, id 69%, created_at 56% | runs 34, tasks 6, executions 5, run 2 |
| agent_tool | 37 | 27 | name 82%, id 74%, description 67%, created_at 63%, parameters 56% | tools 30, tool 9, integrations 1, skills 1 |

Cohort: 680 providers with harvested OpenAPI, 156 crosswalks. Of the providers exposing a ai_agent: 57% create, 88% list, 62% fetch, 42% update, 42% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- An agent agrees on its name, id and created_at -- and not on what makes it an agent: its instructions sit at 29%, and the model and the tools it may call are each carried by a minority under different names. 156 platforms expose an agent; they describe its brain 156 ways.
- A tool agrees on name, description and a parameters schema -- the function-calling shape the model providers defined, which agent platforms adopted wholesale.
- A run agrees on status, id and created_at; a thread only on id and created_at.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- Agents are `/ai-agents`, threads `/agent-threads`, runs `/agent-runs` and tools `/agent-tools`: help desk owns agents, messaging owns conversations, and CI/CD and workflow automation own runs.
- Assistants, bots and copilots are agents.
- Singular `/chat` is a chat-completion call and belongs to the models standard, not here.
- Executions count as runs only beneath an agent, task or workflow path.
- Duplicates merged: Duvo, Parallel, Sail, Ottic into Rime, and the eventwren family.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
