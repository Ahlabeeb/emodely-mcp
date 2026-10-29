# eModely Engine beta: tester guide

Thank you for testing the eModely Engine. This guide adds the beta details to the [README](../README.md) and takes about 10 minutes.

## 1. Before you start

- **Access.** New accounts receive a free trial, which starts with the first successful run; the sign-in page shows its length. If a trial is not available for your account, request access at [engine.emodely.com/request-access](https://engine.emodely.com/request-access).
- **Sign-in.** Create an account when you first connect, with email and password or with Google, Microsoft or LinkedIn.
- **An assistant.** Claude (web, desktop and mobile), Claude Code, ChatGPT (added on chatgpt.com; then web, desktop and mobile, depending on the plan), VS Code (GitHub Copilot chat), Cursor, Codex CLI or MCP Inspector. See [Connect](../README.md#connect) in the README.

## 2. Connect and sign in

Paste this into your AI assistant and it will guide you:

> Help me connect the eModely connector: https://github.com/Ahlabeeb/emodely-mcp

Follow [Connect](../README.md#connect) for your assistant. When the browser window opens on engine.emodely.com, sign in and select **Allow**.

**"Access denied" after sign-in:** your account has no active access yet, or its access has ended. Contact support@emodely.com. See [Troubleshooting](../README.md#troubleshooting) for this and other sign-in problems.

## 3. What to try

1. Say hello and choose a way to start: Quick, Detailed or Just assume. In Quick and Detailed, answer whether the plant is new or existing and whether it is air-cooled or water-cooled.
2. Estimate cooling loads for a building or a small district, with the quick method and then the detailed method.
3. Size and simulate a plant for one of your own projects. Leave out client names.
4. Ask for chilled-water storage options for the same plant. The storage advisor runs in the background. The assistant starts it and checks back for the result, so it can take a little while.
5. Change one input, re-run, and ask the assistant to compare the two runs.
6. Ask for the hourly results as Excel, and open the download link.
7. Try a city that is not in the library, and upload your own EPW file through the link the assistant gives you.
8. Give the assistant a small chiller performance table, let it fit and save a curve set, and run a plant with it.
9. List your saved plants and runs, and delete a run or a plant you no longer need.

## 4. What to report

We want to hear about anything that is wrong, confusing or slow, for example:

- results that look wrong to an engineer;
- a confusing question, or too many questions;
- an input you needed that the assistant could not take;
- the assistant estimating numbers itself instead of running the engine;
- problems with connecting, sign-in, upload or download.

For each report, include the assistant and app you used, the date and time with your time zone, your prompt, what happened and what you expected, the weather file the assistant reported, and any error message word for word.

## 5. How to report

- **In the chat.** Ask the assistant to report the problem. It prepares a private report for the eModely team and sends it only after you approve it.
- **Public issue.** Open an [issue](https://github.com/Ahlabeeb/emodely-mcp/issues/new/choose) with the **Feedback** form. Issues are public, so leave out client names, project locations, drawings, download links and chat share links.
- **Private email.** Write to support@emodely.com for anything confidential, or if you have no GitHub account.

## 6. Terms

- Use of the engine is subject to the [eModely Engine Terms of Use](https://engine.emodely.com/terms) and the [eModely Privacy Policy](https://emodely.com/privacy).
- Results are engineering estimates. Check the inputs and results. You remain responsible for design and investment decisions.
- Do not try to reverse-engineer the engine, for example by running systematic series of simulations to map its behaviour, and do not extract or compile the chiller library.
- Fair-use limits apply to some actions; the assistant tells you when one is reached.
