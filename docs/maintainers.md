# Maintaining this repository

- **Allowed contents.** Connector settings, plugin config, skill text and documentation only. `scripts/check-no-leaks.sh` runs in CI and fails on any other file, on internal hosts, and on anything that looks like a key or a coefficient table.
- **Validation.** Run `claude plugin validate .` and `claude plugin validate ./plugins/emodely-engine --strict`.
- **Plugin releases.** The plugin version is independent of the engine. Engine updates need no plugin release. Release only when the plugin's own files change:
  1. Raise `version` in `plugins/emodely-engine/.claude-plugin/plugin.json`. Claude Code users stay on the installed version until it changes.
  2. Run `bash scripts/package-plugin.sh`. It builds `dist/emodely-engine-<version>.zip` from the committed plugin folder.
  3. Attach the zip to a GitHub release tagged `v<version>`, with a short user-facing note.
