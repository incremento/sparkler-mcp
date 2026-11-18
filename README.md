<img src="assets/logo.png" alt="" width="64" height="64">

# Sparkler for your agent

[Sparkler](https://withsparkler.com) makes presentation decks that the audience joins from their phones. You make the deck by asking the agent you already use: Claude, ChatGPT, Cursor, Claude Code, Codex or any other app that speaks MCP. Sparkler has no AI of its own. Your agent writes the slides; Sparkler checks them, renders them in one of its themes, hosts the talk on one link, runs the live room and sends the follow-up email afterwards.

This repository holds Sparkler's listing and plugin files. Sparkler itself is a hosted service at `https://withsparkler.com/mcp`, so there is nothing here to install or run.

## Connect

The address is the same everywhere:

```
https://withsparkler.com/mcp
```

It is a remote MCP server (Streamable HTTP) with OAuth sign-in. The first time, your agent opens a Sparkler page in the browser; you sign in with your email address and choose Allow. A new email address gets a free account.

**Claude:** find Sparkler in Claude's connector directory and choose Connect, or add a custom connector with the address above (Settings, Connectors, Add custom connector).

**ChatGPT:** find Sparkler in ChatGPT's apps and choose Connect.

**Cursor:** install Sparkler from the Cursor Marketplace, or add this to `.cursor/mcp.json`:

```json
{
  "mcpServers": {
    "sparkler": { "url": "https://withsparkler.com/mcp" }
  }
}
```

**VS Code:**

```sh
code --add-mcp '{"name":"sparkler","type":"http","url":"https://withsparkler.com/mcp"}'
```

**Claude Code:**

```sh
claude mcp add --transport http sparkler https://withsparkler.com/mcp
```

Then type `/mcp`, choose sparkler, and sign in.

**Codex:**

```sh
codex mcp add sparkler --url https://withsparkler.com/mcp
codex mcp login sparkler
```

**Anything else:** any MCP client that supports remote servers with OAuth works with the address above. For a client without browser sign-in, make a personal key on the [Connect page](https://withsparkler.com/app/connect) and send it as `Authorization: Bearer <key>`.

## What to ask for

- "Use Sparkler to make a 20-minute talk on onboarding new managers, for about 40 team leads. Open with a question for the room to guess, add a vote and a question time, and send me the preview link."
- "Bring my PowerPoint into Sparkler and add three questions for the audience."
- "Make this deck in our brand colours from example.com, then publish it and give me the present link."
- "How did yesterday's talk go? Show me the votes and the questions people asked."

## The tools

"Changes things" means the tool saves, replaces or removes something in your Sparkler account; your agent app may ask you before it runs one of them.

| Tool | What it does | Changes things |
|---|---|---|
| `get_guide` | The guide to slide types, themes and audience features | No |
| `whoami` | Which Sparkler account is connected, and its plan | No |
| `create_deck` | Makes a new deck and returns a private preview link | Adds a deck |
| `get_deck` | Lists your decks, or reads one | No |
| `edit_deck` | Changes a deck: adds, replaces, moves or deletes slides, sets the theme | Yes, can remove slides |
| `add_image` | Stores an image for slides, sent by your agent or fetched from a public link | Adds an image |
| `preview` | Pictures of slides, so your agent can check how they look | No |
| `preview_sheet` | The whole deck on one contact sheet | No |
| `upload_theme` | Saves your own theme, or makes one from a brand's website | Yes, can replace or remove a theme |
| `start_import` | Starts bringing in a PowerPoint file or a Google Slides link | Adds an import |
| `get_import` | Reads an import's slides, text and pictures, for your agent to rebuild | No |
| `publish` | Publishes a deck and returns its share link, present link and join code; can also take it down | Yes, makes a deck public or private |
| `get_results` | The room's answers, questions and follow-up figures after a talk | No |

A deck stays private until your agent publishes it. Audience answers are anonymous to the speaker.

## In this repository

- `server.json`: the entry in the [official MCP Registry](https://registry.modelcontextprotocol.io) (`com.withsparkler/sparkler`)
- `.cursor-plugin/plugin.json` and `mcp.json`: the Cursor plugin
- `assets/logo.png`: the icon

## Links

- Documentation: https://withsparkler.com/docs
- Privacy: https://withsparkler.com/privacy
- Terms: https://withsparkler.com/terms
- Help: hello@withsparkler.com (a person reads every email)

The files in this repository are under the MIT licence. Sparkler is made by Incremento Ltd.
