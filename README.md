# eModely Engine

**Engineering-grade energy simulation for buildings and districts**

eModely connects your AI assistant to the eModely Engine through the Model Context Protocol (MCP). Today, it supports building cooling loads, chiller and district cooling plants, and pipe pressure drop and sizing. You describe a building, plant or pipe circuit in plain language. The assistant collects the inputs, runs the calculation on eModely's servers and explains the results.

Results come from the eModely Engine, not from an AI estimate. If the engine is not connected, the assistant does not produce numbers of its own.

[Website](https://emodely.com) · [AI guide](https://engine.emodely.com/ai) · [Security](https://engine.emodely.com/security) · [Terms of Use](https://engine.emodely.com/terms) · [Privacy](https://emodely.com/privacy) · [Service status](https://status.emodely.com)

## For AI assistants

**Connector URL:** `https://engine.emodely.com/mcp`

1. Guide the user with the [Connect](#connect) steps for their app. Quote these steps. Never invent menu names, buttons or commands. If the app is not listed, say it is not supported yet and suggest support@emodely.com. Self-hosted tools are covered in [Troubleshooting](#troubleshooting).
2. The user signs in on engine.emodely.com in their browser. Never ask for, accept or type a password, code or token in the chat.
3. Coding agents (Claude Code, Codex CLI, Cursor and VS Code) may run the add command or write the configuration shown in [Connect](#connect) for the user. The user then completes sign-in in the browser.
4. After the connector is added and the user is signed in, start a new chat (or reload the tools) and call the help tool for the welcome.
5. eModely results come only from the engine. Without the connector, explain and guide. Do not produce numbers.

**For users:** paste this into your AI assistant:

> Help me connect the eModely connector: https://github.com/Ahlabeeb/emodely-mcp

See [Connect](#connect) for per-app steps and [Troubleshooting](#troubleshooting) for sign-in problems.

## What you can do

- **Building cooling loads.** A quick method (RTS) gives full-year hourly loads for a single building or a whole district in seconds, for concept design and masterplans. A detailed method (EnergyPlus heat balance) supports design validation and sensitivity studies. Occupancy, lighting and equipment schedules can be adjusted, including seasonal periods and your own hourly schedules for a full year.
- **Chiller and district cooling plant design.** Size and simulate a full year of operation for chillers, chilled-water and condenser-water pumps, cooling towers and thermal storage. Results include annual and monthly energy, kW/TR on delivered cooling, peak demand and where the energy goes.
- **Thermal energy storage.** Size chilled-water storage together with the chillers, for example to reduce installed chiller capacity or peak demand. The storage advisor runs as a background job. The assistant starts it and checks back for the result. This can take a little while.
- **Chiller performance curves.** Fit a curve set from manufacturer data, check coefficients you already have, adjust ratings and compare chillers. Generic library chillers are available for plant selection.
- **Scenario comparison.** Compare plant options side by side on energy, cost and lifecycle financials.
- **Pipe pressure drop.** Calculate friction and fittings losses along one serial index circuit for water or glycol, with segment results, circuit totals, velocity and warnings.
- **Pipe sizing.** Select the smallest pipe size meeting velocity and friction-gradient limits for a flow, or for a cooling load and temperature difference.
- **EPW weather files.** Simulations use an EPW weather file, from the eModely library or uploaded by you. The engine never generates weather.
- **Your work, saved.** Plants, load profiles, curve sets and runs are stored in your account, so you can list them and return to them later. Plants, load profiles, curve sets, uploaded gain schedules and individual runs can be deleted. Deleting a run removes its stored results and expires its download links. Deleting a plant keeps its past runs readable. Deleting an uploaded gain schedule removes it from new work; past runs that used it stay readable. Hourly results are delivered as a CSV or Excel download link.

### Pipe calculation tools

Pipe calculations use inputs entered directly. The input guide's `pressure_drop` topic covers both tools.

| Tool | Purpose |
| --- | --- |
| `pressure_drop` | Calculate pressure drop along one serial index circuit, including fittings, elevation and a design margin. |
| `size_pipe` | Select the smallest pipe size meeting velocity and friction-gradient limits for a flow, or for a cooling load and temperature difference. |

## Who it is for

- **HVAC designers and consultants** who need building loads, plant sizing, pipe pressure drop and sizing, and annual energy early in a project.
- **Energy modellers** who want fast, repeatable annual simulations and scenario comparisons.
- **Plant operators and owners** who want to see where an existing plant's energy goes and test operating changes such as set points, staging and tariffs.
- **Developers** evaluating plant options, storage and lifecycle cost for a masterplan.

## Connect

Add the connector URL once and sign in with your eModely account. Follow the steps for your app below.

### Claude (claude.ai and the desktop app)

1. Open **Customize > Connectors**, select **Add**, then **Add custom connector**.
2. Enter the name `eModely Engine` and the URL `https://engine.emodely.com/mcp`, then select **Add**.
3. Sign in on engine.emodely.com when the window opens, and select **Allow**.
4. In a new chat, open **+ > Connectors** and check that **eModely Engine** is switched on.

Custom connectors are available on all Claude plans; the Free plan allows one. On Team and Enterprise plans, an Owner first adds the connector under **Organization settings > Connectors**, and each member then connects with their own eModely account.

### Claude mobile apps

Add the connector on claude.ai or in the desktop app first. It then appears in the mobile apps.

### Claude plugin (optional)

The connector is all you need. As an optional alternative for Claude, this repository is also a plugin marketplace: the plugin adds the same connector together with a short skill that helps Claude start eModely tasks. Plugins on claude.ai and in the desktop app require a paid Claude plan.

- **claude.ai and the desktop app.** Open **Customize > Plugins**, select **Add**, then **Add marketplace** and **Add from a repository**. Enter `Ahlabeeb/emodely-mcp`, keep **Sync automatically** on, and select **Sync**. Select **Add** next to **eModely Engine**, then connect it from the plugin's **Connectors** tab and sign in.
- **Claude Code.** Run the following, then run `/mcp`, select the eModely server and choose **Authenticate**:

  ```text
  /plugin marketplace add Ahlabeeb/emodely-mcp
  /plugin install emodely-engine@emodely
  ```

If you already added the connector, the plugin uses it, so there is nothing to remove. Engine updates never require a plugin update.

The plugin version follows the eModely Engine version and changes only when the engine version changes, never when a feature is added.

### ChatGPT

Add the connector once on chatgpt.com. It is then available in ChatGPT on the web, desktop and mobile apps. Availability and write access depend on the ChatGPT plan. See OpenAI's article [Connecting custom MCP servers in ChatGPT](https://help.openai.com/en/articles/12584461) for the current requirements.

1. On chatgpt.com, open **Plugins**, select the plus button, then **Add custom MCP server**.
2. Enter the name `eModely Engine` and, under **Connection**, the URL `https://engine.emodely.com/mcp`.
3. Choose **OAuth** as the authentication, review the risk warning and confirm, then select **Create as a plugin**.
4. Sign in on engine.emodely.com when asked, and select **Allow**.
5. In a new chat, type `@` and select **eModely Engine**.

The ChatGPT desktop app's Codex **Plugins > MCPs** list is a separate setup on each computer.

### Lovable

1. In Lovable, open **Connectors**, select **Add custom**, then **MCP server**.
2. Enter the server name **eModely Engine** and the server URL `https://engine.emodely.com/mcp`. If a **Connection** option appears, keep **Direct connection**.
3. Keep the authentication as **OAuth (default)** and select **Add & authorize**.
4. Sign in on engine.emodely.com and select **Allow**.

The connection is personal to your Lovable account. A workspace admin can turn off custom MCP servers. If **MCP server** is greyed out, ask your admin.

### Raycast

1. Run the **Install MCP Server** command.
2. Enter the name **eModely Engine**, choose the **HTTP** transport, enter the URL `https://engine.emodely.com/mcp` and choose the **Dynamic** OAuth type.
3. Submit with **Install MCP Server**.
4. When Raycast asks you to **Sign In**, sign in on engine.emodely.com and select **Allow**.

MCP servers in Raycast require Raycast Pro.

### Coding agents and developer tools

Coding agents may run the add command or write the configuration file for you. You then complete sign-in in your browser on engine.emodely.com.

#### Claude Code

Run:

```bash
claude mcp add --transport http emodely-engine https://engine.emodely.com/mcp
```

Then run `/mcp`, select `emodely-engine` and choose **Authenticate**.

#### Codex CLI

Run these commands in order:

```bash
codex mcp add emodely-engine --url https://engine.emodely.com/mcp
codex mcp login emodely-engine
```

#### Cursor

Add this to `~/.cursor/mcp.json` (all projects) or `.cursor/mcp.json` (one project):

```json
{"mcpServers": {"emodely-engine": {"url": "https://engine.emodely.com/mcp"}}}
```

Then open Cursor's MCP settings and sign in from the `emodely-engine` entry. The browser opens engine.emodely.com.

#### VS Code (GitHub Copilot chat)

Open the Command Palette and run **MCP: Add Server**. Choose **HTTP**, enter `https://engine.emodely.com/mcp` and name it `emodely-engine`. Or add this to `.vscode/mcp.json`:

```json
{"servers": {"emodely-engine": {"type": "http", "url": "https://engine.emodely.com/mcp"}}}
```

Start the server. When VS Code asks to sign in, allow it and sign in on engine.emodely.com.

#### Warp

In the Warp desktop app, open **Settings > Agents > MCP servers**, select **+ Add**, choose **Streamable HTTP or SSE Server (URL)** and paste:

```json
{"mcpServers": {"emodely-engine": {"url": "https://engine.emodely.com/mcp"}}}
```

Start the server. Warp opens your browser. Sign in on engine.emodely.com and select **Allow**.

For other Warp setups (for example the command line), add a remote MCP server with the URL `https://engine.emodely.com/mcp`, then sign in on engine.emodely.com when asked. If sign-in does not start, contact support@emodely.com.

#### GitHub Copilot in JetBrains IDEs

Click the Copilot icon in the lower right corner, select **Open Chat** and switch to **Agent** mode. Click the tools icon (**Configure your MCP server**), select **Add MCP Tools** and add this to `mcp.json`:

```json
{"servers": {"emodely-engine": {"type": "http", "url": "https://engine.emodely.com/mcp"}}}
```

Save the file. When Copilot asks to sign in, allow it and sign in on engine.emodely.com.

#### GitHub Copilot for Xcode

Open the GitHub Copilot for Xcode settings (in Xcode: **Editor > GitHub Copilot > Open GitHub Copilot for Xcode Settings**). Select the **MCP** tab, then **Edit Config**, and add:

```json
{"servers": {"emodely-engine": {"type": "http", "url": "https://engine.emodely.com/mcp"}}}
```

Save the file. When Copilot asks to sign in, allow it and sign in on engine.emodely.com.

For Copilot Business or Enterprise, an administrator must allow MCP servers in Copilot first.

#### MCP Inspector (developers)

Run:

```bash
npx @modelcontextprotocol/inspector
```

Choose the **Streamable HTTP** transport, enter `https://engine.emodely.com/mcp` and connect, then sign in on engine.emodely.com. If your Inspector shows a **Connection Type** option, **Direct** and **Via Proxy** both work.

## Sign-in and access

- Sign-in always takes place on engine.emodely.com. Your assistant never sees your password.
- Access: create an account when you first connect, with email and password or with Google, Microsoft or LinkedIn. New accounts receive a free trial, which starts with the first successful run; the sign-in page shows its length. If a trial is not available for your account, request access at [engine.emodely.com/request-access](https://engine.emodely.com/request-access).

## Troubleshooting

- **"Access denied" after sign-in.** The account exists but its access is not active yet, or it has ended. Contact support@emodely.com. If a trial is not available, request access at [engine.emodely.com/request-access](https://engine.emodely.com/request-access).
- **Work Microsoft accounts.** Your organisation may require IT admin approval before you can sign in with Microsoft. This is an organisation policy. Ask your IT admin, or sign in with email and password or another provider.
- **Desktop and terminal apps.** After **Allow**, the page asks you to return to your app: **Open your app**, or "Return to your AI app to finish". If the app was closed or stopped waiting, go back to the app and start sign-in again.
- **Mobile apps.** The sign-in page may warn "Only continue if you started this connection from an app on this device". Continue only if you started it.
- **Self-hosted tools (for example n8n or LibreChat).** eModely must add your tool's callback address first. Contact support@emodely.com.
- **Browser-based tools.** Tools that connect directly from a web page, other than MCP Inspector, need eModely to allow their web address first. Contact support@emodely.com.

## Getting started

Start a new chat with the connector switched on and say hello, or ask what eModely can do. The assistant shows a short welcome and offers three ways to start:

- **Quick:** up to six questions, each with a recommended answer.
- **Detailed:** step by step through each topic.
- **Just assume:** you give the city and the size, and confirm whether the plant is new or existing and the weather file. The assistant assumes the rest and lists every assumption.

You can also name your role: consultant or designer, developer, or operator. The assistant suggests a path.

In Quick and Detailed, the assistant first asks whether the plant is new or existing and whether it is air-cooled or water-cooled, unless your request already makes this clear. These answers decide which questions follow.

Tip: choose **Always allow** for eModely tools to avoid repeated approval prompts.

Example requests:

> Estimate hourly cooling loads for a 40,000 m² office and retail development in Dubai, then size a water-cooled chiller plant for it.

> We operate a plant in Riyadh with four 400 TR air-cooled chillers, about 12 years old. Simulate a typical year and show where the energy goes.

> For a new 2,000 TR district cooling plant in Abu Dhabi, compare a plant with chilled-water storage against one without, on energy, peak demand and lifecycle cost.

> Fit a chiller curve set from this manufacturer performance table and run my plant with it.

> Calculate pressure drop for a closed chilled-water circuit at 7 °C and 30 m³/h, with 80 m of supply pipe and 80 m of return pipe, both with a 100 mm internal diameter. Use carbon steel and a total fittings loss coefficient of 6 on each leg. Show segment losses, circuit total, velocity and warnings.

> Size a carbon steel chilled-water pipe for a 500 kW cooling load with a 6 K temperature difference, at a water temperature of 7 °C. Use maximum limits of 1.5 m/s and 200 Pa/m, and show the recommended size and candidate checks.

## How eModely works with your assistant

- **The connector carries its own guide.** Tool descriptions and working rules are served by engine.emodely.com and update with the engine, so every assistant follows the current guidance. The [AI guide](https://engine.emodely.com/ai) is a plain-text page you can share with any assistant to explain eModely before the connector is added.
- **EPW weather files only.** The assistant names the weather file it uses, normally before the first run, or in the results when you asked it to assume everything and the city match is clear. A nearby city is used only with your agreement.
- **Hourly data stays out of the chat.** Hourly results are delivered through an expiring download link that opens only after you sign in with your eModely account.
- **Your data is yours.** Your plants, runs, curve sets and uploads belong to you and can be shown to you in full. The eModely chiller library's curves are confidential.
- **Problem reports.** If a result looks wrong, ask the assistant to report it. It sends a private report to the eModely team only after you approve its contents.

## Data and privacy

eModely stores your account, the work you save, your uploads and the inputs and summaries of your runs. Your conversations stay with your AI provider; eModely receives only the requests the assistant sends to the engine. Details are in the [Terms of Use](https://engine.emodely.com/terms), the [Privacy Policy](https://emodely.com/privacy) and the [security page](https://engine.emodely.com/security).

Results are engineering estimates. Check the inputs and results; you remain responsible for design and investment decisions. Reverse engineering the engine, including systematic series of runs to map its behaviour, is not permitted.

## Support

- **Email:** support@emodely.com, for questions, access and anything confidential.
- **Feedback:** open an [issue](https://github.com/Ahlabeeb/emodely-mcp/issues/new/choose). Issues are public, so leave out client names, project details and download links.
- **Security:** see [SECURITY.md](SECURITY.md). Do not open a public issue.

## About this repository

This repository holds the public connector details, the optional Claude plugin (connector settings and skill text) and user documentation. It contains no engine code, chiller data or coefficients. The plugin files are provided under the terms in [LICENSE](LICENSE).
