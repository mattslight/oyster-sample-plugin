# Oyster Sample Plugin — Pomodoro

The starter template for building [Oyster](https://oyster.to) plugins. Click **Use this template** above to create your own plugin repo, or install this one as-is — it's a fully functional Pomodoro timer.

![Pomodoro](https://img.shields.io/badge/runtime-static-7c6bff) ![License](https://img.shields.io/badge/license-MIT-7c6bff)

## What this demonstrates

- The minimum viable Oyster plugin: `manifest.json` + an HTML entrypoint.
- The `runtime: "static"` plugin kind — a self-contained HTML file loaded as an artifact on the Oyster surface.
- Persisting user preferences via `localStorage` (scoped to the iframe, no Oyster API needed).

## Install (manual — Tier 1)

```bash
git clone https://github.com/mattslight/oyster-sample-plugin ~/.oyster/userland/pomodoro
```

Restart Oyster. The artifact appears on your surface.

Future tiers (`oyster install mattslight/oyster-sample-plugin`, in-app browser) will land once the CLI and community registry ship — see [Oyster's plugin system design](https://github.com/mattslight/oyster-os/blob/main/docs/plans/plugin-system.md).

## Use as a template

1. Click **Use this template** → **Create a new repository**.
2. Edit `manifest.json`:
   - Change `id` to your plugin's ID (lowercase, no spaces — becomes the folder name).
   - Change `name`, `description`, `author`, `authorUrl`, `repo`.
   - Bump `version` on every release.
3. Replace `src/index.html` with your plugin.
4. Tag and release on GitHub: `git tag v0.1.0 && git push --tags`.

## Manifest fields

| Field | Required | Purpose |
|---|---|---|
| `id` | yes | Unique plugin ID. Never change after release. |
| `name` | yes | Human-readable display name. |
| `version` | yes | Semver. |
| `minOysterVersion` | yes | Minimum Oyster version this plugin needs. |
| `description` | yes | One-line summary. Shown in plugin browser. |
| `author` | yes | Your name or handle. |
| `authorUrl` | no | Link to your homepage / GitHub. |
| `repo` | yes | `owner/name` on GitHub. Used for updates. |
| `type` | yes | Artifact type (`app`, `notes`, `diagram`, etc.). |
| `runtime` | yes | `static` today. `bundle`, `mcp`, `panel` in future. |
| `entrypoint` | yes | Path to the HTML file (for `static`) or `main.js` (for `bundle`). |
| `ports` | yes | Declared ports the plugin needs (empty for `static`). |
| `storage` | yes | `none` or path for persistent server-side storage. |
| `capabilities` | yes | Opt-in capability list (empty for sandboxed static plugins). |
| `status` | yes | `"ready"` when published. |
| `builtin` | yes | `false` for third-party plugins. |
| `created_at`, `updated_at` | yes | ISO 8601 timestamps. |

## Developing

This template is pure static HTML — no build step. Open `src/index.html` directly in a browser to iterate, then drop the folder into `~/.oyster/userland/<your-id>/` to test inside Oyster.

For plugins that need bundling (JavaScript libraries, TypeScript), wait for the `runtime: "bundle"` kind — it'll add an esbuild workflow similar to [Obsidian's sample plugin](https://github.com/obsidianmd/obsidian-sample-plugin).

## Getting listed in the Oyster community directory

When the registry ships, submit a PR to `mattslight/oyster-community-plugins` adding one entry to `community-plugins.json`:

```json
{
  "id": "your-plugin-id",
  "name": "Your Plugin",
  "author": "Your Name",
  "description": "…",
  "repo": "your-username/your-plugin-repo"
}
```

Your plugin will appear at [oyster.to/plugins](https://oyster.to) and in the in-app browser.

## License

MIT — use this as a template freely.
