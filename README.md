# Federation Graph

A single-page editor for drawing federation graphs: nodes, notes, images and the wires between them. It runs entirely in the browser, saves projects automatically, and can optionally sync projects to this GitHub repository so a team can work on the same graph.

No build step, no dependencies, no server. It is one `index.html` plus a few small files.

**Live site:** `https://<your-username>.github.io/<repo-name>/`

## What it does

- **Nodes** with types, colours, groups, a badge, and per-node appearance (background and text colour, alignment, bold / italic / underline).
- **Notes** (floating text) and **images** (drop, paste or add; crop, resize, rotate, give them a name).
- **Wires** that are curved or straight, with labels, custom colours, pins to reshape them, and an in / out port on every side of a node.
- **Selection tools** for nodes, notes, images, wires and groups, plus a *Filter selection* button for dropping items from a selection.
- **Bulk create** (one node per line), **find & replace** across node names, properties and notes, undo / redo.
- **PNG export** with four layouts (whole graph, selection only, selection highlighted in its group, selection highlighted in the whole graph), an optional legend and a transparent background.
- **Projects** stored in your browser, with JSON import / export.
- **GitHub sync**, per project (see below).

Press **?** in the app for the full list of shortcuts.

## Publish it on GitHub Pages

1. Create a repository and upload everything in this folder to its root (`index.html` must be at the top level).
2. Go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, pick `main` and `/ (root)`, and save.
4. After a minute the site is live at `https://<your-username>.github.io/<repo-name>/`.

To try it on your own computer, just open `index.html` in a browser. (Sync and offline install need the `https` site.)

## Sync projects with GitHub

Sync is optional and works per project, so you can keep some projects local and others shared.

**One-time setup, for each person**

1. Create a fine-grained token at <https://github.com/settings/personal-access-tokens>.
   Give it access to **only this repository** and the permission **Contents: Read and write**.
2. In the app open **Projects → GitHub…**. The owner and repository are filled in from the site address.
3. Paste the token and press **Save & test**.

Everyone who collaborates needs write access to the repository and their own token. The token is kept in your browser only and is never written to the repository.

**Using it**

- Turn on the **GitHub** switch at the end of a project's row. Off keeps the project local only.
- A synced project is saved as `federation-graph/<id>.json`, and its images under `federation-graph/img/`. Every save is a commit.
- Changes save a few seconds after you stop editing. The app checks for other people's changes about every 25 seconds and loads them quietly when you have nothing unsaved.
- **Sync now** and **Reload latest** are on each synced row. **Load from GitHub** adds projects that exist in the repository but not in your list yet.
- If you both changed the same project, you choose: **Load theirs**, **Keep mine**, or **Save mine as a copy**.

**Good to know**

- GitHub Pages on a free account needs a public repository, so synced projects can be read by anyone. Don't sync anything private.
- If Pages publishes from `main`, each save rebuilds the site. To avoid that, create a separate branch (for example `data`) and enter it in the **Branch** field when connecting.
- Updates arrive within about half a minute. There is no live cursor or instant co-editing.
- Deleting a synced project only removes your local copy. The file on GitHub stays, and **Load from GitHub** brings it back.

## Your data

Projects live in your browser's local storage, per browser and per site address. Clearing site data removes them, so use **Projects → Export** for a backup, or turn on GitHub sync. Nothing is sent anywhere unless you switch sync on, and then it goes only to the repository you chose.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole app |
| `manifest.webmanifest`, `icon.svg`, `icon-192.png`, `icon-512.png`, `icon-maskable-512.png` | Lets the site be installed like an app |
| `sw.js` | Offline support (network first, cache as a fallback) |
| `LICENSE` | MIT licence |

## Browser support

Current versions of Chrome, Edge, Firefox and Safari.

## Licence

MIT. See [LICENSE](LICENSE). Made by Ezrael Vitto.
