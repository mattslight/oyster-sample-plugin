# Oyster Sample App — Pomodoro

The starter template for building [Oyster](https://oyster.to) apps. Click **Use this template** above to create your own app repo, or install this one as-is — it's a fully functional Pomodoro timer.

![Pomodoro](https://img.shields.io/badge/runtime-static-7c6bff) ![License](https://img.shields.io/badge/license-MIT-7c6bff)

## What this demonstrates

- The minimum viable Oyster app: `manifest.json` + an HTML entrypoint.
- The `runtime: "static"` app kind — a self-contained HTML file loaded as an artifact on the Oyster surface.
- Persisting user preferences via `localStorage` (scoped to the iframe, no Oyster API needed).

## Install

```bash
oyster install mattslight/oyster-sample-app
```

The Pomodoro artifact appears on your surface.

## Use as a template

1. Click **Use this template** → **Create a new repository**.
2. Edit `manifest.json`:
   - Change `id` to your app's ID (lowercase, no spaces — becomes the folder name).
   - Change `name`, `description`, `author`, `authorUrl`, `repo`.
   - Bump `version` on every release.
3. Replace `src/index.html` with your app.
4. Tag and release on GitHub: `git tag v0.1.0 && git push --tags`.

## Manifest fields

| Field | Required | Purpose |
|---|---|---|
| `id` | yes | Unique app ID. Never change after release. |
| `name` | yes | Human-readable display name. |
| `version` | yes | Semver. |
| `minOysterVersion` | yes | Minimum Oyster version this app needs. |
| `description` | yes | One-line summary. Shown in app browser. |
| `author` | yes | Your name or handle. |
| `authorUrl` | no | Link to your homepage / GitHub. |
| `repo` | yes | `owner/name` on GitHub. Used for updates. |
| `type` | yes | Artifact type (`app`, `notes`, `diagram`, etc.). |
| `runtime` | yes | `static` today. `bundle`, `mcp`, `panel` in future. |
| `entrypoint` | yes | Path to the HTML file (for `static`) or `main.js` (for `bundle`). |
| `ports` | yes | Declared ports the app needs (empty for `static`). |
| `storage` | yes | `none` or path for persistent server-side storage. |
| `capabilities` | yes | Opt-in capability list (empty for sandboxed static apps). |
| `status` | yes | `"ready"` when published. |
| `builtin` | yes | `false` for third-party apps. |
| `created_at`, `updated_at` | yes | ISO 8601 timestamps. |

## Developing

This template is pure static HTML — no build step. Open `src/index.html` directly in a browser to iterate, then drop the folder into `~/Oyster/apps/<your-id>/` to test inside Oyster.

For apps that need bundling (JavaScript libraries, TypeScript), wait for the `runtime: "bundle"` kind — it'll add an esbuild workflow similar to [Obsidian's sample plugin](https://github.com/obsidianmd/obsidian-sample-plugin).

## Getting listed in the Oyster community directory

Submit a PR to `mattslight/oyster-community-apps` adding one entry to `community-apps.json`:

```json
{
  "id": "your-app-id",
  "name": "Your App",
  "author": "Your Name",
  "description": "…",
  "repo": "your-username/your-app-repo"
}
```

Your app will appear at [oyster.to/apps](https://oyster.to/apps) and in the in-app browser.

## License

MIT — use this as a template freely.
