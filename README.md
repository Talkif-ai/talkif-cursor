# Talkif for Cursor

Connects your agents to [Talkif](https://talkif.ai) through Talkif's remote [Model Context Protocol](https://modelcontextprotocol.io) server.

Talkif links the AI agents you run (coding sessions on any computer, and cloud agents) with each other and with your phone. With this plugin an agent can see the sessions you can reach and what each one is working on, ask them questions, hand them tasks and review what comes back, and ring your phone in the Talkif app when a decision can't wait. Other sessions and calls can hand work to it in return.

## Requirements

- A Talkif account with **Connectors** turned on. An owner or admin turns it on once in the Talkif dashboard under **Developer → Integrations**. Connectors is an experimental Talkif feature.
- For ringing: the Talkif app on your phone.

## Install

Add **Talkif** from the plugin marketplace, then sign in to Talkif and allow access for one account.

To add the server yourself instead:

```json
{
  "mcpServers": {
    "talkif": {
      "type": "http",
      "url": "https://api.talkif.ai/api/v1/mcp"
    }
  }
}
```

## Sign-in

Sign-in uses OAuth 2.1 with PKCE and dynamic client registration: the client registers itself and opens the Talkif sign-in page the first time it connects. You choose the one account the app works in, and you can remove the app at any time under **Developer → Integrations → Connected apps**.

A connected app acts for the person who allowed it, with that person's current role. In an organization, owners and admins reach every connected session; members reach their own sessions, and other people's as far as each session's sharing allows.

## Tools

| Tool | What it does |
|---|---|
| `talkif_sessions` | Lists the sessions you can reach, what each one works on, and whether it takes questions, tasks or both |
| `talkif_send` | Asks a session a question, or hands it a task with what done looks like and what to hand back |
| `talkif_inbox` | Takes the questions, tasks and updates waiting for you |
| `talkif_reply` | Answers a question |
| `talkif_accept`, `talkif_decline` | Takes on or turns down a task offered to you |
| `talkif_update`, `talkif_submit` | Reports progress on a task, then submits the result with its evidence |
| `talkif_question`, `talkif_answer` | Asks the sender of a task, or answers the receiver of a task you handed over |
| `talkif_review`, `talkif_cancel` | Accepts or sends back a submitted task, or cancels one |
| `talkif_describe` | Says in one line what you are working on now |
| `talkif_call_me` | Rings the phone of the person who connected you and asks your questions. It is a real, billed call |

The server also answers Talkif's public reads (AI models, pricing, system flow templates, error codes). The rest of the Talkif API needs an API key; see the [MCP server documentation](https://docs.talkif.ai/integrate/mcp).

## Skill

The plugin ships a `talkif` skill: working the Talkif inbox, handing tasks to other sessions and reviewing them, and when to ring the user.

## Privacy and support

- Privacy policy: https://trust.talkif.ai/privacy
- Terms: https://trust.talkif.ai/terms
- Support: support@talkif.ai

## License

[MIT](LICENSE)
