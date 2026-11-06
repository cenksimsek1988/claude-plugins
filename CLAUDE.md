# claude-plugins

The public plugin catalog `cenk`: `.claude-plugin/marketplace.json`, which lists Cenk Simsek's public plugins. No plugin code lives here: each plugin is in its own repository.

## Rules (Cenk, 6 Nov 2026)

- Only public plugins are listed. A private plugin stays in its own private repository, shared with invited people through that repository's own one-plugin catalog (example: `cenk-workbench@cenk-workbench`).
- On a personal GitHub account an invited collaborator can also push ("repository owners can only grant write access to collaborators", GitHub docs). Read-only needs a GitHub organization.
- Each plugin's repository keeps its own catalog, named after the plugin, for local work and invited people. Example: `claude plugin marketplace add <folder of the cenk-overtime clone>`, then `cenk-overtime@cenk-overtime`.
- Never two copies of one plugin installed: uninstall `<plugin>@<plugin>` before installing `<plugin>@cenk`, and the other way round.

## Entries

- Plugin in a subfolder of its repository: `git-subdir`. Example: `{"source": "git-subdir", "url": "https://github.com/cenksimsek1988/cenk-overtime.git", "path": "cenk-overtime"}`.
- Plugin at the top of its repository: `url`. Example: `{"source": "url", "url": "https://github.com/<owner>/<repo>.git"}`.
- Full `https://` URLs, not `owner/repo`: the short form clones over SSH when a key is found, and `/plugin` in a session does not fall back to HTTPS (Claude Code docs, plugins/host-marketplace).
- No `version` in an entry: `plugin.json` wins, and `claude plugin validate` warns when both are set.
- Give each entry `description`, `author`, `homepage`, `license`, `category` and `keywords`: before install, users see only the entry's own fields for a remote source.
- To remove or rename an entry, add it to a top-level `renames` map (old name to new name, or to `null`). Keep old entries.

## Waiting

- cenk-jobs: add on the day `cenksimsek1988/claude-job-search` is public (its public release, Job search coordinator). Entry source: `{"source": "git-subdir", "url": "https://github.com/cenksimsek1988/claude-job-search.git", "path": "plugins/cenk-jobs"}`; copy description, keywords and category from its `plugins/cenk-jobs/.claude-plugin/plugin.json` and its catalog entry. Tested from a throwaway config on 6 Nov 2026 with Cenk's git login.

## Every change

- An entry in `CHANGELOG.md` and a higher `version` in `.claude-plugin/marketplace.json`.
- Commit only when Cenk asks, with `/cenk-workbench:commit`. Local git identity: Cenk Simsek <35446555+cenksimsek1988@users.noreply.github.com>.

## Checks

- `claude plugin validate .`
- Install test that leaves Cenk's own setup alone: a throwaway config folder. Example (Git Bash): `CLAUDE_CONFIG_DIR=$(mktemp -d) sh -c 'claude plugin marketplace add . && claude plugin install cenk-overtime@cenk && claude plugin list'`.
- Desktop app test: new session, type `/cenk-overtime:` and see the skills.
