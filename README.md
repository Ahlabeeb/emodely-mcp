# eModely Engine

**Cooling design and simulation for buildings and district cooling plants, from your AI assistant.**

eModely connects your AI assistant to the eModely Engine through the Model Context Protocol (MCP). You describe a building or a plant in plain language. The assistant collects the inputs, runs the calculation on eModely's servers with real weather data, and explains the results.

Results come from the eModely Engine, not from an AI estimate. If the engine is not connected, the assistant does not produce numbers of its own.

**Connector URL:** `https://engine.emodely.com/mcp`

[Website](https://emodely.com) · [AI guide](https://engine.emodely.com/ai) · [Security](https://engine.emodely.com/security) · [Terms of Use](https://engine.emodely.com/terms) · [Privacy](https://emodely.com/privacy) · [Service status](https://status.emodely.com)

## What you can do

- **Building cooling loads.** A quick method (RTS) gives full-year hourly loads for a single building or a whole district in seconds, for concept design and masterplans. A detailed method (EnergyPlus heat balance) supports design validation and sensitivity studies. Occupancy, lighting and equipment schedules can be adjusted, including seasonal periods and your own hourly schedules for a full year.
- **Chiller and district cooling plant design.** Size and simulate a full year of operation for chillers, chilled-water and condenser-water pumps, cooling towers and thermal storage. Results include annual and monthly energy, kW/TR on delivered cooling, peak demand and where the energy goes.
- **Thermal energy storage.** Size chilled-water storage together with the chillers, for example to reduce installed chiller capacity or peak demand.
- **Chiller performance curves.** Fit a curve set from manufacturer data, check coefficients you already have, adjust ratings and compare chillers. Generic library chillers are available for plant selection.
- **Scenario comparison.** Compare plant options side by side on energy, cost and lifecycle financials.
- **Real weather.** Every run uses a real EPW weather file, from the eModely library or uploaded by you. The engine never generates weather.
- **Your work, saved.** Plants, load profiles, curve sets and runs are stored in your account, so you can list them and return to them later. Plants, load profiles and curve sets you no longer need can be deleted; past runs stay readable. Hourly results are delivered as a CSV or Excel download link.

## Who it is for

- **HVAC designers and consultants** who need building loads, plant sizing and annual energy early in a project.
- **Energy modellers** who want fast, repeatable annual simulations and scenario comparisons.
- **Plant operators and owners** who want to see where an existing plant's energy goes and test operating changes such as set points, staging and tariffs.
- **Developers** evaluating plant options, storage and lifecycle cost for a masterplan.

## Connect

You add the connector URL once and sign in with your eModely account. There is nothing to download or install.

**Assistants and apps:**

- **Claude:** claude.ai, the desktop app and the mobile apps. Add the connector on claude.ai or in the desktop app; it then appears in the mobile apps.
- **ChatGPT:** add the connector once on chatgpt.com (web) as a custom MCP server. It is then available in ChatGPT on the web, desktop and mobile apps. Availability depends on the ChatGPT plan.

### Claude (web and desktop app)

1. Open **Customize > Connectors**, select **Add**, then **Add custom connector**.
2. Enter the name `eModely Engine` and the URL `https://engine.emodely.com/mcp`, then select **Add**.
3. Sign in on engine.emodely.com when the window opens, and select **Allow**.
4. In a new chat, open **+ > Connectors** and check that **eModely Engine** is switched on.

Custom connectors are available on all Claude plans; the Free plan allows one. On Team and Enterprise plans, an Owner first adds the connector under **Organization settings > Connectors**, and each member then connects with their own eModely account.

**Claude Code:** run `claude mcp add --transport http emodely-engine https://engine.emodely.com/mcp` in a terminal, then run `/mcp`, select `emodely-engine` and choose **Authenticate**.

### Claude plugin (optional)

The connector is all you need. As an optional alternative for Claude, this repository is also a plugin marketplace: the plugin adds the same connector together with a short skill that helps Claude start eModely tasks. Plugins on claude.ai and in the desktop app require a paid Claude plan.

- **claude.ai and the desktop app.** Open **Customize > Plugins**, select **Add**, then **Add marketplace** and **Add from a repository**. Enter `Ahlabeeb/emodely-mcp`, keep **Sync automatically** on, and select **Sync**. Select **Add** next to **eModely Engine**, then connect it from the plugin's **Connectors** tab and sign in.
- **Claude Code.** Run the following, then run `/mcp`, select the eModely server and choose **Authenticate**:

  ```text
  /plugin marketplace add Ahlabeeb/emodely-mcp
  /plugin install emodely-engine@emodely
  ```

If you already added the connector, the plugin uses it, so there is nothing to remove. Engine updates never require a plugin update.

### ChatGPT

Add the connector once on chatgpt.com. It is then available in ChatGPT on the web, desktop and mobile apps. Availability and write access depend on the ChatGPT plan. See OpenAI's article [Connecting custom MCP servers in ChatGPT](https://help.openai.com/en/articles/12584461) for the current requirements.

1. On chatgpt.com, open **Plugins**, select the plus button, then **Add custom MCP server**.
2. Enter the name `eModely Engine` and, under **Connection**, the URL `https://engine.emodely.com/mcp`.
3. Choose OAuth authentication, review the risk warning and confirm, then select **Create as a plugin**.
4. Sign in on engine.emodely.com when asked, and select **Allow**.
5. In a new chat, type `@` and select **eModely Engine**.

The ChatGPT desktop app's Codex **Plugins > MCPs** list is a separate setup on each computer.

## Sign-in and access

- Sign-in always takes place on engine.emodely.com. Your assistant never sees your password.
- Access: create an account when you first connect, with email and password or with Google, Microsoft or LinkedIn. New accounts receive a 30-day free trial, which starts with the first successful run. If a trial is not available for your account, request access at [engine.emodely.com/request-access](https://engine.emodely.com/request-access).
- If you sign in and see "Access denied", your account exists but its access is not active yet, or it has ended. Contact support@emodely.com.

## Getting started

Start a new chat with the connector switched on and say hello, or ask what eModely can do. The assistant shows a short welcome and offers three ways to start:

- **Quick:** up to six questions, each with a recommended answer.
- **Detailed:** step by step through each topic.
- **Just assume:** you give only the city and the size; the assistant assumes the rest and lists every assumption.

Example requests:

> Estimate hourly cooling loads for a 40,000 m² office and retail development in Dubai, then size a water-cooled chiller plant for it.

> We operate a plant in Riyadh with four 400 TR air-cooled chillers, about 12 years old. Simulate a typical year and show where the energy goes.

> For a new 2,000 TR district cooling plant in Abu Dhabi, compare a plant with chilled-water storage against one without, on energy, peak demand and lifecycle cost.

> Fit a chiller curve set from this manufacturer performance table and run my plant with it.

## How eModely works with your assistant

- **The connector carries its own guide.** Tool descriptions and working rules are served by engine.emodely.com and update with the engine, so every assistant follows the current guidance. The [AI guide](https://engine.emodely.com/ai) is a plain-text page you can share with any assistant to explain eModely before the connector is added.
- **Real weather only.** The assistant names the weather file it uses, normally before the first run, or in the results when you asked it to assume everything and the city match is clear. A nearby city is used only with your agreement.
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
