# Maintaining this repository

- **Allowed contents.** Connector settings, plugin config, skill text and documentation only. `scripts/check-no-leaks.sh` runs in CI and fails on any other file, on internal hosts, and on anything that looks like a key or a coefficient table.
- **Validation.** Run `claude plugin validate .` and `claude plugin validate ./plugins/emodely-engine --strict`.
- **No downloads.** Users add the connector URL; there are no packages or release files to publish. Engine updates need no change here.
- **Plugin version.** The optional Claude plugin's version is independent of the engine. Raise `version` in `plugins/emodely-engine/.claude-plugin/plugin.json` only when the plugin's own files change, because Claude Code users stay on the installed version until it changes.
