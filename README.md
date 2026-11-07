# cenk: Cenk Simsek's Claude Code plugins

The plugin catalog (marketplace) `cenk`. Every plugin here is named `cenk-<purpose>`, lives in its own repository and installs on its own.

| Plugin | What it does |
|---|---|
| [cenk-overtime](https://github.com/cenksimsek1988/cenk-overtime) | Helps employees who worked unpaid overtime or extra shifts prepare their claim for a lawyer: their out-of-hours work counted from their own records, and an evidence report for the lawyer to check. Not legal advice. |
| [cenk-jobs](https://github.com/cenksimsek1988/cenk-jobs) | Your job search with Claude: finds and screens postings under your own employer rules, writes CVs and letters from your own facts, applies on its own whenever your records answer every question, and tracks applications, interviews and prep on one private dashboard. |

Only public plugins are listed. A private plugin is shared from its own repository with invited people; see its README.

## Install

In the Claude desktop app (Code tab) or a `claude` terminal session:

```
/plugin marketplace add https://github.com/cenksimsek1988/claude-plugins.git
/plugin install cenk-overtime@cenk
/plugin install cenk-jobs@cenk
```

From a terminal, without a session:

```bash
claude plugin marketplace add https://github.com/cenksimsek1988/claude-plugins.git
```
```bash
claude plugin install cenk-overtime@cenk
```
```bash
claude plugin install cenk-jobs@cenk
```

- Write the addresses with `https://`: the short form `cenksimsek1988/claude-plugins` clones over SSH when a GitHub SSH key is found, and an install from `/plugin` in a session does not fall back to HTTPS.
- Then start a new session. Each plugin's README says how to begin.

## One copy of each plugin

- Install a plugin one way only: from `cenk`, or from its own repository (its catalog is named after the plugin, for example `cenk-overtime@cenk-overtime`).
- To switch, uninstall the other copy first, for example `claude plugin uninstall cenk-overtime@cenk-overtime`, then `claude plugin marketplace remove cenk-overtime`.

## Updates

- In a session: `/plugin marketplace update cenk`, then `/reload-plugins`. In a terminal: `claude plugin update cenk-overtime@cenk`.
- Or turn on auto-update: `/plugin`, tab Marketplaces, `cenk`, Enable auto-update.
- A new copy arrives only when the plugin's version changes.

## For developers: the local fallback

Each plugin's repository has its own one-plugin catalog, named after the plugin. Add the folder of a clone instead of this catalog:

```bash
claude plugin marketplace add <folder of the clone>
```
```bash
claude plugin install cenk-overtime@cenk-overtime
```

- Edits in the folder load at the next session, with no new version and no push.
- Use it too when an install from GitHub fails in the desktop app.
- Keep one copy: uninstall `<plugin>@cenk` first.

## Versions

- A plugin's version lives only in its own `.claude-plugin/plugin.json`. The entries here carry none: Claude Code reads `plugin.json` first, and a second version would only disagree with it.
- So a plugin release needs no change here. This catalog gets a new version only when an entry is added, removed or changed (`CHANGELOG.md`).

## License

MIT, see `LICENSE`. Each plugin has its own license in its repository.
