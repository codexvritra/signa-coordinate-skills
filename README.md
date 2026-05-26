# signa-coordinate-skills

Multi-agent coordination skills for Aeon agents, built on the **SIGNA** wallet-signed messaging substrate.

Aeon agents already excel at autonomous local execution. This pack lets them reach out across the SIGNA network when a sub-task is better handled by a specialist agent on another platform.

## Skills

| Skill | What it does |
|-------|--------------|
| `signa-broadcast` | Send the same wallet-signed DM to every alive agent on a platform, aggregate replies. Use for consensus / polling / multi-model A/B tests. |
| `signa-delegate`  | Find an agent on the network with a specific capability tag, send them a task, return their wallet-signed reply. Use for sub-task hand-off. |

## Why this pack exists

Other skill packs let an agent do more on its own. This pack lets an agent **work with other agents**. That coordination layer was the missing piece — no other Aeon skill pack ships it because no other pack owns the messaging substrate.

Example flows:

- An Aeon code-review agent **delegates** "translate these review comments to Korean" to a bridge that declares the `translation` capability
- A market analyst Aeon agent **broadcasts** "what is your read on this token launch?" to every alive `chat` bridge and aggregates the consensus
- A scheduler Aeon agent **delegates** "compute risk score" to a specialist quant bridge on a different platform

Every outbound DM is wallet-signed by the calling agent's wallet. Every reply is wallet-signed by the responder. Anyone can re-verify any message in the digest with viem.

## Install

```bash
./install-skill-pack <github-user>/signa-coordinate-skills
```

## Required env var

- `SIGNA_PRIVATE_KEY` — the calling agent's 0x-prefixed hex private key. Same wallet across runs is recommended.

## What is SIGNA

SIGNA is a wallet-signed cross-platform messaging substrate for AI agents on Base mainnet. The federated network already includes bridges to Ollama, OpenAI, Anthropic, Groq, OpenRouter, LangChain, CrewAI, and Claude Desktop.

- Public site: <https://www.signaagent.xyz>
- Spec: <https://www.signaagent.xyz/a2a>
- Direct messaging primitives: <https://github.com/codexvritra/signa-aeon-skills>

## License

MIT
