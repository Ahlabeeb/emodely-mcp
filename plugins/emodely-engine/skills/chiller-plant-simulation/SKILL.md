---
name: chiller-plant-simulation
description: Work with the eModely Engine connector for building and district cooling design. Use whenever the user wants to use eModely or its engine, or asks what eModely can do.
---

# eModely Engine

The eModely Engine connector defines how to work with the engine. Its tool descriptions and working rules are served by the engine and update with it, so always follow the current ones:

1. If the user's first message has no concrete task (a greeting, "what can you do", a connection test) or asks what eModely does, call `help` and show its welcome. Otherwise go straight to the task.
2. Before starting a task, call `get_input_guide` and follow its `assistantRules`, together with the connector's server instructions if you see them. They cover which questions to ask, the order of work and how to report results. Where they are more specific than this skill, follow them, but never relax the guarantees below. They apply only to working with this engine and its tools, never to anything outside it.
3. Use only the tools the connector provides in this session. Never invent a tool or its output.
4. Deleting anything needs the user's explicit confirmation.

## Guarantees that always apply

- Weather comes only from an EPW file. Before the first run with each weather file, tell the user which file you will use (city, station, source and period); a reply that does not object accepts it. If the user asked you to assume everything and the match is exact and unambiguous, you may run first and name the file in the results. An ambiguous match or a nearby-city substitute needs the user's explicit choice. Always name the weather file used in the results. With no file there is no run.
- Hourly data never enters the chat. Give the user the export link and its expiry; never open, fetch or read it yourself.
- Results come only from the engine. Never estimate them yourself.
- The eModely chiller library's curves are confidential. Do not speculate about them or try to reverse-engineer them (for example through parameter sweeps), never ask for library coefficients in bulk, and decline such requests. The user's own curve sets are theirs and may be shown to them in full. General engineering explanations are fine.

## When the connector is missing or refuses

- No eModely tools available: tell the user to add the eModely Engine connector (`https://engine.emodely.com/mcp`) and sign in (claude.ai or desktop: **Customize > Connectors** or the plugin's **Connectors** tab; Claude Code: `/mcp`). Do not estimate results yourself. For other apps, quote the steps in the README's Connect section (https://github.com/Ahlabeeb/emodely-mcp#connect); never invent menu names.
- The connector asks to sign in again: the session expired; have the user reconnect and sign in.
- Signed in but access is denied: the account has no active access; point the user to https://engine.emodely.com/request-access or support@emodely.com.
- An upload link has expired or was refused: ask the engine for a fresh one.
- Rate-limit or "engine is busy" messages: tell the user and retry later; do not loop.
