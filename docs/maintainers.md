# Maintaining this repository

- **Allowed contents.** Connector settings, plugin config, skill text and documentation only. `scripts/check-no-leaks.sh` runs in CI and fails on any other file, on internal hosts, and on anything that looks like a key or a coefficient table.
- **Validation.** Run `claude plugin validate .` and `claude plugin validate ./plugins/emodely-engine --strict`.
- **No downloads.** Users add the connector URL; there are no packages or release files to publish.
- **Plugin version.** The plugin version follows the eModely Engine version and changes only when the engine version changes, never when a feature is added.
